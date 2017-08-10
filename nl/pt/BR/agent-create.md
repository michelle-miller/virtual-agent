---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-10"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Criando um agente
{: #agent-create}

Ao assinar o serviço, é fornecido um robô com pacote de recursos **General Customer Service (Atendimento Geral ao Cliente)** no idioma inglês ativado. É possível criar robôs adicionais com outros pacotes de recursos ou que conversam com clientes em idiomas diferentes do inglês.
{: shortdesc}

Para passar a usar um agente com um pacote de recursos diferente como seu agente primário, primeiro crie um novo agente com o pacote de recursos desejado, em seguida, é possível excluir o agente que foi fornecido para você inicialmente. Certifique-se de fazer a comutação antes de gastar muito tempo configurando o agente General Customer Service (Atendimento Geral ao Cliente). Consulte [Excluindo um agente](agent-create.html#delete) para obter informações adicionais. 

Se você gastar tempo configurando uma instância de agente para funcionar corretamente, e desejar implementá-la para uso, mas ainda poder experimentá-la ou tentar ideias de aprimoramento, é possível clonar o agente para criar uma cópia para fins de teste. Consulte [Clonando um agente](agent-create.html#clone) para obter detalhes adicionais. 

## Limites do Agente

O número de agentes que podem ser criados depende de seu plano de serviço. 

| Plano de Serviços     |      Número de agentes |
|------------------|----------------------:|
| Tentativa            |                     2 |
| Padrão         |                    10 |
| Premium          |                   100 |

Lembre-se de que as chamadas API feitas de vários robôs implementados são reunidas e consideradas o número total de respostas do agente virtual atribuídas à sua assinatura.

### Procedimento

Siga estas etapas para criar um agente.

1.  No menu principal ![Ícone com três linhas horizontais](images/hamburger.png), clique em **Create New Agent (Criar Novo Agente)**.

1.  Escolha o tipo de pacote de recursos que você deseja que seja fornecido para o agente quando ele for criado. O quadro identifica quais idiomas são suportados. No entanto, nem todos os recursos estão disponíveis em todos os idiomas. Clique no link **View Details (Visualizar Detalhes)** para ver uma lista completa de recursos suportados por idioma. 

1.  Clique em **Select (Selecionar)** em um quadro do pacote de recursos para criar um novo agente para o qual é fornecido esse tipo de pacote.

1.  Se aplicável, escolha o idioma e, em seguida, forneça as informações solicitadas para o agente. 
   >**Nota:** O rótulo do agente especificado aqui é exibido somente no conjunto de ferramentas de administração do Watson Virtual Agent que é usado para gerenciar o agente. Não é o nome da persona do agente virtual que interage com seus usuários; é possível definir ou mudar isso na página **Settings (Configurações)**.

1.  Clique em **Create (Criar)**.

## Clonando um agente
{: #clone}

Clone um agente para criar um novo agente com a mesma configuração e configurações que o original. Depois de clonar o agente, o original e o clone não estarão mais ligados um ao outro. As mudanças feitas em um **não** são aplicadas ao outro. 

Não é possível criar um clone de um agente em um idioma que seja diferente do idioma do original. 

### Procedimento

Siga estas etapas para criar um agente.

1.  Abra a página **Settings (Configurações)** do agente que você deseja clonar. 

1.  Role para baixo e, em seguida, clique em **Clone Agent (Clonar Agente)**.

1.  Forneça as informações solicitadas para o agente. 
   >**Nota:** O rótulo do agente especificado aqui é exibido somente no conjunto de ferramentas de administração do Watson Virtual Agent que é usado para gerenciar o agente. Não é o nome da persona do agente virtual que interage com seus usuários; você define isso em outro lugar.

1.  Clique em **Clone (Clonar)**.

## Excluindo um agente
{: #delete}

Se não estiver usando um agente, exclua-o para que ele não continue sendo considerado em seu limite de número de agentes. 

### Procedimento

Siga estas etapas para criar um agente.

1.  Abra a página **Settings (Configurações)** do agente que você deseja excluir. 

1.  Role para baixo e, em seguida, clique em **Delete Agent (Excluir Agente)**.

1.  Quando solicitado, digite o texto `delete (excluir)` e, em seguida, clique em **OK**.
