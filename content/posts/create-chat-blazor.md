---
title: HangFire WebFarm
date: 2023-07-14T15:54:51-03:00
draft: false
description: Uma Hangfire WebFarm é um cenário em que várias instâncias da aplicação, que utilizam o Hangfire para processar tarefas em segundo plano, estão distribuídas em diferentes servidores (ou nós) que compartilham o mesmo banco de dados ou storage. Esse conceito é usado para fins de escalabilidade e alta disponibilidade, permitindo que várias instâncias da aplicação compartilhem a carga de processamento das tarefas em segundo plano e evitem pontos únicos de falha.

--

Uma Hangfire WebFarm é um cenário em que várias instâncias da aplicação, que utilizam o Hangfire para processar tarefas em segundo plano, estão distribuídas em diferentes servidores (ou nós) que compartilham o mesmo banco de dados ou storage. Esse conceito é usado para fins de escalabilidade e alta disponibilidade, permitindo que várias instâncias da aplicação compartilhem a carga de processamento das tarefas em segundo plano e evitem pontos únicos de falha.

A configuração de uma WebFarm com o Hangfire geralmente envolve os seguintes passos:

1. Configuração do Storage Compartilhado:
Todas as instâncias da aplicação que compõem a WebFarm devem apontar para o mesmo banco de dados ou storage, permitindo que compartilhem as informações das tarefas em segundo plano. Por exemplo, se você estiver usando o SQL Server como storage, todas as instâncias devem usar a mesma string de conexão para o banco de dados SQL Server.
2. Configuração de Filas Compartilhadas:
Para evitar que as tarefas sejam processadas várias vezes por diferentes instâncias da aplicação, você pode configurar diferentes filas para cada instância do Hangfire. Isso permite que as tarefas sejam distribuídas uniformemente entre as instâncias.
3. Configuração dos Servidores:
Em cada instância da aplicação, você precisa configurar o servidor do Hangfire para processar as tarefas em segundo plano. Cada instância da aplicação pode executar o servidor do Hangfire usando configurações específicas, como o número máximo de trabalhadores (workers) ou a quantidade de tarefas por lote (batch).
4. Balanceamento de Carga:
O balanceamento de carga entre as instâncias da aplicação pode ser realizado através de ferramentas de balanceamento de carga, como o Nginx ou o Azure Load Balancer, dependendo do ambiente em que sua WebFarm está hospedada. Essas ferramentas distribuem as solicitações de clientes entre as várias instâncias de forma equilibrada, garantindo que a carga seja dividida.

Lembre-se de que, ao configurar uma WebFarm, é essencial garantir que as tarefas em segundo plano sejam projetadas para serem seguras e resilientes em relação a várias instâncias. Algumas tarefas podem exigir mecanismos adicionais, como bloqueios distribuídos, para evitar que várias instâncias executem a mesma tarefa simultaneamente.

Além disso, é importante monitorar a carga e o desempenho das instâncias da WebFarm para ajustar a quantidade de recursos alocados a cada uma delas e garantir uma operação eficiente e confiável do sistema como um todo.

Vamos criar um exemplo simples de Hangfire WebFarm usando o SQL Server como storage e duas instâncias da aplicação para processar tarefas em segundo plano. Neste exemplo, as duas instâncias estarão hospedadas localmente para fins de demonstração.

Passo 1: Criação do projeto
Crie duas aplicações [ASP.NET](http://asp.net/) (Web Applications) usando o Visual Studio ou a ferramenta de linha de comando dotnet:

```bash
dotnet new web -n HangfireWebFarmApp1
dotnet new web -n HangfireWebFarmApp2

```

Passo 2: Instalação dos pacotes NuGet
Em cada aplicação, instale o pacote NuGet do Hangfire e o pacote do storage SQL Server:

```bash
cd HangfireWebFarmApp1
dotnet add package Hangfire
dotnet add package Hangfire.SqlServer

cd ../HangfireWebFarmApp2
dotnet add package Hangfire
dotnet add package Hangfire.SqlServer

```

Passo 3: Configuração do Hangfire
Vamos configurar cada aplicação para usar o SQL Server como storage e configurar filas diferentes para cada instância:

Em `Startup.cs` de HangfireWebFarmApp1:

```csharp
using Microsoft.Owin;
using Owin;
using Hangfire;
using Hangfire.SqlServer;

[assembly: OwinStartup(typeof(HangfireWebFarmApp1.Startup))]

namespace HangfireWebFarmApp1
{
    public class Startup
    {
        public void Configuration(IAppBuilder app)
        {
            GlobalConfiguration.Configuration.UseSqlServerStorage("your_connection_string_here", new SqlServerStorageOptions
            {
                QueuePollInterval = TimeSpan.FromSeconds(15),
                QueueNames = new[] { "app1" }
            });

            app.UseHangfireDashboard();
            app.UseHangfireServer(new BackgroundJobServerOptions
            {
                Queues = new[] { "app1" }
            });

            // Exemplo de tarefa em segundo plano
            RecurringJob.AddOrUpdate(() => Console.WriteLine("Tarefa em segundo plano da App1 executada!"), Cron.Minutely);
        }
    }
}

```

Em `Startup.cs` de HangfireWebFarmApp2:

```csharp
using Microsoft.Owin;
using Owin;
using Hangfire;
using Hangfire.SqlServer;

[assembly: OwinStartup(typeof(HangfireWebFarmApp2.Startup))]

namespace HangfireWebFarmApp2
{
    public class Startup
    {
        public void Configuration(IAppBuilder app)
        {
            GlobalConfiguration.Configuration.UseSqlServerStorage("your_connection_string_here", new SqlServerStorageOptions
            {
                QueuePollInterval = TimeSpan.FromSeconds(15),
                QueueNames = new[] { "app2" }
            });

            app.UseHangfireDashboard();
            app.UseHangfireServer(new BackgroundJobServerOptions
            {
                Queues = new[] { "app2" }
            });

            // Exemplo de tarefa em segundo plano
            RecurringJob.AddOrUpdate(() => Console.WriteLine("Tarefa em segundo plano da App2 executada!"), Cron.Minutely);
        }
    }
}

```

Certifique-se de substituir `"your_connection_string_here"` pela string de conexão correta do seu banco de dados SQL Server.

Passo 4: Execução das aplicações
Execute as duas aplicações em instâncias separadas. Uma vez que ambas estejam em execução, você terá uma WebFarm simples com duas instâncias do Hangfire processando tarefas em segundo plano em filas diferentes (`app1` e `app2`) compartilhando o mesmo banco de dados.
