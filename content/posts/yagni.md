---
title: YAGNI You Aren't Gonna Need It
date: 2023-09-10T21:22:47-03:00
draft: false
description: YAGNI é um acrônimo que significa "You Aren't Gonna Need It" (Você não vai precisar disso, em português). É um princípio da engenharia de software que se baseia na ideia de que os desenvolvedores não devem adicionar funcionalidades ou código que não são estritamente necessários no momento presente. Em vez disso, eles devem se concentrar em implementar apenas as funcionalidades que são solicitadas ou comprovadamente necessárias para o sistema. O objetivo é evitar o desperdício de tempo e recursos em funcionalidades que podem nunca ser usadas ou que podem ser adicionadas posteriormente, quando realmente forem necessárias.
---

"YAGNI" é um acrônimo que significa "You Aren't Gonna Need It" (Você não vai precisar disso, em português). É um princípio da engenharia de software que se baseia na ideia de que os desenvolvedores não devem adicionar funcionalidades ou código que não são estritamente necessários no momento presente. Em vez disso, eles devem se concentrar em implementar apenas as funcionalidades que são solicitadas ou comprovadamente necessárias para o sistema. O objetivo é evitar o desperdício de tempo e recursos em funcionalidades que podem nunca ser usadas ou que podem ser adicionadas posteriormente, quando realmente forem necessárias. Vou explicar o conceito em detalhes e fornecer exemplos:

**Princípio YAGNI em Detalhes:**

1. **Foco na Necessidade Atual:** O princípio YAGNI enfatiza que os desenvolvedores devem se concentrar nas funcionalidades que são necessárias no momento presente para atender aos requisitos do sistema. Isso significa não gastar tempo implementando recursos que não estão sendo solicitados ou que não têm um caso de uso imediato.

2. **Evitar Suposições Futuras:** YAGNI encoraja os desenvolvedores a evitar fazer suposições sobre o que pode ser necessário no futuro. Em vez disso, o desenvolvimento deve ser orientado pelos requisitos atuais e pelas necessidades dos usuários.

3. **Mantém o Código Simples:** Ao evitar a adição de funcionalidades desnecessárias, o código do sistema permanece mais simples e fácil de entender. Cada funcionalidade adicional aumenta a complexidade do código, tornando-o mais difícil de manter.

**Exemplos de YAGNI:**

A seguir, apresento dois exemplos concretos que demonstram como o princípio YAGNI pode ser aplicado:

**Exemplo 1: Desenvolvimento de um Sistema de Comércio Eletrônico**

Imagine que você esteja desenvolvendo um sistema de comércio eletrônico e seu cliente solicite que os clientes possam fazer compras online, adicionar itens ao carrinho e finalizar pedidos. O cliente não menciona a necessidade de um sistema de recomendação de produtos neste momento.

**Abordagem YAGNI:**

Nesse caso, a abordagem YAGNI sugere que você implemente apenas as funcionalidades essenciais para a realização de compras online, adicionando itens ao carrinho e finalizando pedidos. Você não deve gastar tempo desenvolvendo um sistema de recomendação de produtos, pois isso não foi solicitado e pode não ser necessário no momento. Se, no futuro, o cliente expressar interesse em recomendações de produtos, você pode adicionar essa funcionalidade posteriormente.

**Exemplo 2: Adição de Recursos de Autenticação**

Suponha que você esteja desenvolvendo um aplicativo da web simples que não exige autenticação de usuário inicialmente. No entanto, você prevê que, em algum momento no futuro, os usuários precisarão se autenticar para acessar recursos exclusivos.

**Abordagem YAGNI:**

Ao aplicar o princípio YAGNI, você começará com o desenvolvimento do aplicativo da web sem implementar a autenticação de usuário. Isso permite que você entregue rapidamente a funcionalidade principal do aplicativo. Quando a autenticação se tornar uma necessidade real e os requisitos forem claros, você pode adicionar a autenticação ao aplicativo.

Em ambos os exemplos, a abordagem YAGNI evita o desenvolvimento prematuro de funcionalidades que podem não ser necessárias imediatamente. Isso economiza tempo e recursos, mantém o código mais simples e permite que as funcionalidades sejam adicionadas à medida que são realmente necessárias, em vez de serem baseadas em suposições futuras. É importante lembrar que a aplicação do princípio YAGNI deve ser equilibrada com a necessidade de atender aos requisitos reais do cliente e do sistema, e não deve ser usada como desculpa para evitar funcionalidades legítimas ou planejamento adequado.
