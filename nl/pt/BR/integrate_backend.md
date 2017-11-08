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

# Incluindo o agente em um canal de suporte existente
{: #integrate_backend}

A API do {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} foi projetada para suportar a fácil transição de uma conversa entre o agente virtual e uma pessoa ou outro serviço de robô em uma infraestrutura de suporte existente. De fato, a equipe da LivePerson, Inc. fechou uma parceria com a {{site.data.keyword.IBM}} para implementar apenas uma integração. Para obter detalhes adicionais, consulte [Integração do LiveEngage](integrate_backend.html#liveperson) abaixo.
{: shortdesc}

Para você mesmo construir uma solução simples, é possível codificar seu aplicativo de forma que todos os recursos que estão configurados para serem transferidos para um agente humano sejam transmitidos para um canal existente que é monitorado pela equipe de suporte. Consulte [Respostas do dW ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://developer.ibm.com/answers/questions/318623/where-can-i-find-documentation-examples-on-integra/ "Ícone de link externo"){: new_window} para obter informações sobre como transferir uma conversa para o Slack, por exemplo. 

Para usar a API do {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} para integrar o agente virtual em um canal de suporte existente, conclua essas etapas:

1.  Recupere as chaves API que são necessárias para fazer chamadas API. Consulte [Obtendo chaves API](publish.html#api-keys) para obter detalhes. 

1.  Use as APIs REST do {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} para interagir com o robô programaticamente. Acesse o portal **[{{site.data.keyword.IBM_notm}} developerWorks API Explorer](https://developer.ibm.com/api/view/id-339:title-Watson_Virtual_Agent){: new_window}** para acessar as APIs REST no {{site.data.keyword.Bluemix_notm}}.

1.  Para obter o ID do robô, execute uma das seguintes ações:
    - Para obter o ID do robô da interface com o usuário da ferramenta de configuração do {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, conclua as seguintes etapas:
      1.  No menu principal ![Icon with three horizontal lines](images/hamburger.png)  do{{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}, clique em **Documentation (Documentação)** e, em seguida, clique na guia **Publish (Publicar)**.
      1.  Copie o valor botID do bloco de script.

    - Para obter o ID do robô do website API Explorer, execute essas etapas:
      1.  Conecte-se ao [IBM developerWorks API Explorer ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://developer.ibm.com/api/ "Ícone de link externo"){: new_window}. Clique em **My APIs (Minhas APIs)** e, em seguida, clique no quadro do {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}. 
      1.  Clique em **Documentation>Retrieve Bot (Documentação>**Recuperar Bot)** na barra de navegação. 
      1.  Clique em **USE** na parte superior da janela de referência do API explorer.
      1.  Role para baixo até a seção *Parâmetros de consulta e caminho* e clique em **TEST (TESTE)**.
      >**Nota:** Você deve selecionar uma chave para usar com a API antes de fazer o teste. 

      1.  O ID do robô é exibido no parâmetro `bot_id` na resposta resultante. 

## Integração LiveEngage
{: #liveperson}

O {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} foi projetado para trabalhar em harmonia com suas contrapartes humanas. 

Por exemplo, LivePerson, Inc., um provedor de soluções do sistema de mensagens de negócios móveis em nuvem e on-line, fez parceria com a IBM para integrar um robô do {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} em sua experiência de bate-papo do LiveEngage. O **LiveEngage** é uma plataforma de classe corporativa, baseada em nuvem, que permite que consumidores enviem mensagens de suas marcas favoritas diretamente. A nova oferta, **LiveEngage with Watson**, inclui respostas de um robô do {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} para interação com representantes de cuidado humano introduzidos continuamente, em tempo real, somente se necessário.

O robô do LivePerson usa muitos dos seguintes comportamentos, que são oferecidos pelo {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}:

- Aceitar conversas que são roteadas para ele do serviço externo. 
- Acionar a transferência de conversas para o serviço externo nas seguintes condições:
    - O cliente pede para falar com um agente humano.
    - Um recurso é configurado para rotear para um agente humano.
    - O cliente pergunta sobre um assunto que o robô não foi projetado para reconhecer e direcionar. 
- Identificar e relatar o ponto na conversa em que o usuário para de entender o robô ou perde o interesse na conversa.
- Reconhecer quando a conversa termina e notificar o serviço para ativar quaisquer atividades pós-interação para começar. 
- Ao transferir uma conversa, inclua informações sobre a intenção do usuário para que a conversa possa ser roteada para o agente humano que é mais experiente no direcionamento de solicitações desse tipo. 
- Ao transferir uma conversa, inclua o histórico do bate-papo para que a pessoa que está assumindo a questão entenda o contexto da conversa que ocorreu até o momento.

Para solicitar acesso à oferta, consulte o [website do LivePerson ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://engage.liveperson.com/usage/watson/?utm_medium=website&utm_source=IBM&utm_campaign=Watson "Ícone de link externo"){: new_window}.
