+++
author = "Manuel Sanchez"
title = "Deploy Azure Storage Account con Terraform JSON"
date = "2021-06-06"
description=""
tags = [
    "Azure", "Azure-Storage-Account", "sta", "Terraform"
]
categories = [
    "Azure", "Azure-Storage-Account", "sta", "Terraform"
]
images  = ["images/posts/Terraform.png"]
thumbnail = "images/posts/Terraform.png"
comment = false
+++

En este post quiero explicaros como podemos desplegar Infraestructura como código a través de Terraform, pero en vez de usar la sintaxis nativa usaremos la alternativa que es compatible con JSON.

### *¿Esto como sucede?*

Terraform también soporta una sintaxis alternativa que es compatible con JSON. Esta sintaxis es útil cuando se generan partes de una configuración mediante programación, ya que se pueden utilizar las bibliotecas JSON existentes para preparar los archivos de configuración generados.
La sintaxis JSON se define en términos de la sintaxis nativa. Todo lo que se puede expresar en sintaxis nativa también se puede expresar en sintaxis JSON, pero algunas construcciones son más complejas de representar en JSON debido a las limitaciones de la gramática JSON.
Terraform espera la sintaxis nativa para los archivos nombrados con un sufijo .tf, y la sintaxis JSON para los archivos nombrados con un sufijo .tf.json.

### *¿Qué son los Azure Storage Accounts?*

Azure Storage Account contiene todos los objetos de datos de Azure Storage, incluidos blobs, recursos compartidos de archivos, colas, tablas y discos. La cuenta de almacenamiento (Storage Accounts) proporciona un espacio de nombres único para los datos de Azure Storage que es accesible desde cualquier lugar del mundo mediante HTTP o HTTPS. Los datos de la cuenta de almacenamiento son duraderos y altamente disponibles, seguros y escalables a gran escala.
Una vez que tenemos esto, vamos a desplegar un Storage Account a través de Terraform usando la sintaxis alternativa:

main.tf.json

~~~
{
	"data": {
		"azurerm_subscription": {
			"current": {}
		},
		"azurerm_client_config": {
			"current": {}
		},
		"azuread_domains": {
			"aad_domains": {
				"only_default": "true"
			}
		}
	},
	"resource": {
		"azurerm_resource_group": {
			"rg": {
				"name": "${var.resource_group_name}",
				"location": "${var.location}",
				"tags": "${var.tags}"
			}
		}
	}
}
~~~

providers.tf.json

~~~
{
	"data": {
		"azurerm_subscription": {
			"current": {}
		},
		"azurerm_client_config": {
			"current": {}
		},
		"azuread_domains": {
			"aad_domains": {
				"only_default": "true"
			}
		}
	},
	"resource": {
		"azurerm_resource_group": {
			"rg": {
				"name": "${var.resource_group_name}",
				"location": "${var.location}",
				"tags": "${var.tags}"
			}
		}
	}
}
~~~

sta.tf.json

~~~
{
    "resource": {
        "azurerm_storage_account": {
            "sta": {
                "name": "${var.name-sta}",
                "resource_group_name": "${azurerm_resource_group.rg.name}",
                "location": "${var.location}",
                "account_tier": "${var.sku-sta}",
                "account_replication_type": "${var.replication-type-sta}",
                "enable_https_traffic_only": "${var.http-traffic-only-sta}",
                "tags": "${var.tags}"
            }
        },
        "azurerm_storage_container": {
            "sta_container": {
                "name": "${var.name-sta-container}",
                "storage_account_name": "${azurerm_storage_account.sta.name}",
                "container_access_type": "${var.access-type-sta-container}"
            }
        }
    }
}
~~~

variable.tf

~~~
#Commons
variable "location" {
  description = "(Required) Location of the all services to be created"
  default="westeurope"
}

variable "resource_group_name" {
  description = "(Required) Resource group name of the all services to be created"
  default= "TestTF"
}

variable "tags" {
  description = "(Required) Tags to be applied to the all services to be created"
  default = { Project = "jumpstart_azure_tf" }
}

# Storage Account
variable "name-sta" {
  description = "(Required) Name of Storage Account"
  default="statestingaz"
}

variable "sku-sta" {
  description = "(Required) Sku Storage Account"
  default="Standard"
}

variable "replication-type-sta" {
  description = "(Required) Replication type on Storage Account"
  default="LRS"
}

variable "http-traffic-only-sta" {
  description = "(Required) http-traffic-only-sta Storage Account"
  default=true
}

variable "name-sta-container" {
  description = "(Required) Name of Storage Account Container"
  default="tfstate"
}

variable "access-type-sta-container" {
  description = "(Required) Access Type of Storage Account Container"
  default="private"
}
~~~

De esta forma tendremos nuestro proyecto completamente automatizado.

Saludos!
