+++
author = "Manuel Sanchez"
title = "Deploy Azure Digital Twins con Terraform"
date = "2021-07-30"
description="Los modelos digitales de Azure Digital Twins son representaciones dinámicas actualizadas del mundo real. Mediante el uso de las relaciones de los modelos de DTDL personalizados, conectará gemelos a un gráfico dinámico que representa el entorno."
tags = [
    "Azure", "Digital Twins", "IoT", "Terraform"
]
categories = [
    "Azure", "Digital Twins", "IoT", "Terraform"
]
images  = ["images/posts/ADT.svg"]
thumbnail = "images/posts/ADT.svg"
comment = false
+++

Esta mañana he visto que ya habian liberado el modulo de **[Azure Digital Twins para terraform](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/digital_twins_instance)**

Y estoy seguro de que una vez que usted también lee a través de él, usted aprenderá que usted tiene que tomar varios pasos con el fin de lograr la configuración de Azure Digital Twins.
Voy a intentar ahorrarte algo de tiempo, proporcionándote una configuración básica de terraform que te ayudará a ponerte en marcha en un abrir y cerrar de ojos.

> Los modelos digitales de Azure Digital Twins son representaciones dinámicas actualizadas del mundo real. Mediante el uso de las relaciones de los modelos de DTDL personalizados, conectará gemelos a un gráfico dinámico que representa el entorno.

### 1. Crear el fichero providers.tf con el siguiente contenido

~~~
    terraform {
    required_version = "> 0.12"
    }

    provider "azurerm" {
    version = "~> 2.40.0"
    features {}
    }

    provider "azuread" {
    version = "~> 1.0"
    }
~~~

### 2. Crear el fichero main.tf con el siguiente contenido

~~~
{
    data "azurerm_subscription" "current" {}

    data "azurerm_client_config" "current" {
    }

    data "azuread_domains" "aad_domains" {
    only_default = true
    }

    # Create Resource Group
    resource "azurerm_resource_group" "rg" {
    name     = var.resource_group_name
    location = var.location
    tags     = var.tags
    }
}
~~~

### 3. Crear el fichero Digital_Twins.tf con el siguiente contenido

~~~
{
    resource "azurerm_digital_twins_instance" "example" {
    name                = var.dt_name
    resource_group_name = azurerm_resource_group.rg.name
    location            = var.location

    tags = var.tags
    }
}
~~~

### 4. Crear el fichero variable.tf con el siguiente contenido

~~~
# Commons
variable "location" {
  description = "(Required) Location of the all services to be created"
  default="westeurope"
}

variable "resource_group_name" {
  description = "(Required) Resource group name of the all services to be created"
  default= "DTexample"
}

variable "tags" {
  description = "(Required) Tags to be applied to the all services to be created"
  default = { Project = "DigitalTwins", Owner = "Manuel Sánchez" }
}

# Azure Digital Twins
variable "dt_name"{
  description = "(Required) Name of Digital Twins instance"
  default = "DTmanutest"
}
~~~

### 5. Desplegar la solución

~~~
az login
az account set -- subscription <--SubscriptionID-->
terraform init
terraform plan -out tf.plan
terraform apply ./tf.plan
~~~

De esta forma tendremos nuestro proyecto completamente automatizado.
Espero que le sirva de ayuda. Encuentre el código completo [aquí](https://github.com/Manuss20/azure.samples/tree/master/Digital_Twins_v2)

Saludos!