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

# Publicando o agente para usá-lo como demo
{: #publish}

Em menos de 10 minutos, é possível publicar um agente em um site de teste para compartilhá-lo com colegas e avaliar juntos se ele atende às necessidades de sua organização.
{: shortdesc}

Para publicar o agente em um site de teste, conclua as seguintes etapas.

1.  Determine onde na página você deseja que a janela de bate-papo do robô seja exibida. No `<div>` elemento HTML que define a área de destino, inclua um atributo do id se um não estiver definido. Você usará o atributo do id para referir-se ao elemento mais tarde. Por exemplo, `<div id="ibm-chat-root"></div>`.

1.  Siga as instruções em [Obtendo chaves API](publish.html#api-keys) para recuperar as seguintes chaves:
    - ID do Cliente
    - Cliente secreta do token

1.  A partir do menu principal ![Icon with three horizontal lines](images/hamburger.png), clique em **Documentation (Documentação)** e, em seguida, role para baixo até a seção **Publish (Publicar)**.

1.  Se você possuir múltiplos agentes, clique na seta para baixo para obter o ID do bot para o agente que você deseja publicar.

    Este botID é o ID que foi gerado pelo serviço e designado ao seu bot.

    Um bloco de script é gerado e exibido em sua página. Este script pode ser copiado e colocado em uma página HTML para renderizar o agente na página. Você deve substituir alguns dos valores no script com os valores adequados para a sua instância.

1.  Copie o bloco de script e cole em um texto ou editor de HTML.

    ``` Javascript
    <script src='https://unpkg.com/@watson-virtual-agent/chat-widget@1.6.0/dist/chat.min.js'>
    </script>
    <script>
      IBMChat.init({
        el: 'Ibm_chat_root',
        baseURL: 'Https://api.ibm.com/virtualagent/run/api/v1',
        botID: 'YOUR_BOT_ID',
        XIBMClientID: 'YOUR_IBM_CLIENT_ID',
        XIBMClientSecret: 'YOUR_IBM_CLIENT_SECRET'
      });
    </script>
    ```

1.  Substitua os seguintes valores de atributo:
    - **el**: Especifique o ID do elemento que você escolheu para usar na Etapa 1.
    - **XIBMClientID**: Inclua o valor de ID do cliente que foi copiado anteriormente.
    - **XIBMClientSecret**: Inclua o valor do token secreto do cliente que foi copiado anteriormente.

   Use os valores baseURL e botID que são especificados no script; eles são gerados pelo serviço.

   **Importante:** Mantenha os valores de XIBMClientID e XIBMClientSecret da forma mais privada possível.

1.  Integre e inicialize o widget de bate-papo do Watson Virtual Agent colando o script revisado em sua página da web.

   Inclua o script o mais próximo possível da tag de fechamento `</body>` para evitar que o script bloqueie o restante da página de ser renderizado. Esta colocação também assegura que qualquer elemento associado ao script será totalmente renderizado pelo tempo que o script for executado.

1.  Atualize a página da web e dê uma chance ao agente!

   O widget de bate-papo está associado e renderizado para o elemento HTML designado na Etapa 1. É possível ocultar ou mostrar e posicionar esse elemento. O widget se estende a toda a altura e largura do elemento. A largura máxima é 768 pixels e a altura mínima é 300 pixels.

Quando estiver pronto para colocar o agente para trabalhar ajudando seus clientes diretamente, você deve executar algumas etapas adicionais. Consulte [Integrando o agente](integrate.html) para obter mais detalhes.

## Obtendo chaves de API
{: #api-keys}

Para provar que você tem permissão para usar os serviços da API do Watson Virtual Agent, as seguintes chaves devem estar associadas a quaisquer chamadas API que são feitas para o serviço:

- ID do Cliente
- Cliente secreta do token

Siga estas etapas para recuperar as credenciais.

1.  Acesse o website do [IBM developerWorks API Explorer ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://developer.ibm.com/api/ "Ícone de link externo"){: new_window} e conecte-se com o mesmo IBMid que foi usado para se inscrever na assinatura de serviço. Crie um nome do usuário, se necessário. Clique no link **My APIs (minhas APIs)** no cabeçalho da página.

1.  Procure o quadro do {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} e, em seguida, clique no ícone da chave associado a ela.

1.  Se não selecionou, selecione a chave que você deseja usar. São geradas duas credenciais para a chave e são mostradas com seus valores ofuscados em dois campos. Passe o mouse sobre os campos.

1.  Clique no botão **SHOW (MOSTRAR)** para remover a ofuscação dos valores de campos.

1.  Será preciso fornecer esses valores posteriormente, portanto, copie-os para um arquivo de texto.
    - O primeiro campo contém a chave de ID do cliente.
    - O segundo campo contém o token secreto do cliente.

  ![Add node](images/api-explorer.jpg)
