+++
author = "Manuel Sanchez"
title = "Azure Event Grid"
date = "2018-11-18"
description="Azure Event Grid es una plataforma de enrutamiento de eventos inteligentes administrados que le permite reaccionar en tiempo real a los cambios que están ocurriendo en sus aplicaciones alojadas en Azure o en cualquier recurso de Azure que usted posea."
tags = [
    "Azure", "Azure Event Grid", "Event Grid", "Processes", "Cloud"
]
categories = [
    "Azure", "Azure Automation", "Azure Event Grid",  "Cloud"
]
images  = ["images/posts/azureeventgrid.jpg"]
thumbnail  = "images/posts/azureeventgrid.jpg"
comment = false
+++

Azure Event Grid es una plataforma de enrutamiento de eventos inteligentes administrados que le permite reaccionar en tiempo real a los cambios que están ocurriendo en sus aplicaciones alojadas en Azure o en cualquier recurso de Azure que usted posea.

Actualmente para recibir una notificación de un cambio de etapa en un recurso, como un nuevo registro en una base de datos, o cuando alguien crea una Máquina Virtual, generalmente piensa en un sondeo programado o continuo. Eso significa que estamos constantemente consumiendo potencia de cómputo (CPU y recursos de red) para monitorear todos estos cambios.

Pero ahora con Azure Event Grids esto puede cambiar. ¡Podemos hacer que tus aplicaciones envíen eventos cuando se produce un cambio de estado, al igual que las notificaciones automáticas! Esos solo se activan una vez que se envían los eventos procesables.

Cualquier componente que esté interesado en esos eventos puede suscribirse y recibir notificaciones sin sondeo, reduciendo los recursos y costes.

> *Event Grid nos permite poder integrarlo con cualquier servicio o aplicaciones debido a que todo se basa en HTTP, Event Grid puede integrarse virtualmente con cualquier servicio o aplicación. Aquí entra en acción las ventajas de Event Grid, la **simplificación** de **operaciones** y en la **automatización** de la seguridad a través de una aplicación de políticas más sencilla, expandiendo los escenarios sin servidor y sin fuentes de eventos. Permitiendo una mejor comunicación e integración entre sus servicios y aplicaciones basados en eventos.*

Event Grid, gestiona los eventos de Azure incorporados de los servicios de Azure, así como los eventos personalizados de sus aplicaciones y los publica en tiempo real. Puede escalar y manejar dinámicamente millones de eventos cada segundo y Azure ofrece 99.99 de disponibilidad (Acuerdos de nivel de servicio ) para cargas de trabajo en producción.

A medida que se reciben los eventos, Event Grid facilita la activación de acciones programáticas a través de los controladores de eventos, como pueden ser Azure Automation, Event Hubs, Azure Functions, Azure Logic Apps, ect.

![imagen event grid](images/posts/event_grid1.jpg)

Podéis encontrar algunos ejemplos acerca de Event Grid en: [https://docs.microsoft.com/es-es/azure/event-grid/monitor-virtual-machine-changes-event-grid-logic-app](https://docs.microsoft.com/es-es/azure/event-grid/monitor-virtual-machine-changes-event-grid-logic-app)

Saludos!