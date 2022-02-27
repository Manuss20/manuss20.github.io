+++
author = "Manuel Sanchez"
title = "Deploy Azure Maps con Terraform"
date = "2021-11-15"
description="El SDK web de Azure Maps permite personalizar mapas interactivos con contenido propio e imágenes. Puede usar este mapa interactivo para las aplicaciones web o móviles. El control de mapa usa WebGL, que permite representar grandes conjuntos de datos con alto rendimiento. Puede desarrollar con el SDK con JavaScript o TypeScript"
tags = [
    "Azure", "Azure Maps", "Maps", "Geospartial", "Terraform"
]
categories = [
    "Azure", "Azure Maps", "Maps", "Geospartial", "Terraform"
]
images  = ["images/posts/AzureMaps.png"]
thumbnail = "images/posts/AzureMaps.png"
comment = false
+++

En este post quiero explicaros como podemos desplegar Azure Maps usando Terraform, revisando esta mañana he visto que ya habian liberado el modulo de **[Azure Maps para terraform](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/maps_account)**

Y estoy seguro de que una vez que usted también lee a través de él, usted aprenderá que usted tiene que tomar varios pasos con el fin de lograr la configuración de Azure Maps.
Voy a intentar ahorrarte algo de tiempo, proporcionándote una configuración básica de terraform que te ayudará a ponerte en marcha en un abrir y cerrar de ojos.

> El SDK web de Azure Maps permite personalizar mapas interactivos con contenido propio e imágenes. Puede usar este mapa interactivo para las aplicaciones web o móviles. El control de mapa usa WebGL, que permite representar grandes conjuntos de datos con alto rendimiento. Puede desarrollar con el SDK con JavaScript o TypeScript.

### 1. Crear el fichero providers.tf con el siguiente contenido

~~~
    terraform {
    required_providers {
        azurerm = {
        source  = "hashicorp/azurerm"
        version = "~> 2.65"
        }
        azuread = {
        source  = "hashicorp/azuread"
        version = "2.0.1"
        }
    }
    }

    provider "azurerm" {
    features {}
    }

    provider "azuread" {}
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

### 3. Crear el fichero maps.tf con el siguiente contenido

~~~
{
    resource "azurerm_maps_account" "map" {
        name                = var.maps_name
        resource_group_name = azurerm_resource_group.rg.name
        sku_name            = var.maps_sku
        tags                = var.tags
      }
}
~~~

### 4. Crear el fichero variable.tf con el siguiente contenido

~~~
  variable "location" {
    description = "(Required) Location of the all services to be created"
    default="westeurope"
  }
  
  variable "resource_group_name" {
    description = "(Required) Resource group name of the all services to be created"
    default= "RGexample"
  }
  
  variable "tags" {
    description = "(Required) Tags to be applied to the all services to be created"
    default = { Project = "TF_example" }
  }
  
  # Azure Maps
  variable "maps_name"{
    description = "(Required) Name of Azure Maps instance"
    default = "mapsexamplemanu"
  }
  
  variable "maps_sku"{
    description = "(Required) SKU of Azure Maps instance"
    default = "S1"
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
Espero que le sirva de ayuda. Encuentre el código completo [aquí](https://github.com/Manuss20/azure.samples/tree/master/Azure_Maps)

Saludos!