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

# Visão geral
{: #index}

O {{site.data.keyword.virtualagentfull}} é um conjunto de componentes pré-configurados cognitivos baseado no serviço do
{{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}. Configurando o agente virtual com
informações de sua empresa, é possível implementar rapidamente um robô de bate-papo automatizado que se comunique com os seus clientes para ajudá-los a alcançarem os
seus objetivos.
{: shortdesc}

O {{site.data.keyword.watson}}&trade; {{site.data.keyword.virtualagentshort}} fornece os componentes a seguir:

- Uma ferramenta de configuração que pode ser usada para configurar como você deseja que o robô responda a vários tipos de solicitações.
- Um conjunto de recursos que representam objetivos comuns ou ações que os clientes normalmente desejam executar (como "Pagar minha conta" ou "Diga-me o seu
horário comercial").
- Um modelo de língua natural treinado para identificar as intenções com base na entrada de cliente.
- Um fluxo de diálogo de conversa que pode manipular algumas solicitações complexas solicitando informações adicionais, gerar respostas e acionar eventos a
serem manipulados por seu aplicativo. Se o diálogo predefinido não satisfizer as suas necessidades, será possível implementar o seu próprio diálogo customizado usando
as ferramentas de serviço do {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}.
- Um mecanismo para aumentar os recursos do agente com recursos customizados que você define em uma área de trabalho
do {{site.data.keyword.conversationshort}} e vincula ao agente.
- Um widget de bate-papo que é possível integrar em sua página da web e um SDK que é possível usar para desenvolver um widget de bate-papo customizado.
- Um conjunto de APIs que é possível usar para integrar o seu aplicativo com o agente virtual.

## Visão geral arquitetural
{: #arch_overview}

O diagrama a seguir ilustra a arquitetura de uma implementação típica do {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}}:

![Visão Geral Arquitetural ](images/arch-overview.png)

A implementação inclui os componentes principais a seguir:

- Serviço do **{{site.data.keyword.conversationshort}}**

    Uma instância do serviço do {{site.data.keyword.watson}} {{site.data.keyword.conversationshort}}. O serviço do
{{site.data.keyword.conversationshort}} fornece os artefatos para recursos: as intenções, as entidades e o fluxo de diálogo, juntamente com o processamento
cognitivo subjacente que alimenta os recursos do robô de bate-papo. Você interage diretamente com a área de trabalho do {{site.data.keyword.conversationshort}}
quando deseja implementar apenas um diálogo customizado ou recurso customizado.

    Para obter mais informações sobre as intenções e diálogos, consulte a documentação de serviço do
[{{site.data.keyword.conversationshort}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://www.ibm.com/watson/developercloud/doc/conversation/configure-workspace.html){: new_window}.

- **Robô**

    Um robô construído no serviço do {{site.data.keyword.conversationshort}}, incluindo um conjunto de recursos. O robô é treinado para reconhecer
consultas de usuário relacionadas à participação do cliente, como solicitações para informações básicas da empresa e pagamento de conta. A ferramenta de configuração
de robô permite configurar informações específicas da empresa que podem ser fornecidas em resposta para consultas de usuário e para configurar a resposta para cada
recurso.

- **O website de sua empresa**

    O seu aplicativo de negócios voltado para o cliente, que manipula a comunicação com o robô do {{site.data.keyword.watson}}
{{site.data.keyword.virtualagentshort}} e com os seus sistemas de registro (como bancos de dados de clientes ou sistemas de faturamento).

- **Janela Bate-papo**

    A interface de bate-papo do agente virtual, que os clientes usam para se comunicarem com o robô. É possível usar o widget de bate-papo fornecido, com ou
sem customização ou é possível usar o SDK do cliente para implementar o seu próprio widget de bate-papo.

