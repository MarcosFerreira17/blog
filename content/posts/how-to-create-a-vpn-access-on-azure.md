---
title: How to create a vpn access on Azure
date: 2023-04-04T08:07:11-03:00
draft: true
description:
---

# Arquitetura proposta :

![Arquitetura do projeto proposto](/static/images/azure-posts/arquitetura.png)

## Criando o ambiente:

### vnet-onpres
Começamos abrindo o portal do Azure, na label de 'virtual network' e iniciamos a criação de uma nova rede virtual, com o nome 'vnet-onpres':

![Criando a rede virtual](/static/images/azure-posts/criando-vnet.png)
### Basic Steps:
- Subscription: Escolha a subscription que deseja criar a rede virtual.
- Escolha um Resource Group: Escolha um resource group que deseja criar a rede virtual.
- Escolha o nome da virtual network.
- Escolha a região da rede virtual.
- Clique em Next.

## Configurando Segurança:
![Configurando Segurança](/static/images/azure-posts/configurando-seguranca.png)
Na label de security, temos as opções de [Azure Bastion](https://learn.microsoft.com/en-us/azure/bastion/bastion-overview), [Azure Firewall](https://learn.microsoft.com/en-us/azure/firewall/) e [DDos Network Protection](https://learn.microsoft.com/en-us/azure/ddos-protection/ddos-protection-overview) que são serviços que podem ser utilizados para melhorar a segurança da rede virtual. Neste caso, não iremos utilizar nenhum desses serviços, então, podemos clicar em 'Next'.

## Configurando Subnets:
![Configurando Subnets](/static/images/azure-posts/configurando-subnets.png)
Na label de subnets, podemos configurar as subnets que serão utilizadas na rede virtual. Neste caso, iremos criar uma subnet chamada 'GatewaySubnet' com o endereço de rede '192.168.0.0/27'. Clique em 'Add subnet' e preencha os campos com os valores abaixo:
![Configurando Subnets](/static/images/azure-posts/configurando-gateway.png)
- Name: GatewaySubnet
- 