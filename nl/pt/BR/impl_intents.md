---

copyright:
  years: 2015, 2017
lastupdated: "2017-08-01"

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

# Implementando recursos principais
{: #impl_intents}

Entenda as tarefas de desenvolvimento que devem ser concluídas para suportar os tipos de resposta selecionados para determinados recursos.
{: shortdesc}

Considere como você deseja manipular os recursos a seguir, no mínimo:

- ***Nenhum dos acima***

    A resposta que você definir para esse recurso será retornada aos usuários sempre que eles inserirem uma entrada de que o sistema não pode reconhecer e
mapear para um recurso ativado. Como resultado, ela poderá ser exibida para usuários várias vezes, especialmente se você não ativar muitos recursos. Pense sobre como você deseja
que o agente virtual responda. Uma resposta de texto, como *Sinto muito. Eu não entendo sobre o que você está perguntando.* é suficiente. Se
você desejar que os usuários tenham a opção de contatar um agente humano, será possível incluir o texto, *Insira o 'agente' a ser transferido para um
agente humano.* Esta entrada aciona o evento `agent`, que é explicado abaixo. Consulte [Como
nenhum dos acima é usado](/docs/services/virtual-agent/personalize.html#none_of_the_above) para obter mais informações.

- **Intenção e recursos **Conectar ao agente* com o tipo de resposta *Transferir para agente humano***

    Esses recursos transferem o usuário para um agente humano. Deve-se incluir a lógica que transfere a conversa para a sua equipe de suporte. Uma abordagem
que é possível tomar é incluir a lógica que se conecta a um serviço externo que já é usado para gerenciar solicitações recebidas em seu site de suporte ao cliente. Problemas
que o agente virtual não pode direcionar podem ser transferidos para a sua equipe de suporte como parte de sua fila existente de solicitações de suporte a serem
priorizadas e direcionadas. Para implementar a lógica de transferência, atenda ao evento de `agent` e defina as funções para executar quando o evento
é acionado. Consulte
[dwAnswers ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/answers/search.html?f=&amp;type=question&amp;redirect=search/search&amp;q=watson-virtual-agent&amp;q=human){: new_window} para obter ideias.

- **Recursos com o tipo de resposta *Usar a conversa integrada***

    Se você mantém as configurações padrão para os recursos principais que são configurados para usar o tipo de resposta de conversa integrada e esses
recursos estão ativados, então, deve-se incluir uma lógica para suportar a troca de informações e transações de negócios que são manipuladas pelas conversas
integradas. Consulte [Implementando a lógica para suportar a conversa integrada](/docs/services/virtual-agent/impl_intents.html#backend_transaction) para obter mais detalhes.

- **Recursos com o tipo de resposta *Usar a sua própria conversa***

    Para recursos complexos que requerem um diálogo customizado para manipular a troca de informações com o usuário, é possível escrever um diálogo usando o
serviço do {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}. Consulte
[Incluindo diálogos customizados para recursos principais](/docs/services/virtual-agent/personalize.html#use_custom) para obter mais detalhes.

## Implementando a lógica para suportar conversa integrada
{: #backend_transaction}

Saiba como trocar informações e processos de negócios completos que podem ocorrer quando os usuários interagem com recursos que são configurados para usar a
conversa integrada.

### Sobre essa Tarefa

Alguns dos recursos principais que são configurados para usar o tipo de resposta de conversa integrada por padrão podem transacionar processos de negócios. O
seu aplicativo deve ser capaz de registrar a transação com os sistemas backend de registro.

- Se você implementar o widget de bate-papo {{site.data.keyword.IBM_notm}} fornecido, ele reconhecerá eventos que são acionados por determinadas
respostas do usuário. No entanto, há etapas adicionais que deve-se executar para atender a esses eventos em seu aplicativo para que seja possível concluir as
transações iniciadas no seu sistema backend.
- Se você não está usando o widget de bate-papo fornecido, então, deve-se assegurar que a sua interface com o usuário customizado pode reconhecer eventos que
são acionados pelos fluxos de conversas integradas e manipulá-los apropriadamente.

Por exemplo, com o recurso **Atualizar endereço**, um usuário pode mudar o endereço para cobrança em sua conta. Deve-se gravar o código que
obtém o novo endereço por meio do agente virtual e atualiza a conta do usuário em seu sistema de registro com as novas informações.

É importante observar que o propósito de um diálogo é apenas reunir informações do usuário. As informações fornecidas pelo usuário são armazenadas em uma das
duas maneiras:

- As informações que não forem sensíveis ou privadas serão armazenadas no contexto de diálogo, que é um objeto de dados disponível para ambos, o robô e o seu
aplicativo.
- Informações sensíveis ou privadas (como números de cartão de crédito) são armazenadas em variáveis privadas, que estão disponíveis apenas para o seu
aplicativo e não são transmitidas para o robô. 

### Procedimento

Para implementar completamente as transações de negócios acionadas por meio de recursos com respostas de conversa integrada, conclua as etapas a
seguir:

1. Inclua a lógica em seu aplicativo que obtém informações de perfil para o usuário atual do sistema backend para mostrar na janela de bate-papo antes das
informações serem mudadas. Por exemplo, mostrar aos usuários um saldo da conta antes que eles a paguem.

    Use a ação `getUserProfileVariables`. Esta ação obtém as variáveis e as configura no perfil.

    ```
    IBMChat.subscribe('action:getUserProfileVariables', function(data) {
     var variables = data.message.action.args.variables; // specify the variables you want to get in this array
       for (var i = 0; i < variables.length; i++) {
           var value = something(variables[i]) 
           /*do something to get the value of variables[i]. might be an ajax call or getting 
           data from local cookies. Depends on where you stored the information.*/
           window.IBMChat.profile.set(variables[i], value);
       }
       IBMChat.sendSilently('success'); // or cancel or failure
    });
    ```
    {: screen}

    Este exemplo usa uma chamada REST para obter informações sobre um saldo da conta e uma data de vencimento.

    ```
    var xmlHttp = new XMLHttpRequest();
      xmlHttp.onreadystatechange = function() { 
        if (xmlHttp.readyState == 4 && xmlHttp.status == 200)
          callback(xmlHttp.responseText);
      }
      xmlHttp.open("GET", url, true);
      xmlHttp.send(null);
    }
    /* Get information from the backend database and add it
    into the profile with IBMChat.profile.set(). */
    IBMChat.subscribe('action:getUserProfileVariables', function(data) {
     /*
     data = {
       message: {
          text: ['some text'],
                action: {
                     name: 'getUserProfileVariables',
                     args: {
                         variables: [
                    "bill_amount",
                    "payment_due_date"
                ]
                     }
                }
       }
       
     }
     */
      
     httpGetAsync('http://yourdomain.com/userprofile', function(user) {
       /* The record on the backend system might return information like this.
       user = {
         "bill_amount": 42.01,
         "payment_due_date": "11/24/2008"
       }
       */
       var variables = data.message.action.args.variables;
       for (var i = 0; i < variables.length; i++) {
         var value = user[variables[i]]);
         window.IBMChat.profile.set(variables[i], value);
       /* Now the chat widget can use the values it retrieved from the backend service. */
       }
       IBMChat.sendSilently('success'); // or cancel or failure
     });
    });
    ```
    {: screen}

1. Inclua lógica em seu aplicativo que primeiro atende à ação que inicia o processo de negócios e, em seguida, executa o processo de negócios.

    Para obter uma lista de ações que são associadas a recursos que têm tipos de resposta de conversa integrada, veja
[https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md#action ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md#action){: new_window}.

### Fazer um pagamento
{: #makeapayment}

    Execute as etapas a seguir para implementar o código que suporta esta transação.
    1. O seu aplicativo deve recuperar o saldo atual do usuário e a data de vencimento do sistema backend. Use o método `action:getUserProfileVariables` para obter e configurar as variáveis `bill_amount` e `payment_due_date`
    na loja de perfil.
    1. O seu aplicativo deve atender ao evento `payBill` e definir a lógica para executar quando o evento é acionado.
    1. O seu aplicativo também deve atender ao evento `sendPaymentReceipt` e definir a lógica para executar quando o evento é acionado.

### Atualizar endereço
{: #updateaddress}

    1. O widget de bate-papo usa um layout de formulário para perguntar pelas informações de novo endereço do usuário e armazená-las no perfil automaticamente. Ele armazena estas variáveis de perfil:

        ```
        user_street_address1
        user_street_address2
        user_locality
        user_state_or_province
        user_zipcode
        ```
        {: screen}

    1. O seu aplicativo deve atender ao evento `updateAddress`.

        ```
        IBMChat.subscribe('action:updateAddress', function(data) {<your-code>}
        ```
        {: screen}

        Defina uma função que obtém e envia o novo endereço e o tipo de endereço (`address_type`) para o sistema backend quando a ação `updateAddress` é acionada.

        Para coletar dados com muitos valores, como um endereço residencial, é possível usar o layout de formulário que é construído no widget de bate-papo. Os usuários inserem valores em múltiplos campos e, em seguida, enviam o formulário inteiro. Por exemplo, para enviar o novo endereço para o seu site por meio de uma chamada REST POST, é possível usar a lógica como esta.

        ```
        /* When a user enters information into a form, it is automatically added 
        to the user profile. So a typical flow would be to include a form layout in the 
        chat window, and then call this action after the form is submitted */
        IBMChat.subscribe('action:updateAddress', function(data) {
          var record = {
            "first_name": IBMChat.profile.get('first_name'),
            "last_name": IBMChat.profile.get('last_name'),
            "user_street_address1": IBMChat.profile.get('user_street_address1'),
            "user_street_address2": IBMChat.profile.get('user_street_address2'),
            "user_locality": IBMChat.profile.get('user_locality'),
            "user_state_or_province": IBMChat.profile.get('user_state_or_province'),
            "user_zipcode": IBMChat.profile.get('user_zipcode')
          };
          httpPostAsync('/updateRecord/', record, function(err, response) {
            if (err) IBMChat.receive('There was an error updating the address.');
          });
        });
        ```
        {: screen}

        Para obter mais informações sobre layouts integrados, veja [https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md#layout ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-virtual-agents/virtual-agent-dialog/blob/master/dialog-contract.md#layout){: new_window}.

### Atualizar o número do telefone de contato
{: #updatephone}

    1. O widget de bate-papo usa um layout de formulário para perguntar o novo número do telefone do usuário e o armazena no perfil automaticamente. Ele armazena estas variáveis de perfil:

        ```
        user_phone_number
        phone_number_type
        ```
        {: screen}

    1. O seu aplicativo deve atender ao evento `updatePhoneNumber` e definir a lógica para obter e enviar o novo número do telefone e tipo para o sistema backend quando o evento é acionado.

### Atualizar e-mail
{: #updateemail}

    1. O widget de bate-papo usa um layout de formulário para perguntar o novo endereço de e-mail do usuário e o armazena no perfil automaticamente. Ele armazena estas variáveis de perfil:

        ```
        user_email_address
        email_type
        ```
        {: screen}

    1. O seu aplicativo deve atender ao evento `updateEmail` e definir a lógica para obter e enviar o novo endereço de e-mail para o sistema backend quando o evento é acionado. Ele também envia informações sobre para quais tipos de notificação usar o novo endereço (`email_type`).
