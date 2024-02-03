+++
author = "Manuel Sanchez"
title = "Confidential containers in Azure Kubernetes Service"
date = "2023-06-01"
description="En este post quiero explicaros como podemos usar contenedores confidenciales en Azure Kubernetes Service (AKS) ya que nos ofrece una capa adicional de seguridad para proteger datos sensibles de nuestros contenedores, ideales para diversas aplicaciones que incluyen análisis de macrodatos y machine learning."
tags = [
    "Azure", "Azure Container Apps", "Containers", "Apps", "Modern Apps"
]
categories = [
    "Azure", "Azure Container Apps", "Containers", "Apps", "Modern Apps"
]
images  = ["images/posts/AKS.png"]
thumbnail = "images/posts/AKS.png"
comment = false
+++

En este post quiero explicaros como podemos usar contenedores confidenciales en Azure Kubernetes Service (AKS) ya que nos ofrece una capa adicional de seguridad para proteger datos sensibles de nuestros contenedores, ideales para diversas aplicaciones que incluyen análisis de macrodatos y machine learning.

### *¿Qué es Confidential containers en Azure Kubernetes Service?*

Azure Kubernetes Service (AKS) es un servicio de orquestación de contenedores que simplifica la implementación, administración y escalabilidad de las aplicaciones. Los contenedores confidenciales en AKS son una nueva característica que proporciona un nivel adicional de seguridad, lo que permite a los usuarios proteger sus datos más sensibles dentro de un contenedor.

Los contenedores confidenciales proporcionan un conjunto de características y funcionalidades para proteger aún más las cargas de trabajo de contenedor estándar para lograr mayores objetivos de seguridad y privacidad de los datos e integridad del código del entorno de ejecución. Azure Kubernetes Service incluye Contenedores confidenciales en AKS (preview).
  
### *¿Por qué apostar por Azure Kubernetes Service?*

Azure Kubernetes Service es una excelente opción para las organizaciones que buscan simplificar la administración de contenedores y aumentar la velocidad de desarrollo. Ofrece una plataforma segura y escalable para implementar aplicaciones, con características que incluyen balanceo de carga, monitoreo y diagnóstico integrados, seguridad de red y mucho más. Además, los contenedores confidenciales proporcionan una capa adicional de protección para los datos sensibles. Los contenedores confidenciales se basan en contenedores confidenciales Kata y cifrado basado en hardware para cifrar la memoria del contenedor. Establece un nuevo nivel de confidencialidad de los datos evitando que los datos de la memoria durante el cálculo estén en formato de texto no cifrado y legible. La confianza se obtiene en el contenedor a través de la atestación de hardware, lo que permite el acceso a los datos cifrados por entidades de confianza.
  
### *¿Cuáles son los beneficios?*

Los contenedores confidenciales en AKS ofrecen una serie de beneficios, entre ellos:  

- Seguridad mejorada: Los datos sensibles están protegidos dentro del contenedor, lo que aumenta la seguridad general de la aplicación.  
- Flexibilidad: Puedes ejecutar cualquier aplicación dentro de un contenedor confidencial.  
- Escalabilidad: Azure Kubernetes Service te permite escalar tus aplicaciones fácilmente para satisfacer la demanda.  
  
### *¿Que escenarios son ideales?*

- Ejecute análisis de macrodatos mediante Apache Spark para el reconocimiento de patrones de fraude en el sector financiero.
- Ejecutar ejecutores de GitHub autohospedados para firmar código de forma segura como parte de las prácticas de DevOps de integración continua e implementación continua (CI/CD).
- Inferencia y entrenamiento de machine Learning de modelos de MACHINE Learning mediante un conjunto de datos cifrado de un origen de confianza. Solo se descifra dentro de un entorno de contenedor confidencial para conservar la privacidad.
- Creación de salas limpias de macrodatos para la coincidencia de identificadores como parte del cálculo de varias partes en sectores como el comercio minorista con publicidad digital.
- Creación de zonas de aterrizaje de confianza cero de computación confidencial para cumplir las normativas de privacidad de las migraciones de aplicaciones a la nube.

### *¿Como creamos nuestro primer Confidential containers en Azure Kubernetes Service?*

Crear un contenedor confidencial en AKS es un proceso relativamente sencillo. Primero, debes configurar tu entorno de Azure y AKS. A continuación, puedes usar la línea de comandos de Azure para implementar tu contenedor confidencial. Para obtener instrucciones más detalladas, consulta la documentación oficial de Azure. Recuerda que es una característica en versión preliminar, por lo que es no esta recomendado para entornos de producción.

### *Conclusiones*

En mi opinión los contenedores confidenciales en AKS nos ofrecen un nivel de seguridad adicional para nuestras aplicaciones, lo que nos permite proteger nuestros datos más sensibles. Todo ello dentro del ecosistema que nos ofrece AKS, es una excelente opción para cualquier organización que busque una solución de escalable, segura y fácil de usar.  

Saludos!