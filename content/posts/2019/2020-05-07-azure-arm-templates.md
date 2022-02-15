+++
author = "Manuel Sanchez"
title = "Azure ARM Templates"
date = "2019-05-07"
description="Las plantillas de Azure ARM (Azure Resource Manager) permite aprovisionar las aplicaciones usando una plantilla declarativa. En una sola plantilla, se pueden implementar varios servicios junto con sus dependencias. Se usa la misma plantilla para implementar repetidamente la aplicación durante cada etapa de su ciclo de vida."
tags = [
    "Azure", "Azure ARM", "DevOps", "Deploy", "Templates", "Cloud"
]
categories = [
    "Azure", "Azure ARM", "DevOps", "Deploy", "Templates", "Cloud"
]
images  = ["images/posts/Azure-ARM.jpg"]
thumbnail  = "images/posts/Azure-ARM.jpg"
comment = false
+++

Las plantillas de Azure ARM (Azure Resource Manager) permite aprovisionar las aplicaciones usando una plantilla declarativa. En una sola plantilla, se pueden implementar varios servicios junto con sus dependencias. Se usa la misma plantilla para implementar repetidamente la aplicación durante cada etapa de su ciclo de vida.

Esto nos ayudará a poder desplegar todos los componentes de nuestra solución, de una única vez, en un grupo de recursos concreto. De esta forma simplificamos la administración de éstos entre los diferentes entornos. Por ejemplo: desarrollo, preproducción y producción.

Vamos a crear un ejemplo sencillo de ARM siguiendo estos pasos:

Abrimos Visual Studio y seleccionamos un proyecto del tipo «Azure Resource Group»:

![Creación del proyecto ARM en Visual Studio](images/posts/ARM1.jpg)

Cuando estamos creando nuestro proyecto nos solicitara elegir un tipo de plantilla, para este caso concreto seleccionaremos la plantilla del tipo “Web App”:

![Selección del tipo de plantilla Web App](images/posts/ARM2.jpg)

Una vez seleccionado el tipo de plantilla nos creará nuestra solución que tendrá el siguiente aspecto:

![Solución en Visual Studio](images/posts/ARM3.jpg)

El esquema que aparece en la foto anterior se puede apreciar 3 ficheros importantes:

- **Deploy-AzureResourceGroup.ps1: Script de despliegue.**
- **WebSite.json: Fichero donde se encuentran definido los componentes a desplegar.**
- **WebSite.parameters.json: Fichero que contiene los parámetros de configuración.**

Dentro del fichero WebSite.json podemos observar el esquema de la plantilla que hemos creado. Por defecto incluye un montón de paramentos adicionales, aunque podemos simplificarlo con los siguientes elementos esenciales:

~~~
{
  "$schema": "https://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#",
  "contentVersion": "1.0.0.0",
  "parameters": { },
  "variables": { },
  "resources": { },
  "outputs": { },  
}
~~~

- **$Schema**: Contiene el esquema JSON que se usará para la plantilla ARM.
- **contentVersion**: Especifica la versión de la plantilla que estás usando. Por defecto se asignará automáticamente el - valor inicial de 1.0.0.0
- **Parameters**: Son los parámetros que se pasan a la ejecución de la plantilla.
- **Variables**:  Variables para poder reutilizarlas a lo largo de la plantilla.
- **Resources**: Epecifica los componentes que se van a desplegar.
- **Outputs**: Es la salida de resultados de la plantilla.

Una vez tengamos la plantilla finalizada, procederemos a realizar el despliegue. Éste se puede realizar desde Visual Studio o desde PowerShell (en nuestro caso lo haremos desde Visual Studio):

Desde la solución hacemos click derecho sobre el proyecto -> Deploy -> new (tal y como vemos en la siguiente imagen):

![Menu contextual desde la solución para realizar el Deploy ](images/posts/ARM4.jpg)

Nos solicitará algunos parámetros indicando nuestra suscripción de Azure, y nos preguntará si queremos crear un nuevo grupo de recursos o crearlo en uno ya existente:

![Formulario con los datos necesarios para el deploy](images/posts/ARM5.jpg)

Nos indicará si falta algún dato obligatorio para la ejecución:

![Edición de los parámetros](images/posts/ARM6.jpg)

Una vez lanzado el deploy, podremos ver el output de resultados para asegurarnos que todo ha ido correctamente:

![Ejecución en la consola y output con los resultados](images/posts/ARM7.jpg)

Una vez nos diga que está completado, podremos ir a nuestra suscripción de Azure, para comprobar que se han creado los recursos correctamente:

![Portal de Azure](images/posts/ARM8.jpg)

##### **Conclusiones:**

- Permite desplegar, gestionar y controlar todos los recursos para su solución como un solo grupo, en lugar de - manejar estos recursos de manera individual.
- Reutilizar esa implementación varias veces a lo largo de todo el ciclo de vida del desarrollo, y tener la - confianza de que sus recursos se despliegan correctamente.
- Podemos definir las dependencias entre los recursos para que se desplieguen en el orden correcto.
- Nos permite poder aplicar etiquetas a los recursos para organizarlos lógicamente en la suscripción.
- Nos ayuda a gestionar nuestra infraestructura a través de plantillas declarativas en lugar de scripts.
- Unificar la visualización de la facturación de tu organización mediante la visualización de los gastos para un - grupo de recursos que comparten la misma etiqueta.

Saludos!