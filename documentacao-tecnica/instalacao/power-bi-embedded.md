# Power BI Embedded

Para facilitar o processo de instalação do Power Embedded, criamos este tutorial para auxiliar nossos clientes a realizar a instalação do Power Embedded.

### Pré-requisitos para realizar a instalação

Como o Power Embedded é um sistema no formato SaaS, você não precisará contratar ou gerenciar nenhum servidor, aplicação ou banco de dados, irá apenas utilizar o software como um serviço.

Para configurar o Power Embedded na sua empresa, precisamos que os seguintes pré-requisitos sejam atendidos antes de agendarmos a instalação:

* Conta de um usuário do Azure com permissão para criar a capacidade Fabric ou Embedded.
* Conta de um usuário do Azure com permissão para criar grupos e aplicativos no Azure AD.
* Conta de um usuário do Azure que possua a role “Fabric administrator” para acessar o [portal de administração do Power BI.](https://app.powerbi.com/admin-portal/tenantSettings)

Durante a reunião de instalação do sistema, que é feita junto com o cliente, precisamos que seja fornecido um usuário com as permissões listadas acima, ou que tenha alguma pessoa do time do cliente, com essas permissões, que possa compartilhar a tela e executar as ações que serão instruídas.



### Como criar o usuário do Power Embedded no Azure AD

Para criar o aplicativo que será utilizado pelo Power Embedded, você precisará acessar [esse link aqui](https://portal.azure.com/#view/Microsoft\_AAD\_IAM/ActiveDirectoryMenuBlade/\~/RegisteredApps).

Na tela abaixo, clique no botão “New registration

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2023/08/Manual-de-Instalacao-do-Power-Embedded-3.png" alt=""><figcaption></figcaption></figure>

Agora você deverá escolher um nome para o aplicativo que irá criar no seu Azure AD. O nome fica a seu critério.

Após isso, clique no botão “Register”, no final da página

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2023/08/Manual-de-Instalacao-do-Power-Embedded-5.png" alt=""><figcaption></figcaption></figure>

Após a criação desse aplicativo, você será direcionado para a tela de visão geral.

Copie o valor do campo “Application (client) ID” e salve em um bloco de notas. Essa chave é o que você irá colar no campo “**Id do Cliente do Power BI**” na configuração da organização do Power Embedded

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2023/08/Manual-de-Instalacao-do-Power-Embedded-6.png" alt=""><figcaption></figcaption></figure>

Agora clique na opção “Certificates & secrets” e em seguida, clique no botão “New client secret

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2023/08/Manual-de-Instalacao-do-Power-Embedded-7.png" alt=""><figcaption></figcaption></figure>

Na nova tela aberta, digite uma descrição para esse segredo (conforme a sua preferência) e selecione a validade deste segredo.

Sugiro escolher 24 meses para só precisar se preocupar com essa expiração depois de 2 anos (Sim, após o prazo escolhido, esse segredo irá expirar e o sistema irá PARAR de funcionar. Você precisará gerar um novo segredo e atualizar no Power Embedded).

Agora clique no botão “Add”, no final da página

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2023/08/Manual-de-Instalacao-do-Power-Embedded-8.png" alt=""><figcaption></figcaption></figure>

Agora copie o campo “Value” gerado. Existe um botão de copiar ao lado dessa chave.

Anote e guarde bem essa chave, pois essa será a ÚNICA vez que você poderá vê-la. Caso você perca essa chave, não será possível recuperá-la: Você precisará gerar um novo segredo e atualizar no sistema.

Esse valor que destaquei e você copiou, você deverá colar no campo “**Chave de Acesso do Cliente do Power BI**” da tela de configuração do Power Embedded

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2023/08/Manual-de-Instalacao-do-Power-Embedded-9.png" alt=""><figcaption></figcaption></figure>



### Sincronizar usuários e grupos do Azure AD (Entra ID)

Para integrar o Power Embedded com o Azure AD (Entra ID) e importar os usuários e grupos.

Na mesma tela de registro de aplicativos, clique em “API permissions” e em “Add a Permission”.

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2024/07/Permissoes-de-APIS.png" alt=""><figcaption></figcaption></figure>

Na próxima tela selecione a opção do “Microsoft Graph”.

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2024/07/Permissoes-aplicativo.png" alt=""><figcaption></figcaption></figure>

Em seguida seleciona a opção de “Application permissions”.

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2024/07/Microsoft-Graph.png" alt=""><figcaption></figcaption></figure>

Na aba a seguir, busque por “Directory” e selecione a primeira opção “Directory.Read.All” e clique em “Add permissions”.

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2024/07/Directory-1.png" alt=""><figcaption></figcaption></figure>

Para finalizar basta conceder o consentimento do administrador clicando em “Grant admin consent for”.

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2024/07/Conssentimento-admin.png" alt=""><figcaption></figcaption></figure>

Pronto, quando finalizar as próximas etapas já conseguirá importar os usuários e grupos do Azure AD (Entra ID) para o Power Embedded.



### Adicionando o usuário do Power Embedded a um novo grupo do AD

Para liberar permissões no Portal de Administração do Power BI para o Service Principal que você acabou de criar, ele obrigatoriamente precisa fazer parte de um grupo de segurança do Azure AD (Entra ID).

Para fazer isso, acesse [este link aqui](https://portal.azure.com/#view/Microsoft\_AAD\_IAM/GroupsManagementMenuBlade/\~/AllGroups) e clique no botão “New group”

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2023/08/Manual-de-Instalacao-do-Power-Embedded-11.png" alt=""><figcaption></figcaption></figure>

Selecione a opção “Security” no campo “Group type” e digite um nome à sua preferência para esse grupo que estamos criando.

Clique no link “Owners” e adicione as pessoas que ficarão responsáveis pelo Power Embedded

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2023/08/Manual-de-Instalacao-do-Power-Embedded-12.png" alt=""><figcaption></figcaption></figure>

Clique no link “No members selected” da categoria “Members”

Na tela que foi aberta, digite o nome do Service Principal que você criou para filtrar. Selecione o Service Principal na lista e clique no botão “Select”, no final da página

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2023/08/Manual-de-Instalacao-do-Power-Embedded-13.png" alt=""><figcaption></figcaption></figure>

Agora que você selecionou o membro para adicionar à este novo grupo, clique no botão “Create”, no final da página

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2023/08/Manual-de-Instalacao-do-Power-Embedded-14.png" alt=""><figcaption></figcaption></figure>



### Como criar a capacidade do Power BI Embedded

Para criar a capacidade do Power BI Embedded, utilize [esse link aqui](https://portal.azure.com/#create/Microsoft.PowerBIDedicated).

Selecione a sua assinatura, o grupo de recursos que irá utilizar, dê um nome para a sua capacidade do Embedded (lembrando que o nome precisa ser único para toda a região selecionada) e selecione a região onde o recurso será criado

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2023/08/Manual-de-Instalacao-do-Power-Embedded-17.png" alt=""><figcaption></figcaption></figure>

Lembre-se de especificar o tamanho da capacidade que irá criar e clique no botão “Review + Create” e depois no botão “Create”, no final da página

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2023/08/Manual-de-Instalacao-do-Power-Embedded-18.png" alt=""><figcaption></figcaption></figure>

Para o recurso de otimização de capacidade funcionar corretamente, você precisa adicionar as permissões necessárias na capacidade para o usuário/grupo do Power Embedded.

Acesse a sua capacidade Embedded ou Fabric no portal do Azure, seleciona o item “IAM (Controle de acesso)” no menu esquerdo, depois clique no botão “Adicionar” -> “Adicionar atribuição de função

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2023/10/Power-Embedded-Adicionar-permissoes-na-capacidade.png" alt=""><figcaption></figcaption></figure>

Clique na aba “Funções de administrador privilegiadas”, marque a função “Contribuidor” e depois clique no botão “Próximo

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2023/10/Power-Embedded-Adicionar-permissoes-na-capacidade-Contribuidor.png" alt=""><figcaption></figcaption></figure>

Marque a opção “Usuário, grupo ou entidade de serviço”, clique no link “+ Selecionar membros”, localize e selecione o usuário ou grupo do Power BI Embedded que você criou e clique no botão “Selecionar

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2023/10/Power-Embedded-Adicionar-permissoes-na-capacidade-Adicionar-usuario.png" alt=""><figcaption></figcaption></figure>

Clique no botão “Examinar + atribuir” e na próxima tela de resumo da operação, clique nesse botão novamente

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2023/10/Power-Embedded-Adicionar-permissoes-na-capacidade-Confirmar.png" alt=""><figcaption></figcaption></figure>

Agora vamos adicionar o usuário do Power Embedded como administrador da capacidade.

Para isso, clique no item “Administradores de capacidade do Power BI” no menu da esquerda

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2023/10/Power-Embedded-Adicionar-administrador-da-capacidade.png" alt=""><figcaption></figcaption></figure>

Localize e selecione o usuário que você criou para o Power Embedded e depois, clique no botão “Selecionar"

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2023/10/Power-Embedded-Adicionar-administrador-da-capacidade-Confirmar.png" alt=""><figcaption></figcaption></figure>

Um novo registro contendo o ID do objeto do service principal do Power Embedded irá aparecer na lista dos administradores da capacidade.

**Não se esqueça de clicar no botão “Salvar” para confirmar a alteração.**

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2023/10/Power-Embedded-Adicionar-administrador-da-capacidade-Salvar.png" alt=""><figcaption></figcaption></figure>



### Como liberar as permissões necessárias no Portal de Administração do Power BI

Utilizando um usuário com permissão de administrador do Power BI, acesse [este link aqui](https://app.powerbi.com/admin-portal/tenantSettings).

Desça a página até encontrar a seção “Developer settings” (ou aperte Ctrl+F e busque por “api”)

Marque a opção “Allow service principals to use Power BI APIs”.

Por questões de segurança, marque a opção “Specific security groups” na seção “Apply to:” e selecione o grupo de segurança que criamos no começo deste tópico (no meu caso, “PowerEmbedded-Group”)

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2023/08/Manual-de-Instalacao-do-Power-Embedded-15.png" alt=""><figcaption></figcaption></figure>

Clique no botão “Apply”.

Ainda na categoria “Developer settings”, marque a opção “Embed content in apps” e adicione o grupo de segurança que você criou no filtro “Specific security groups”, na opção “Apply to”.

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2023/09/Power-BI-Admin-Settings-Developer-Embed-Content-in-Apps-e1695681301598.png" alt=""><figcaption></figcaption></figure>

Desça mais um pouco a página e repita o mesmo processo para o item “Allow service principals to use read-only admin APIs”, na seção “Admin API Settings”.

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2023/08/Manual-de-Instalacao-do-Power-Embedded-16.png" alt=""><figcaption></figcaption></figure>

Pronto! Agora o Portal possui acesso ao seu ambiente do Power BI.



### Primeiro acesso ao Portal Administrativo

Acesse a área administrativa do Portal, acessando [esse link aqui](https://admin.powerportal.cloud/), logado com um usuário com permissão de “Administrador Global do Azure”.

Você irá autenticar na sua conta Microsoft e assim que terminar de logar, verá uma tela de solicitação de permissão no seu Azure AD.

**Marque a opção “Consent on behalf of your organization” e clique no botão “Accept”.**

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2023/08/Manual-de-Instalacao-do-Power-Embedded-4.png" alt=""><figcaption></figcaption></figure>



{% hint style="warning" %}
Esqueceu de marcar a opção “Consent on behalf of your organization” ou fez a instalação com uma conta que não era administrador?
{% endhint %}

<details>

<summary>Clique aqui para visualizar como liberar a permissão manualmente</summary>

Caso você tenha acessado o portal de administração utilizando um usuário sem as permissões necessárias, a tela acima talvez não apareça para você, e apareça, na verdade, a tela abaixo, quando você ou outro usuário tentar logar na área administrativa.

<img src="https://powerembedded.com.br/wp-content/uploads/2023/10/Enterprise-Application-Consentir-App-como-Administrador.png" alt="" data-size="original">

Se isso acontecer, você precisará autorizar a aplicação do Power Embedded (powerportal.cloud) em nome da organização, utilizando um usuário com permissões globais no Azure AD.

Para fazer isso, clique no link “[Enterprise Applications](https://portal.azure.com/#view/Microsoft\_AAD\_IAM/StartboardApplicationsMenuBlade/\~/AppAppsPreview/menuId\~/null)” do Azure AD (Entra ID)

[![](https://powerembedded.com.br/wp-content/uploads/2023/10/Aplicativos-empresariais.png)](https://powerembedded.com.br/wp-content/uploads/2023/10/Aplicativos-empresariais.png)

Localize e clique no aplicativo “powerportal.cloud”

[![](https://powerembedded.com.br/wp-content/uploads/2023/10/Aplicativos-empresariais-powerportal.cloud\_.png)](https://powerembedded.com.br/wp-content/uploads/2023/10/Aplicativos-empresariais-powerportal.cloud\_.png)

Clique no menu “Permissão” no painel da esquerda e depois clique no botão “Conceder consentimento do administador para …” e autorize a aplicação.

[![](https://powerembedded.com.br/wp-content/uploads/2023/10/Aplicativos-empresariais-Permissoes-powerportal.cloud\_.png)](https://powerembedded.com.br/wp-content/uploads/2023/10/Aplicativos-empresariais-Permissoes-powerportal.cloud\_.png)

Após confirmar as permissões, você será direcionado para o sistema e deverá criar a nova organização.

[![](https://powerembedded.com.br/wp-content/uploads/2023/08/Manual-de-Instalacao-do-Power-Embedded-2-1024x619.png)](https://powerembedded.com.br/wp-content/uploads/2023/08/Manual-de-Instalacao-do-Power-Embedded-2.png)

</details>



Após confirmar as permissões, você será direcionado para o sistema e deverá criar a nova organização.

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2023/08/Manual-de-Instalacao-do-Power-Embedded-2.png" alt=""><figcaption></figcaption></figure>



Nesta tela, você poderá configurar as seguintes configurações:

* **Nome:** É o nome da sua empresa. O sistema irá recuperar o nome cadastrado no Tenant do Azure, mas você poderá alterá-lo nesta tela ou futuramente, pela página de configurações do sistema.
* **Workspace:** É o workspace inicial do sistema. Você pode selecionar qualquer workspace nesse momento, pois isso poderá ser alterado posteriormente.
* **Id do Cliente do Power BI:** É o ID do Service Principal que será criado para integrar o Power Embedded com o seu Azure Active Directory (vamos explicar mais sobre isso logo abaixo).
* **Chave de Acesso do Cliente do Power BI:** É o segredo gerado para o Service Principal (vamos explicar mais sobre isso logo abaixo).
* **Domínio Customizado:** É o domínio da sua empresa (sem www ou https). Esse campo será utilizado para criar uma URL de acesso personalizada de acesso aos relatórios (ex: relatorios.suaempresa.com.br)

Com o Client ID e o Secret Value que você obteve no início da instalação e anotou em um bloco de notas, agora vamos utilizá-los na tela de configuração da organização do Power Embedded.

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2023/08/Manual-de-Instalacao-do-Power-Embedded-10-1.png" alt=""><figcaption></figcaption></figure>

Clique no botão “Criar Organização” e você já poderá começar a usar o Portal.



### Como integrar o Portal ao Workspace do Power BI?

Para que seja possível importar os relatórios do Power BI para o Power Embedded, você precisará fazer duas coisas no workspace:

1. Alterar a capacidade do Workspace para capacidade Premium (Embedded).
2. Adicionar o Service Principal criado (usuário do Power Embedded) como administrador dos workspaces que você quer importar relatórios (pode ser mais de 1).

Alterar a capacidade do Workspace para capacidade Premium (Embedded), acesse o workspace, clique nos 3 pontinhos e selecione a opção “Workspace settings"

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2023/08/Manual-de-Instalacao-do-Power-Embedded-19.png" alt=""><figcaption></figcaption></figure>

Na tela que foi aberta, clique no menu “Premium”, depois escolha a licença “Embedded” e no campo “License capacity”, selecione o recurso Embedded que você criou anteriormente na lista.

Clique no botão “Apply”, logo mais abaixo.

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2023/08/Manual-de-Instalacao-do-Power-Embedded-20.png" alt=""><figcaption></figcaption></figure>

A partir desse momento, esse workspace agora está na capacidade Premium e associado ao recurso do Power BI Embedded. Caso você pause esse recurso, o Workspace ficará inacessível, mesmo utilizando uma conta Pro e acessando direto pelo portal.

O último passo agora é adicionar o usuário do Service Principal ao Workspace.

Para adicionar o Service Principal criado como administrador de um workspace, acesse o workspace, clique nos 3 pontinhos e selecione a opção “Manage access"

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2023/08/Manual-de-Instalacao-do-Power-Embedded-21.png" alt=""><figcaption></figcaption></figure>

Clique no botão “+ Add people or groups”.

<figure><img src="https://powerembedded.com.br/wp-content/uploads/2023/08/Manual-de-Instalacao-do-Power-Embedded-22.png" alt=""><figcaption></figcaption></figure>

Pesquise pelo nome do grupo que foi criado anteriormente e lembre de alterar o nível de acesso para “Admin”. Após isso, clique no botão “Add”.

<figure><img src="../../.gitbook/assets/Screenshot 2024-11-05 181548.png" alt=""><figcaption></figcaption></figure>

Pronto! Agora o Power Embedded já possui acesso nesse workspace. Repita isso para todos os Workspaces que você quer importar relatórios.
