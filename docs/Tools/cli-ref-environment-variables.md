---
title: Las variables de entorno de NuGet CLI | Documentos de Microsoft
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 10/24/2017
ms.topic: reference
ms.prod: nuget
ms.technology: 
ms.assetid: 1f5c31ca-fa0a-4798-a906-110f2c73d00b
description: Referencia para las variables de entorno nuget.exe
keywords: variables de entorno de NuGet
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 0a1dc2a928da657b0d222c2adc02fbd850b66704
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2017
---
# <a name="nuget-cli-environment-variables"></a>Variables de entorno de NuGet CLI

El comportamiento de la CLI nuget.exe puede configurarse a través de una serie de variables de entorno, que afectan a nuget.exe en todo el equipo, usuario o proceso niveles.

En general, las opciones especificadas directamente en la línea de comandos o en archivos de configuración de NuGet tienen prioridad, pero hay unas pocas excepciones, como *FORCE_NUGET_EXE_INTERACTIVE*. Si encuentra que nuget.exe tiene un comportamiento diferente entre equipos diferentes, una variable de entorno podría ser la causa. Por ejemplo, Kudu de aplicaciones Web de Azure (se usa durante la implementación) tiene *NUGET_XMLDOC_MODE* establecido en *omitir* para acelerar el rendimiento de la restauración de paquete y ahorrar espacio en disco.

| Variable | Descripción | Comentarios |
| --- | --- | --- |
| http_proxy | Proxy de HTTP que se utiliza para operaciones HTTP de NuGet. | Esto se especificarían como `http://<username>:<password>@proxy.com`. |
| no_proxy | Configura los dominios se omitirá del uso de proxy. | Especificar como dominios separados por coma (,). |
| EnableNuGetPackageRestore | Marca si NuGet implícitamente debe conceder consentimiento si es necesaria por el paquete en la restauración. | Se especifica la marca especificada | como *true* o *1*, cualquier otro valor que se tratan como marca no establecido. |
| NUGET_EXE_NO_PROMPT | Impide que el archivo ejecutable para solicitar las credenciales.| Cualquier valor excepto una cadena nula o vacía se tratará como esta marca conjunto/true. |
FORCE_NUGET_EXE_INTERACTIVE | Variable de entorno global para forzar el modo interactivo. | Cualquier valor excepto una cadena nula o vacía se tratará como esta marca conjunto/true. |
| NUGET_PACKAGES | Ruta de acceso donde se almacenan / en caché paquetes. | Especificar como ruta de acceso absoluta. |
| NUGET_FALLBACK_PACKAGES | Carpetas de paquetes de reserva global. | Rutas de acceso de carpeta absoluto separados por punto y coma (;). |
| NUGET_HTTP_CACHE_PATH | Carpeta de caché HTTP. | Especificar como ruta de acceso absoluta. |
| NUGET_PERSIST_DG | Marca que indica si se deben almacenar los archivos de grupo de distribución (los datos recopilados de MSBuild). | Especificado como *true* o *false* (valor predeterminado), si no establece NUGET_PERSIST_DG_PATH se almacenará en el directorio temporal (carpeta de NuGetScratch en el directorio temporal de entorno actual). |
| NUGET_PERSIST_DG_PATH | Ruta de acceso para conservar los archivos de grupo de distribución. | Especificado como ruta de acceso absoluta, esta opción es utiliza únicamente cuando *NUGET_PERSIST_DG* está establecido en true. |
| NUGET_RESTORE_MSBUILD_ARGS | Establece los argumentos de MSBuild adicionales. |
| NUGET_RESTORE_MSBUILD_| Nivel de detalle |Establece el nivel de detalle del registro de MSBuild. | Valor predeterminado es *silencioso* ("/ v: q"). Los valores posibles *q [uiet]*, *m [inimal]*, *n [ormal]*, *d. [detallado]*, y *diag [nostic]*. |
| NUGET_SHOW_STACK | Determina si la excepción completa (incluido el seguimiento de la pila) se debe mostrar al usuario. | Especificado como *true* o *false* (valor predeterminado). |
| NUGET_XMLDOC_MODE | Determina cómo debe controlarse la extracción de archivos de documentación de XML de ensamblados. | Los modos compatibles son *omitir* (no extraiga los archivos de documentación XML), *comprimir* (almacenar archivos de documento XML como un archivo zip) o *ninguno* (valor predeterminado, tratar los archivos de documento XML como normal archivos). |