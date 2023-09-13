---
title: DRY - Don't Repeat Yourself
date: 2023-09-12T23:19:41-03:00
draft: false
description: "DRY" é um acrônimo que significa "Don't Repeat Yourself" (Não Se Repita, em português). É um princípio fundamental da engenharia de software que enfatiza a importância de evitar a repetição de código e de informações em um sistema de software. A ideia por trás do DRY é que, ao eliminar a duplicação de código, você torna seu software mais eficiente, fácil de manter e menos propenso a erros. 
---

"DRY" é um acrônimo que significa "Don't Repeat Yourself" (Não Se Repita, em português). É um princípio fundamental da engenharia de software que enfatiza a importância de evitar a repetição de código e de informações em um sistema de software. A ideia por trás do DRY é que, ao eliminar a duplicação de código, você torna seu software mais eficiente, fácil de manter e menos propenso a erros. Aqui está uma explicação detalhada do DRY, juntamente com exemplos:

**1. Evitar Repetição de Código:**
O princípio DRY enfatiza que partes do código que executam a mesma funcionalidade não devem ser repetidas em várias partes do sistema. Em vez disso, o código deve ser encapsulado ou abstraído de tal forma que ele possa ser reutilizado sempre que necessário.

**Exemplo 1 - Função de Cálculo de Média:**

Suponha que você esteja escrevendo um programa que calcula a média de uma lista de números. Em vez de escrever a lógica de cálculo da média várias vezes em diferentes partes do código, você pode criar uma função ou método reutilizável para calcular a média e chamá-lo sempre que necessário.

```python
# Versão sem DRY (repetição de código)
lista1 = [10, 20, 30, 40, 50]
lista2 = [5, 15, 25]

soma1 = sum(lista1)
media1 = soma1 / len(lista1)

soma2 = sum(lista2)
media2 = soma2 / len(lista2)

# Versão com DRY (função reutilizável)
def calcular_media(lista):
    soma = sum(lista)
    return soma / len(lista)

lista1 = [10, 20, 30, 40, 50]
lista2 = [5, 15, 25]

media1 = calcular_media(lista1)
media2 = calcular_media(lista2)
```

**2. Manter um Único Ponto de Autoridade:**
DRY também significa que apenas uma parte do código deve ser a fonte ou ponto de autoridade para determinadas informações ou regras de negócio. Quando você precisa fazer uma alteração, é mais seguro e eficiente fazê-la em um único local, em vez de ter que rastrear e atualizar múltiplas cópias da mesma informação.

**Exemplo 2 - Constantes:**

Suponha que você tenha várias partes do seu código que usam um valor de imposto de 10%. Em vez de escrever "0.10" em várias partes do código, você pode definir uma constante chamada "TAXA_DE_IMPOSTO" e usá-la em todo o código. Se a taxa de imposto mudar, você só precisa atualizá-la em um lugar.

```python
# Versão sem DRY (repetição de valores)
subtotal1 = 100.00
imposto1 = subtotal1 * 0.10
total1 = subtotal1 + imposto1

subtotal2 = 200.00
imposto2 = subtotal2 * 0.10
total2 = subtotal2 + imposto2

# Versão com DRY (uso de constante)
TAXA_DE_IMPOSTO = 0.10

subtotal1 = 100.00
imposto1 = subtotal1 * TAXA_DE_IMPOSTO
total1 = subtotal1 + imposto1

subtotal2 = 200.00
imposto2 = subtotal2 * TAXA_DE_IMPOSTO
total2 = subtotal2 + imposto2
```

**3. Facilitar a Manutenção:**
Ao aderir ao DRY, o código é mais fácil de manter, pois as mudanças só precisam ser feitas em um lugar. Isso reduz a chance de inconsistências e erros que podem ocorrer quando o código duplicado é esquecido ou atualizado de maneira inconsistente.

**Exemplo 3 - Validação de Dados:**

Imagine que você está desenvolvendo um sistema que valida números de telefone em várias partes do código. Em vez de repetir a mesma lógica de validação de telefone em diferentes lugares, você pode criar uma função de validação reutilizável.

```python
# Versão sem DRY (repetição de lógica)
def validar_telefone(telefone):
    # Lógica de validação
    if len(telefone) != 10:
        return False
    for char in telefone:
        if not char.isdigit():
            return False
    return True

resultado1 = validar_telefone("1234567890")
resultado2 = validar_telefone("555-555-5555")

# Versão com DRY (função reutilizável)
def validar_telefone(telefone):
    # Lógica de validação
    if len(telefone) != 10:
        return False
    for char in telefone:
        if not char.isdigit():
            return False
    return True

resultado1 = validar_telefone("1234567890")
resultado2 = validar_telefone("555-555-5555")
```

Em resumo, o princípio DRY encoraja os desenvolvedores a evitar a duplicação de código e de informações, promovendo a reutilização de código, a clareza, a manutenibilidade e a consistência no desenvolvimento de software. Isso resulta em sistemas mais eficientes e menos propensos a erros.
