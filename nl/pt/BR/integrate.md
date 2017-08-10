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

# Integrando o agente
{: #integrate}

Para publicar o agente para uso em produção, deve-se executar etapas adicionais para suportar as funções executadas pelo agente e disponibilizá-lo aos usuários de maneira segura.
{: shortdesc}

## Escolha um método de integração

Escolha uma das maneiras a seguir para integrar seu agente:

- Inclua a interface de bate-papo fornecida por {{site.data.keyword.IBM_notm}} no estado em que se encontra para seu website voltado para o consumidor.
  Consulte [Incluindo o widget de bate-papo fornecido para sua UI](integrate_add-chat.html).

- Amplie a janela do bate-papo fornecido para customizá-lo de acordo com as suas necessidades.
  Consulte [Incluindo o widget de bate-papo fornecido para sua UI](integrate_add-chat.html).

- Crie sua própria interface de bate-papo usando o Client SDK fornecido.
  Consulte [Construindo um bate-papo da interface customizada](integrate_custom-chat.html).

- Inclua o agente em um canal de suporte existente e use a API parainteragir com o agente de maneira programada.
  Consulte [Incluindo o agente em um canal de suporte](integrate_backend.html).

### Antes de começar

Independente do método utilizado para publicar o agente para uso em produção, faça um clone do agente por segurança. Ter uma cópia não integrada do agente permite que você teste as mudanças ou inclusões na funcionalidade na cópia de teste antes de fazê-las no agente que está sendo usado em um ambiente de produção. Consulte [Clonando o agente](agent-create.html#clone) para obter informações adicionais.
