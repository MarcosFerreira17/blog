---
title: S.O.L.I.D. Principles
date: 2023-09-09T20:35:25-03:00
draft: false
description: Os princípios SOLID são um conjunto de cinco princípios de design de software que foram formulados para criar sistemas de software mais flexíveis, compreensíveis e fáceis de manter. Cada letra em "SOLID" representa um princípio específico.
---

Os princípios SOLID são um conjunto de cinco princípios de design de software que foram formulados para criar sistemas de software mais flexíveis, compreensíveis e fáceis de manter. Cada letra em "SOLID" representa um princípio específico. Vou explicar cada princípio em detalhes, usando exemplos em C#:

**1. Princípio da Responsabilidade Única (SRP - Single Responsibility Principle):**
Este princípio afirma que uma classe deve ter apenas uma razão para mudar, ou seja, ela deve ter uma única responsabilidade.

Exemplo em C#:

```csharp
// Versão não aderente ao SRP
class Pedido {
    public void CriarPedido() {
        // Lógica para criar um pedido
    }

    public void GerarRelatorio() {
        // Lógica para gerar um relatório
    }
}

// Versão aderente ao SRP
class Pedido {
    public void CriarPedido() {
        // Lógica para criar um pedido
    }
}

class Relatorio {
    public void GerarRelatorio() {
        // Lógica para gerar um relatório
    }
}
```

No exemplo não aderente ao SRP, a classe "Pedido" está sobrecarregada com duas responsabilidades distintas (criar pedidos e gerar relatórios). Na versão aderente ao SRP, as responsabilidades foram separadas em classes diferentes.

**2. Princípio do Aberto/Fechado (OCP - Open/Closed Principle):**
O OCP afirma que uma classe deve ser aberta para extensão, mas fechada para modificação. Isso significa que você pode adicionar novos comportamentos à classe sem alterar seu código fonte existente.

Exemplo em C#:

```csharp
// Versão não aderente ao OCP
class Calculadora {
    public double Calcular(double a, double b, string operador) {
        switch (operador) {
            case "+":
                return a + b;
            case "-":
                return a - b;
            // Mais operadores aqui
            default:
                throw new ArgumentException("Operador inválido");
        }
    }
}

// Versão aderente ao OCP
interface IOperacao {
    double Calcular(double a, double b);
}

class Soma : IOperacao {
    public double Calcular(double a, double b) {
        return a + b;
    }
}

class Subtracao : IOperacao {
    public double Calcular(double a, double b) {
        return a - b;
    }
}

// Cliente
class Calculadora {
    public double Calcular(IOperacao operacao, double a, double b) {
        return operacao.Calcular(a, b);
    }
}
```

Na versão não aderente ao OCP, a classe "Calculadora" precisa ser modificada sempre que um novo operador é adicionado. Na versão aderente ao OCP, introduzimos uma hierarquia de classes (interface e classes concretas) que permite adicionar novos operadores sem modificar a classe "Calculadora".

**3. Princípio de Substituição de Liskov (LSP - Liskov Substitution Principle):**
O LSP estabelece que objetos de subtipos devem ser substituíveis por objetos de tipos base sem afetar a integridade do programa.

Exemplo em C#:

```csharp
class Ave {
    public virtual void Voar() {
        Console.WriteLine("Voando...");
    }
}

class Pinguim : Ave {
    public override void Voar() {
        throw new InvalidOperationException("Os pinguins não podem voar.");
    }
}

class Cliente {
    public void TreinarAve(Ave ave) {
        ave.Voar();
    }
}
```

O exemplo ilustra que a classe derivada "Pinguim" substitui o método "Voar" da classe base "Ave", mas mantém o contrato da base. O cliente pode treinar qualquer ave para voar, mas os pinguins não podem voar, conforme esperado.

**4. Princípio da Segregação de Interfaces (ISP - Interface Segregation Principle):**
O ISP afirma que as interfaces devem ser específicas para os clientes que as utilizam, evitando interfaces grandes e genéricas.

Exemplo em C#:

```csharp
// Não aderente ao ISP
interface ITrabalhador {
    void Trabalhar();
    void Comer();
}

class Engenheiro : ITrabalhador {
    public void Trabalhar() {
        // Lógica de trabalho do engenheiro
    }

    public void Comer() {
        // Lógica de alimentação do engenheiro
    }
}

// Aderente ao ISP
interface ITrabalhador {
    void Trabalhar();
}

interface IComedor {
    void Comer();
}

class Engenheiro : ITrabalhador, IComedor {
    public void Trabalhar() {
        // Lógica de trabalho do engenheiro
    }

    public void Comer() {
        // Lógica de alimentação do engenheiro
    }
}
```

A versão não aderente ao ISP obriga a classe "Engenheiro" a implementar um método ("Comer") que não é relevante para todos os trabalhadores. A versão aderente ao ISP separa as interfaces em partes específicas, permitindo que as classes implementem apenas as interfaces relevantes para elas.

**5. Princípio da Inversão de Dependência (DIP - Dependency Inversion Principle):**
O DIP sugere que as classes de alto nível não devem depender de classes de baixo nível. Ambas devem depender de abstrações

. Além disso, abstrações não devem depender de detalhes, mas sim detalhes devem depender de abstrações.

Exemplo em C#:

```csharp
// Não aderente ao DIP
class LightBulb {
    public void TurnOn() {
        // Lógica para ligar a lâmpada
    }
}

class Switch {
    private LightBulb bulb;

    public Switch() {
        bulb = new LightBulb();
    }

    public void Operate() {
        bulb.TurnOn();
    }
}

// Aderente ao DIP
interface ISwitchable {
    void TurnOn();
}

class LightBulb : ISwitchable {
    public void TurnOn() {
        // Lógica para ligar a lâmpada
    }
}

class Switch {
    private ISwitchable device;

    public Switch(ISwitchable device) {
        this.device = device;
    }

    public void Operate() {
        device.TurnOn();
    }
}
```

Na versão não aderente ao DIP, a classe "Switch" depende diretamente da classe concreta "LightBulb". Na versão aderente ao DIP, a dependência é invertida, e a classe "Switch" depende de uma abstração ("ISwitchable"). Isso permite que diferentes dispositivos (por exemplo, lâmpadas, ventiladores) sejam controlados pelo mesmo interruptor, seguindo o princípio da inversão de dependência.

Lembrando que os princípios SOLID são diretrizes poderosas para criar código flexível, extensível e de fácil manutenção. Ao aplicá-los corretamente, você pode criar sistemas mais robustos e adaptáveis em C# ou em qualquer outra linguagem de programação.
