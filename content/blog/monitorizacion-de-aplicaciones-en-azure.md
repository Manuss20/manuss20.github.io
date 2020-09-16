+++
author = "Manuel Sanchez"
title = "Monitorización de aplicaciones en Azure"
date = "2019-11-22"
description="Azure Functions es una de las nuevas soluciones que nos ofrece Azure para ejecutar fácilmente pequeños fragmentos de código, o «funciones», en la nube como servicio FaaS (Arquitectura Serverless). Podemos escribir el código que necesita para el problema en cuestión, sin preocuparse de toda la aplicación o la infraestructura para ejecutarlo."
tags = [
    "Azure", "Azure Monitor", "Azure Application Insight", "Monitoring", "Cloud"
]
categories = [
    "Azure", "Azure Monitor", "Azure Application Insight", "Monitoring", "Cloud"
]
images  = ["img/posts/monitorizacion.jpg"]
+++

La mayoría de las compañías tendrán una mezcla de PaaS, IaaS y SaaS, lo que crea un desafío único cuando se trata de monitoreo. El objetivo es poder solucionar las cosas de manera proactiva antes de que sus usuarios y su empresa se vean afectados por fallos inesperados o un rendimiento poco optimo. Para ello vamos a hablar en este articulo sobre Azure Monitor y Application Insights:

#### Azure Monitor

Azure Monitor es un servicio de Azure que proporciona supervisión del rendimiento y la disponibilidad para aplicaciones y servicios en Azure, en otros entornos en la nube o en el entorno local. Azure Monitor recopila datos de varios orígenes en una plataforma de datos común en la que se pueden analizar las tendencias y las anomalías. Las características enriquecidas de Azure Monitor ayudan a identificar y responder rápidamente ante situaciones críticas que pueden afectar a la aplicación.

Las características de Azure Monitor que están habilitadas automáticamente, como la recopilación de métricas y los registros de actividad, que se proporcionan sin costé alguno. Es importante destacar que no existe una versión local de Azure Monitor ya que es un servicio en la nube escalable que procesa y almacena grandes cantidades de datos, aunque Azure Monitor puede supervisar los recursos que están en el entorno local y en otras nubes.

#### Application Insights

Application Insights es una característica de Azure Monitor que es un servicio de Application Performance Management (APM) extensible para desarrolladores y profesionales de DevOps. Úselo para supervisar las aplicaciones en directo. Detectará automáticamente anomalías en el rendimiento e incluye eficaces herramientas de análisis que le ayudan a diagnosticar problemas y a saber lo que hacen realmente los usuarios con la aplicación. Está diseñado para ayudarle a mejorar continuamente el rendimiento y la facilidad de uso. Funciona con diversas aplicaciones y en una amplia variedad de plataformas, como .NET, Node.js o Java EE, hospedadas en el entorno local, de forma híbrida o en cualquier nube pública. Se integra con el proceso de DevOps y tiene puntos de conexión a numerosas herramientas de desarrollo. Puede supervisar y analizar la telemetría de aplicaciones móviles mediante la integración con Visual Studio App Center.

Saludos!