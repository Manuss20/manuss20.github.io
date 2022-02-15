+++
author = "Manuel Sanchez"
title = "Despliegue Azure Web App para contenedores con Terraform"
date = "2018-12-20"
description="Una Web App es un servicio en el cual ponen a disposición una plataforma previamente configurada para alojar aplicaciones web, APIs tipo REST y Back Ends para aplicaciones móviles. Tales aplicaciones pueden estar desarrolladas en cualquier lenguaje conocido como puede ser .Net, Java, Ruby, NodeJS, Python, PHP, entre otros."
tags = [
    "Azure", "WepApps", "Azure Web App", "Terraforms", "Cloud", "Containers", "Docker", "IaC"
]
categories = [
    "Azure", "WenApps", "Azure Web App", "Terraforms", "Cloud", "Containers", "Docker", "IaC"
]
images  = ["images/posts/despliege_WebApps_Azure_Terraforms.jpg"]
thumbnail  = "images/posts/despliege_WebApps_Azure_Terraforms.jpg"
comment = false
+++

Una Web App es un servicio en el cual ponen a disposición una plataforma previamente configurada para alojar aplicaciones web, APIs tipo REST y Back Ends para aplicaciones móviles. Tales aplicaciones pueden estar desarrolladas en cualquier lenguaje conocido como puede ser .Net, Java, Ruby, NodeJS, Python, PHP, entre otros.

Una de las ventajas de estos servicios es que permiten escalar el tamaño de recursos que la Web App necesita con facilidad y le evitan a los desarrolladores de software y empresas tener que instalar y administrar un entorno completo de sistema operativo, base de datos e intérpretes de lenguajes.

Actualmente la tendencia en los desarrollos web modernos está usando Docker containers para “dockerizar” sus aplicaciones. El uso en entornos donde se está creando una arquitectura de microservicios, es probable que esos despliegues los estén haciendo con herramientas de automatización como pueden ser AKS o Terraform.

En este ejemplo nos centraremos en la automatización con Terraform. Actualmente si deseamos usar Azure Web Apps como host de nuestro contenedor, la documentación de Terraform no nos da toda la información necesaria para poder hacerlo. Por ello a continuación os facilito un ejemplo de cómo poder configurarlo:

~~~
# Use the Azure Resource Manager Provider
provider "azurerm" {
  version = "~> 1.15"
}

# Create a new Resource Group
resource "demo_resource_group" "group" {
  name     = "webapp-containers-demo"
  location = "westeurope"
}

# Create an App Service Plan with Linux
resource "azurerm_app_service_plan" "appserviceplan" {
  name                = "${demo_resource_group.group.name}-plan"
  location            = "${demo_resource_group.group.location}"
  resource_group_name = "${demo_resource_group.group.name}"

  # Define Linux as Host OS
  kind = "Linux"

  # Choose size
  sku {
    tier = "Standard"
    size = "S1"
  }

  properties {
    reserved = true # Mandatory for Linux plans
  }
}

# Create an Azure Web App for Containers in that App Service Plan
resource "azurerm_app_service" "dockerapp" {
  name                = "${demo_resource_group.group.name}-dockerapp"
  location            = "${demo_resource_group.group.location}"
  resource_group_name = "${demo_resource_group.group.name}"
  app_service_plan_id = "${azurerm_app_service_plan.appserviceplan.id}"

  # Do not attach Storage by default
  app_settings {
    WEBSITES_ENABLE_APP_SERVICE_STORAGE = false

    /*
    # Settings for private Container Registires  
    DOCKER_REGISTRY_SERVER_URL      = ""
    DOCKER_REGISTRY_SERVER_USERNAME = ""
    DOCKER_REGISTRY_SERVER_PASSWORD = ""
    */
  }

  # Configure Docker Image to load on start
  site_config {
    linux_fx_version = "DOCKER|appsvcsample/static-site:latest"
    always_on        = "true"
  }

  identity {
    type = "SystemAssigned"
  }
}
~~~

Para asegurarnos que se configura correctamente debe de prestar especial atención a que las siguientes propiedades estén correctamente definidas en su archivo de configuración, de lo contrario no funcionará correctamente el despliegue:

~~~
reserved = true
WEBSITES_ENABLE_APP_SERVICE_STORAGE = false
~~~

Saludos!