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

# Crear un agente
{: #agent-create}

Cuando se suscribe al servicio, se le suministra un bot con un paquete de prestaciones de **General Customer Service (Servicio al cliente general)** habilitado. Puede crear bots adicionales con otros paquetes de prestaciones o que conversen con cliente en idiomas distintos al idioma inglés.
{: shortdesc}

Para dejar de utilizar un agente con paquete de prestaciones diferente como su agente primario, en primer lugar cree un agente nuevo con el paquete de prestaciones que desee y, a continuación, puede suprimir el agente que se le ha proporcionado inicialmente. Asegúrese de que realiza el cambio antes de emplear demasiado tiempo en la configuración del agente del servicio al cliente general. Consulte la sección [Suprimir un agente](agent-create.html#delete) para obtener más información. 

Si emplea tiempo configurando una instancia de agente para que quede perfecto, y desea desplegarlo para poder utilizarlo pero también experimentar con el mismo o probar algunas ideas de mejora, puede crear un clon del agente para crear una copia con fines de prueba. Consulte la sección [Clonar un agente](agent-create.html#clone) para obtener más detalles. 

## Límites del agente 

El número de agentes que puede crear depende de su plan de servicio. 

| Plan de servicio |      Número de agentes|
|------------------|----------------------:|
| Prueba           |                     2 |
| Estándar         |                    10 |
| Premium          |                   100 |

Tenga en cuenta que las llamadas a la API realizadas desde varios bots desplegados se añaden conjuntamente y cuentan en el número total de respuestas del agente virtual asignado a su suscripción. 

### Procedimiento

Siga estos pasos para crear un agente. 

1.  En el menú principal ![Icono con tres líneas horizontales](images/hamburger.png) , pulse **Create New Agent (Crear nuevo agente)**.

1.  Seleccione el tipo de paquete de prestaciones que desea que incluya el agente cuando se crea.
La ficha identifica los idiomas soportados. No obstante, no todas las prestaciones están disponibles en cada idioma. Pulse el enlace **View Details (Ver detalles)** para ver una lista completa de las prestaciones soportadas por idioma. 

1.  Pulse **Select (Seleccionar)** en una ficha de paquete de prestaciones para crear un agente nuevo que incluya dicho tipo de paquete. 

1.  Si es aplicable, seleccione el idioma y, a continuación, proporcione la información solicitada para el agente. 
   >**Nota:** La etiqueta del agente que especifique aquí solo se mostrará en la herramienta de administración de Watson Virtual Agent que utilice para gestionar el agente. No es el nombre de la persona de agente virtual que interactúa con sus usuarios. Puede definirlo o cambiarlo en la página **Settings (Ajustes)**.
1.  Pulse **Create (Crear)**.

## Clonación de un agente 
{: #clone}

Clone un agente para crear un agente nuevo con la misma configuración y valores que el original. Después de clonar el agente, el original y el clon dejan de estar unidos entre sí. Los cambios que realice en uno **no** se aplican al otro. 

No puede crear un clon de un agente en un idioma diferente al idioma del original. 

### Procedimiento

Siga estos pasos para crear un agente. 

1.  Abra la página **Settings (Ajustes)** del agente que desea clonar. 

1.  Desplácese y, a continuación, pulse **Clone Agent (Clonar agente)**.

1.  Proporcione la información solicitada para el agente. 
   >**Nota:** La etiqueta del agente que especifique aquí solo se mostrará en la herramienta de administración de Watson Virtual Agent que utilice para gestionar el agente. No es el nombre de la persona de agente virtual que interactúa con sus usuarios. Esto lo define en otra ubicación.
1.  Pulse **Clone (Clonar)**.

## Suprimir un agente
{: #delete}

Si no está utilizando un agente, suprímalo para que no continúe en el recuento de su límite de número de agentes. 

### Procedimiento

Siga estos pasos para crear un agente. 

1.  Abra la página **Settings (Ajustes)** del agente que desea suprimir. 

1.  Desplácese y, a continuación, pulse **Delete Agent (Suprimir agente)**.

1.  Cuando se le solicite, escriba el texto `delete` y, a continuación, pulse **OK (Aceptar)**.
