---
title: Manage identities and governance in Azure [pt-br]
date: 2023-05-26T08:07:11-03:00
draft: false
description: The text "Manage identities and governance in Azure" discusses the role of Azure Active Directory (Azure AD) in identity management and governance in Azure. It explores concepts such as users, groups, and applications, and highlights the importance of multifactor authentication and role-based access control (RBAC). The summary emphasizes the integration of Azure AD with Office 365 and the significance of proper identity management to ensure security and compliance.
---

1.  **O que é o Azure Active Directory (AD) e qual é o seu papel na governança e gerenciamento de identidades no Azure?**
    O Azure Active Directory (AD) é um serviço de gerenciamento de identidades baseado em nuvem fornecido pela Microsoft. Ele desempenha um papel fundamental na governança e gerenciamento de identidades no Azure, permitindo que você crie e gerencie identidades (usuários e grupos) para acessar recursos do Azure e aplicativos. O Azure AD fornece recursos como autenticação, autorização, gerenciamento de acesso baseado em funções (RBAC) e controle de acesso a aplicativos para garantir a segurança e a conformidade dos recursos do Azure.
2.  **Quais são os principais conceitos relacionados à identidade no Azure, como usuários, grupos, aplicativos e serviços de diretório?**
    No Azure, os principais conceitos relacionados à identidade incluem: - Usuários: Representam indivíduos que podem autenticar e acessar recursos no Azure. - Grupos: São coleções lógicas de usuários que facilitam a atribuição e o gerenciamento de permissões em larga escala. - Aplicativos: Permitem que serviços, APIs e outros recursos acessem dados e recursos no Azure em nome dos usuários ou da organização. - Serviços de diretório: No contexto do Azure, refere-se ao Azure AD, que fornece serviços de diretório para gerenciar identidades e autenticação.
3.  **Como faço para criar e gerenciar usuários e grupos no Azure AD?**
    Você pode criar e gerenciar usuários e grupos no Azure AD usando o portal do Azure, o Azure PowerShell, a CLI do Azure ou por meio de programação usando as APIs do Azure AD. No portal do Azure, você pode acessar o serviço do Azure AD, criar usuários individuais e grupos, atribuir permissões e gerenciar outras configurações relacionadas às identidades.
4.  **Quais são as opções de autenticação disponíveis no Azure AD e como posso configurá-las?**
    O Azure AD oferece várias opções de autenticação, incluindo nome de usuário e senha, autenticação multifator, autenticação por meio de aplicativos móveis, autenticação baseada em certificados, autenticação federada com provedores de identidade externos, como o Azure AD Connect, e muito mais. Para configurar as opções de autenticação, você pode acessar as configurações de segurança do Azure AD no portal do Azure e habilitar as opções desejadas, como a autenticação multifator.
5.  **Como posso habilitar a autenticação multifator no Azure AD para aumentar a segurança das identidades?**
    Para habilitar a autenticação multifator no Azure AD, você pode seguir estes passos: - Acesse o portal do Azure e navegue até o serviço do Azure AD. - Selecione "Segurança" e, em seguida, "MFA (Autenticação Multifator)". - Siga as instruções para configurar as opções de autenticação multifator, como a autenticação por telefone, notificações por aplicativo móvel ou uso de tokens de hardware
        ## Principais métodos de gerenciameto de identidades

        O Azure AD (Azure Active Directory) e o RBAC (Controle de Acesso Baseado em Função) são dois conceitos distintos, mas relacionados, dentro do Azure.

        ## **Azure AD:**

        O Azure AD é um serviço de gerenciamento de identidades baseado em nuvem fornecido pela Microsoft. Ele é usado para criar e gerenciar identidades, como usuários e grupos, que podem autenticar e acessar recursos do Azure, bem como aplicativos. O Azure AD desempenha um papel fundamental na governança e gerenciamento de identidades no Azure. Ele fornece recursos de autenticação, autorização e gerenciamento de acesso a aplicativos, além de fornecer recursos de segurança, como autenticação multifator e integração com provedores de identidade externos.

        ## RBAC (Controle de Acesso Baseado em Função):

        RBAC é um modelo de controle de acesso que permite gerenciar o acesso a recursos específicos do Azure com base nas funções atribuídas aos usuários. Em vez de conceder permissões individuais a cada usuário, você pode criar funções personalizadas ou usar funções predefinidas do Azure, como proprietário, colaborador ou leitor, e atribuí-las aos usuários ou grupos. O RBAC permite controlar o que os usuários podem fazer em relação a recursos específicos, definindo permissões granulares com base em suas funções.

        Em resumo, o Azure AD é o serviço de gerenciamento de identidades no Azure, enquanto o RBAC é um modelo de controle de acesso que permite definir e gerenciar permissões para recursos específicos com base em funções. O Azure AD é responsável por autenticação e gerenciamento centralizado de identidades, enquanto o RBAC se concentra no controle de acesso granular a recursos no Azure. Ambos os conceitos trabalham juntos para fornecer governança efetiva e segurança na gestão de identidades e acesso aos recursos do Azure.

        Na Azure, existem diferentes tipos de identidades que estão relacionados ao Azure AD, RBAC e Office 365. Aqui estão os principais tipos de identidade em cada um desses serviços:

        ## Azure Active Directory (Azure AD):

        1. Usuários do Azure AD: São identidades individuais associadas a pessoas ou contas de usuário em uma organização. Essas identidades podem ser autenticadas e usadas para acessar recursos do Azure e aplicativos.
        2. Grupos do Azure AD: São coleções lógicas de usuários, grupos ou aplicativos. Eles podem ser usados para gerenciar permissões de forma eficiente, atribuindo permissões a grupos em vez de usuários individuais.
        3. Aplicativos do Azure AD: São entidades registradas no Azure AD que podem representar aplicativos ou serviços. Esses aplicativos podem solicitar acesso a recursos protegidos pelo Azure AD em nome dos usuários ou da organização.
        4. Identidades Gerenciadas pelo Azure AD para Recursos: Quando você cria recursos no Azure, como máquinas virtuais, bancos de dados ou serviços em nuvem, eles recebem uma identidade gerenciada pelo Azure AD. Essas identidades podem ser usadas para autenticar e autorizar o acesso a outros recursos do Azure.

        ## Azure RBAC (Controle de Acesso Baseado em Função):

        1. Proprietário: É a função com permissões mais elevadas e permite gerenciar todos os aspectos de um recurso no Azure, incluindo permissões RBAC.
        2. Colaborador: É uma função com permissões operacionais que permite gerenciar um recurso no Azure, mas não pode modificar as permissões RBAC ou conceder acesso a outros usuários.
        3. Leitor: É uma função de visualização que permite apenas a leitura de recursos, sem permissão para fazer alterações.

        ## Office 365:

        1. Contas de Usuário do Office 365: São identidades de usuário usadas para acessar serviços e aplicativos do Office 365, como o Microsoft Outlook, Microsoft Teams e SharePoint Online. Essas identidades são gerenciadas pelo Azure AD.
        2. Grupos do Office 365: São grupos usados para colaboração e compartilhamento de recursos no Office 365. Eles podem incluir usuários e conceder acesso a recursos compartilhados, como sites de equipe e caixas de correio compartilhadas.
        3. Serviços do Office 365: São serviços e aplicativos específicos do Office 365, como Exchange Online, SharePoint Online e Microsoft Teams. Eles têm suas próprias identidades e permissões associadas.

        Esses são alguns dos principais tipos de identidades nos serviços Azure AD, RBAC e Office 365. O uso dessas identidades varia de acordo com o serviço e o cenário específico de uso.

        ### Resumo

        O tópico "AZ-104: gerenciar identidades e a governança no Azure" abrange conceitos e práticas relacionados ao gerenciamento de identidades e governança no ambiente do Azure. Aqui está um resumo do que você precisa saber sobre essa sessão:

        1. Azure Active Directory (Azure AD): O Azure AD é um serviço de gerenciamento de identidades baseado em nuvem fornecido pela Microsoft. Ele desempenha um papel central na governança e gerenciamento de identidades no Azure.
        2. Identidades no Azure: As principais identidades no Azure incluem usuários do Azure AD, grupos do Azure AD, aplicativos do Azure AD e identidades gerenciadas pelo Azure AD para recursos.
        3. Controle de Acesso Baseado em Função (RBAC): O RBAC é um modelo de controle de acesso que permite gerenciar permissões para recursos específicos no Azure. Ele usa funções predefinidas ou personalizadas para atribuir permissões a usuários ou grupos.
        4. Autenticação e Autorização: O Azure AD fornece opções de autenticação, como autenticação multifator e integração com provedores externos. O controle de acesso é alcançado através do RBAC e políticas de acesso a recursos.
        5. Governança de Identidade: A governança de identidade no Azure envolve o estabelecimento de práticas para gerenciar o ciclo de vida de identidades, garantindo conformidade, aplicando políticas de segurança e auditoria.
        6. Práticas Recomendadas: Existem práticas recomendadas para gerenciar identidades e governança no Azure, como seguir o princípio do menor privilégio, implementar autenticação multifator, usar grupos para atribuir permissões e monitorar e auditar atividades.
        7. Integração com o Office 365: O Azure AD também é usado para gerenciar identidades no Office 365, permitindo o acesso a serviços como Exchange Online, SharePoint Online e Microsoft Teams.


        Essas informações fornecem uma visão geral dos principais pontos abordados no tópico "AZ-104: gerenciar identidades e a governança no Azure". Explorar esses conceitos e práticas irá ajudá-lo a compreender melhor como gerenciar identidades e garantir uma governança adequada no ambiente do Azure.
