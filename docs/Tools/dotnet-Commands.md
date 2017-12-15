---
title: comandos de NuGet dotNet | Documentos de Microsoft
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 12/08/2017
ms.topic: article
ms.prod: nuget
ms.technology: 
ms.assetid: 0c81dbc4-2c14-4ec8-b87a-b802a899c3ea
description: "Una referencia breve para los comandos relacionados con NuGet mediante la interfaz de línea de comandos de dotnet."
keywords: "comandos de NuGet dotnet, dotnet pack, restauración dotnet, variables locales de nuget dotnet, dotnet nuget inserción, dotnet nuget delete"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 7ff4779f46db102f1384650d82118b34fedd4413
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2017
---
# <a name="dotnet-commands"></a>comandos de dotNet.

La interfaz de línea de comandos DotNet, que se ejecuta en Windows, Mac OS X y Linux, proporciona una serie de comandos de nuget.exe esenciales como se muestra a continuación. Donde dotnet proporciona los comandos que desee, no es necesario descargar nuget.exe.

- [**módulo de dotnet**](https://docs.microsoft.com/dotnet/core/tools/dotnet-pack?tabs=netcore2x): los módulos de código para NETCore SDK proyectos en un paquete de NuGet. Deben usar todos los demás tipos de proyecto[`nuget pack`](cli-ref-pack.md)
- [**restauración de dotnet**](https://docs.microsoft.com/dotnet/core/tools/dotnet-restore?tabs=netcore2x): restaura las dependencias y las herramientas de generación de un proyecto. A partir de NuGet 4.0, se ejecuta el mismo código que `nuget restore`.
- [**variables locales de nuget dotnet**](https://docs.microsoft.com/dotnet/core/tools/dotnet-nuget-locals): borra o listas de recursos locales de NuGet como http-solicitud de caché, caché temporal o carpeta paquetes global de todo el equipo.
- [**inserción de nuget dotnet**](https://docs.microsoft.com/dotnet/core/tools/dotnet-nuget-push): inserta un paquete en un servidor y lo publica, aplicable a nuget.org, Visual Studio Team Services o los servidores de NuGet de terceros.
- [**eliminar dotnet nuget**](https://docs.microsoft.com/dotnet/core/tools/dotnet-nuget-delete): elimina o unlists un paquete desde un servidor, que es aplicable a nuget.org, Visual Studio Team Services o los servidores de NuGet de terceros.