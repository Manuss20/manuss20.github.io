+++
author = "Manuel Sanchez"
title = "The power of Azure Functions"
date = "2019-02-09"
description="Azure Functions es una de las nuevas soluciones que nos ofrece Azure para ejecutar fácilmente pequeños fragmentos de código, o «funciones», en la nube como servicio FaaS (Arquitectura Serverless). Podemos escribir el código que necesita para el problema en cuestión, sin preocuparse de toda la aplicación o la infraestructura para ejecutarlo."
tags = [
    "Azure", "Azure Functions", "Functions", "Serverless", "SaaS", "Cloud"
]
categories = [
    "Azure", "Azure Functions", "Functions", "Serverless", "SaaS", "Cloud"
]
images  = ["img/posts/The-power-of-Azure-Functions.jpg"]
+++

Azure Functions es una de las nuevas soluciones que nos ofrece Azure para ejecutar fácilmente pequeños fragmentos de código, o «funciones», en la nube como servicio FaaS (Arquitectura Serverless). Podemos escribir el código que necesita para el problema en cuestión, sin preocuparse de toda la aplicación o la infraestructura para ejecutarlo. 

Además nos permite utilizar el lenguaje de desarrollo que prefiera, como C#, F#, Node.js, Java o PHP, etc… Por su puesto, sólo pagamos por el tiempo que nuestras funciones se están ejecutando o, lo que es lo mismo, por los recursos de Azure que necesita para su ejecución.

Algunos de los ejemplos donde usar las functions:

- Trigger desde una Queue de Azure Storage
- Trigger desde una Queue de Azure Service Bus
- Trigger desde un Topic de Azure Service Bus
- Webhook
- Petición HTTP
- Ejecución programada por tiempo
- Trigger desde un Blob de Azure Storage
- Trigger desde un Event Hub

> *Una plataforma para cargar el código de la aplicación, ejecutar y administrar la aplicación sin tener que pensar en configurar ningún servido*

Podemos comprarlo con los servicios de Windows en una arquitectura OnPremises, Azure Functions nos cubre un gran número de casos de uso en llamadas a back-end de nuestras aplicaciones. Ya que este modelo se basa en ejecutar código de backend sin administrar los servidores o las aplicaciones, el escalado horizontal es completamente automático y gestionado por el proveedor donde hemos alojado nuestro código.

Si nos ponemos manos a la obra para definir una arquitectura Cloud, será un gran aliado para resolverá vuestros problemas.

Saludos!