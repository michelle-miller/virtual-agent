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

# Análisis de la actividad de los usuarios
{: #dashboard}

La página Métricas contiene un panel de control con visualizaciones que le ayudan a comprender los datos recopilados por el agente virtual.
{: shortdesc}

Para que el panel de control tenga datos que compartir, primero la instancia de {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} {{site.data.keyword.virtualagentshort}} debe estar desplegada y los usuarios deben participar en conversaciones con el agente virtual durante al menos 30 minutos.

## Acerca de las métricas

Las métricas de la página se actualizan cada 30 minutos con datos de las conversaciones que se producen entre el agente virtual y los usuarios. Estas proporcionan conocimientos como:

- Cuántas conversaciones están teniendo lugar
- Cuántos usuarios, nuevos y recurrentes, están participando en conversaciones con el agente virtual
- Qué desean hacer los clientes o qué información buscan más y menos (según qué intenciones se desencadenan más o menos)

Las métricas pueden ayudarle a buscar áreas donde algún trabajo adicional podría mejorar considerablemente el rendimiento del agente virtual:

- Comparar temas populares con las intenciones y las entidades que el servicio está entrenado para reconocer. Las diferencias pueden ayudarle a descubrir nuevas intenciones o terminología que puede enseñar al agente virtual.
- Revise las intenciones identificadas con mayor frecuencia justo antes de que los usuarios soliciten hablar con un agente humano. La investigación de las causas de las escalaciones puede ayudarle a priorizar dónde concentrar los futuros esfuerzos de entrenamiento. Puede determinar si las consultas de los usuarios se están interpretando incorrectamente, si en el servicio falta una intención común, si las respuestas asociadas con una intención requieren una mejora, etc.

Las métricas también pueden ayudarle a planificar las asignaciones de recursos de agentes humanos según los datos sobre las áreas geográficas en las que la utilización del agente virtual es más y menos habitual, así como las horas puntas de conversación.

Las métricas analizan los datos de las conversaciones a bajo nivel, centrándose en los artefactos que contienen prestaciones, que incluyen:

- **Entities (Entidades)**

    Una *entidad* representa un término u objeto relevante para una intención y que proporciona un contexto específico para una intención. Por ejemplo, una entidad podría representar una ciudad donde el usuario desea encontrar la ubicación de un negocio, o el importe del pago de una factura. En la interfaz de usuario, el nombre de una entidad siempre tiene como prefijo el carácter `@`.

- **Intents (Intenciones)**

    Una *intención* representa la finalidad de la entrada de un usuario. Cada prestación utiliza un clasificador de lenguaje natural que puede evaluar una expresión del usuario y encontrar una intención predefinida, si existe. En la interfaz de usuario, el nombre de una intención siempre tiene como prefijo el carácter `#`.

### Procedimiento

1.  Abra la página **Metrics (Métricas)** para el agente actual.

    La parte superior de la página muestra un resumen de los principales puntos de datos y proporciona una vista rápida del comportamiento del agente. Para cada punto de datos, el porcentaje de cambio realizado a lo largo del tiempo seleccionado se muestra entre paréntesis. Se visualiza (N/D) para *no disponible* hasta que transcurre el periodo y se puede medir y mostrar un cambio.

    Los números que se muestran en el resumen a veces pueden diferir de los números que se muestran en otras páginas. Por ejemplo, el número total de interacciones que se muestra aquí podría diferir del número total que se muestra en el separador **Interactions (Interacciones)**. La diferencia se puede producir porque la información de resumen se agrega y actualiza con un intervalo de 30 minutos mientras que el separador **Interactions (Interacciones)** se actualiza en tiempo real.

    Para obtener más información, detalle más en los datos de cada separador.
    - **Agent Metrics (Métricas del agente)**

        Averigüe qué información desean obtener sus usuarios y qué desean hacer cuando interactúan con el agente virtual, y qué objetivos de los usuarios el agente virtual no ha podido satisfacer.
        - El diagrama interactivo **Intents &amp; Entities (Intenciones y entidades)** proporciona conocimientos sobre cómo el servicio {{site.data.keyword.conversationshort}} está interpretando la entrada de los usuarios. Muestra qué entidades ha utilizado el servicio como ayuda para identificar la intención del usuario.

            Se utiliza la sintaxis siguiente como ayuda para interpretar más rápidamente la información en el diagrama:
            - `#<intent-name>`
            - `@<entity-name>`

            Pulse una intención para ver qué entidades han ayudado al servicio a comprender la entrada del usuario como lo ha hecho. O bien pulse una entidad para ver qué intenciones ha ayudado al servicio a identificar.

        - La gráfica **Topics (Temas)** captura las palabras o frases pronunciadas con mayor frecuencia por los usuarios en una conversación. Revise la gráfica para comprender sobre qué están más interesados a hablar los usuarios. Las palabras de esta gráfica son distintas de las entidades capturadas en el diagrama Intenciones y entidades. Las entidades son palabras que se ha entrenado al servicio {{site.data.keyword.conversationshort}} a comprender y a asociar con intenciones determinadas. Las palabras capturadas en la gráfica Temas son simplemente las palabras que se encuentran con mayor frecuencia en las conversaciones con los usuarios. Estas dos podrían o no coincidir. No pierda de vista las palabras de la gráfica Temas para mantenerse informado sobre sus usuarios y descubrir nuevos temas sobre los que es posible que deseen obtener información o sobre los que deseen realizar alguna acción. Los temas populares que siguen siendo populares podrían ser buenos candidatos para nuevas entidades que pueden ayudar a {{site.data.keyword.watson}} a reconocer intenciones existentes, o podrían sugerir nuevas intenciones sobre las que podría enseñar a {{site.data.keyword.watson}}.

    - **User Metrics (Métricas de usuario)**

        Obtenga información sobre la ubicación de los usuarios y el volumen de las conversaciones.

    - **Interactions (Interacciones)**

        Consulte las transcripciones de conversaciones individuales.

        Las transcripciones no contienen información de identificación personal. Incluso el nombre del usuario que ha participado en la conversación se mantiene privado. En su lugar, se utiliza un ID de usuario como 509JAJT8PX. Cualquier otra información de identificación personal que proporcionen los usuarios durante la conversación, por ejemplo, números de teléfono o códigos postales, se sustituye con variables que indican los tipos de datos proporcionados, pero no los propios datos.

        > **Nota:** el término *interacción* representa una conversación que tiene lugar entre el usuario y el agente virtual. Se inicia cuando el usuario inicia una conversación con el agente virtual y finaliza cuando finaliza la sesión de la ventana de conversación (lo que tiene lugar cuando se cierra la sesión al usuario o este cierra la sesión, cierra la ventana de conversación o actualiza la ventana de conversación). A menudo una interacción incluye más que un simple intercambio de palabras; los usuarios pueden pulsar botones, ver gráficos como mapas y realizar otras transacciones. Y, a diferencia de una llamada telefónica a un servicio de atención al cliente, la interacción con la sesión de conversación del agente virtual no finaliza tan pronto como el usuario deja de interactuar con él. El agente virtual no tiene ningún otro sitio donde ir; se mantiene en espera en caso de que el usuario desee hacer o preguntar algo más. Por ejemplo, si el usuario pregunta algo, y 20 minutos después pregunta algo más (y lo hace en la misma sesión de ventana de conversación), ambos intercambios se tratan como una única interacción con una duración de 25 minutos.

1.  Si descubre datos significativos que desee compartir con otras personas, puede exportarlos en formato CSV.
