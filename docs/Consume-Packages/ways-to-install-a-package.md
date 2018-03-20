---
title: Formas de instalar paquetes NuGet | Microsoft Docs
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 02/12/2018
ms.topic: get-started-article
ms.prod: nuget
ms.technology: 
description: "Describe el proceso de instalación de paquetes de NuGet en un proyecto, que incluye lo que sucede en el disco y a los correspondientes archivos de proyecto."
keywords: instalar NuGet, consumo de paquetes NuGet, instalar paquetes NuGet, referencias de paquetes NuGet
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 3bae03e148a366388c10d08e83c89dac6ff56d06
ms.sourcegitcommit: 33436d122873249dbb20616556cd8c6783f38909
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2018
---
# <a name="different-ways-to-install-a-nuget-package"></a><span data-ttu-id="49a19-104">Distintas formas de instalar un paquete NuGet</span><span class="sxs-lookup"><span data-stu-id="49a19-104">Different ways to install a NuGet Package</span></span>

<span data-ttu-id="49a19-105">Los paquetes NuGet se descargan e instalan con cualquiera de los métodos siguientes (vea [Instalación de las herramientas del cliente NuGet](../install-nuget-client-tools.md) si todavía no se han instalado):</span><span class="sxs-lookup"><span data-stu-id="49a19-105">NuGet packages are downloaded and installed using any of the following methods (see [Install NuGet client tools](../install-nuget-client-tools.md) if you don't have these installed already):</span></span>

| <span data-ttu-id="49a19-106">Método</span><span class="sxs-lookup"><span data-stu-id="49a19-106">Method</span></span> | <span data-ttu-id="49a19-107">Description</span><span class="sxs-lookup"><span data-stu-id="49a19-107">Description</span></span> |
| --- | --- |
| <span data-ttu-id="49a19-108">CLI de dotnet.exe</span><span class="sxs-lookup"><span data-stu-id="49a19-108">dotnet.exe CLI</span></span><br/>`dotnet install <package_name>` | <span data-ttu-id="49a19-109">(Todas las plataformas) Descarga el paquete identificado con \<package_name\>, expande su contenido en una carpeta del directorio actual y agrega una referencia al archivo de proyecto.</span><span class="sxs-lookup"><span data-stu-id="49a19-109">(All platforms) Downloads the package identified by \<package_name\>, expands its contents into a folder in the current directory, and adds a reference to the project file.</span></span> <span data-ttu-id="49a19-110">También descarga e instala las dependencias.</span><span class="sxs-lookup"><span data-stu-id="49a19-110">Also downloads and installs dependencies.</span></span><ul><li>[<span data-ttu-id="49a19-111">Instalar y usar un paquete (CLI de dotnet)</span><span class="sxs-lookup"><span data-stu-id="49a19-111">Install and use a package (dotnet CLI)</span></span>](../quickstart/install-and-use-a-package-using-the-dotnet-cli.md)</li><li>[<span data-ttu-id="49a19-112">Comandos dotnet</span><span class="sxs-lookup"><span data-stu-id="49a19-112">dotnet commands</span></span>](../tools/dotnet-commands.md)</li></ul> |
| <span data-ttu-id="49a19-113">Interfaz de usuario del Administrador de paquetes (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="49a19-113">Package Manager UI (Visual Studio)</span></span> | <span data-ttu-id="49a19-114">(Windows and Mac) Ofrece una interfaz de usuario a través de la cual puede examinar, seleccionar e instalar paquetes con sus dependencias en un proyecto.</span><span class="sxs-lookup"><span data-stu-id="49a19-114">(Windows and Mac) Provides a UI through which you can browse, select, and install packages and their dependencies into a project.</span></span> <span data-ttu-id="49a19-115">Agrega las referencias a paquetes instalados en el archivo de proyecto.</span><span class="sxs-lookup"><span data-stu-id="49a19-115">Adds references to installed packages to the project file.</span></span><ul><li>[<span data-ttu-id="49a19-116">Instalar y usar un paquete (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="49a19-116">Install and use a package (Visual Studio)</span></span>](../quickstart/install-and-use-a-package-in-visual-studio.md)</li><li>[<span data-ttu-id="49a19-117">Referencia de la interfaz de usuario del Administrador de paquetes</span><span class="sxs-lookup"><span data-stu-id="49a19-117">Package Manager UI reference (Windows)</span></span>](../tools/package-manager-ui.md)</li><li>[<span data-ttu-id="49a19-118">Incluir un paquete NuGet en el proyecto (Mac)</span><span class="sxs-lookup"><span data-stu-id="49a19-118">Including a NuGet package in your project (Mac)</span></span>](/visualstudio/mac/nuget-walkthrough)</li></ul> |
| <span data-ttu-id="49a19-119">Consola del Administrador de paquetes (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="49a19-119">Package Manager Console (Visual Studio)</span></span><br/>`Install-Package <package_name>` | <span data-ttu-id="49a19-120">(Solo Windows) Descarga e instala el paquete identificado por \<package_name\> en un proyecto especificado de la solución y luego agrega una referencia al archivo de proyecto.</span><span class="sxs-lookup"><span data-stu-id="49a19-120">(Windows only) Downloads and installs the package identified by \<package_name\> into a specified project in the solution, then adds a reference to the project file.</span></span> <span data-ttu-id="49a19-121">También descarga e instala las dependencias.</span><span class="sxs-lookup"><span data-stu-id="49a19-121">Also downloads and installs dependencies.</span></span><ul><li>[<span data-ttu-id="49a19-122">Instalar y usar un paquete (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="49a19-122">Install and use a package (Visual Studio)</span></span>](../quickstart/install-and-use-a-package-in-visual-studio.md)</li><li>[<span data-ttu-id="49a19-123">Guía de la consola del Administrador de paquetes</span><span class="sxs-lookup"><span data-stu-id="49a19-123">Package Manager Console guide</span></span>](../tools/package-manager-console.md)</li></ul> |
| <span data-ttu-id="49a19-124">CLI de nuget.exe</span><span class="sxs-lookup"><span data-stu-id="49a19-124">nuget.exe CLI</span></span><br/>`nuget install <package_name>` | <span data-ttu-id="49a19-125">(Todas las plataformas) Descarga el paquete identificado con \<package_name\> y expande su contenido en una carpeta del directorio actual; también se pueden descargar todos los paquetes que aparecen en un archivo `packages.config`.</span><span class="sxs-lookup"><span data-stu-id="49a19-125">(All platforms) Downloads the package identified by \<package_name\> and expands its contents into a folder in the current directory; can also download all packages listed in a `packages.config` file.</span></span> <span data-ttu-id="49a19-126">También descarga e instala las dependencias, pero no realiza ningún cambio a los archivos de proyecto.</span><span class="sxs-lookup"><span data-stu-id="49a19-126">Also downloads and installs dependencies, but makes no changes to project files.</span></span><ul><li>[<span data-ttu-id="49a19-127">Comando install</span><span class="sxs-lookup"><span data-stu-id="49a19-127">install command</span></span>](../tools/cli-ref-install.md)</li></ul> |

## <a name="general-install-process"></a><span data-ttu-id="49a19-128">Proceso de instalación general</span><span class="sxs-lookup"><span data-stu-id="49a19-128">General install process</span></span>

<span data-ttu-id="49a19-129">En general, NuGet hace lo siguiente cuando se le pide que instale un paquete:</span><span class="sxs-lookup"><span data-stu-id="49a19-129">In general, NuGet does the following then asked to install a package:</span></span>

1. <span data-ttu-id="49a19-130">Adquirir el paquete:</span><span class="sxs-lookup"><span data-stu-id="49a19-130">Acquire the package:</span></span>
    - <span data-ttu-id="49a19-131">Se comprueba si el paquete solicitado ya existe en una caché (vea [Administrar la memoria caché de NuGet](managing-the-nuget-cache.md)).</span><span class="sxs-lookup"><span data-stu-id="49a19-131">Check if the requested package already exists in a cache (see [Managing the NuGet cache](managing-the-nuget-cache.md)).</span></span>
    - <span data-ttu-id="49a19-132">Si el paquete no está en la caché, se intenta descargar el paquete desde los orígenes incluidos en los [archivos de configuración](Configuring-NuGet-Behavior.md).</span><span class="sxs-lookup"><span data-stu-id="49a19-132">If the package is not in the cache, attempt to download the package from the sources listed in the [configuration files](Configuring-NuGet-Behavior.md).</span></span>
      - <span data-ttu-id="49a19-133">Para los proyectos que usan el formato de referencia `packages.config`, NuGet usa el orden de los orígenes en la configuración.</span><span class="sxs-lookup"><span data-stu-id="49a19-133">For projects using the `packages.config` reference format, NuGet uses the order of the sources in the configuration.</span></span>
      - <span data-ttu-id="49a19-134">Para los proyectos que usan el formato PackageReference, NuGet comprueba primero los orígenes de las carpetas locales, luego los orígenes de los recursos compartidos de red y, finalmente, los orígenes de HTTP (Internet).</span><span class="sxs-lookup"><span data-stu-id="49a19-134">For projects using the PackageReference format, NuGet checks sources that are local folders first, then checks sources on network shares, then checks HTTP (Internet) sources.</span></span>
      - <span data-ttu-id="49a19-135">En general, el orden en el que NuGet comprueba los orígenes no es especialmente significativo, porque cualquier paquete con un número de versión y un identificador específico es exactamente el mismo independientemente del origen en el que se encuentre.</span><span class="sxs-lookup"><span data-stu-id="49a19-135">In general, the order in which NuGet checks sources isn't particularly meaningful, because any given package with a specific identifier and version number is exactly the same on whatever source it's found.</span></span>
    - <span data-ttu-id="49a19-136">Si el paquete se adquiere correctamente de uno de los orígenes, NuGet lo agrega a la caché.</span><span class="sxs-lookup"><span data-stu-id="49a19-136">If the package is successfully acquired from one of the sources, NuGet adds it to the cache.</span></span> <span data-ttu-id="49a19-137">De lo contrario, no se lleva a cabo la instalación.</span><span class="sxs-lookup"><span data-stu-id="49a19-137">Otherwise, installation fails.</span></span>

1. <span data-ttu-id="49a19-138">Expanda el paquete en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="49a19-138">Expand the package into the project.</span></span>
    - <span data-ttu-id="49a19-139">Expandir significa descomprimir el contenido del paquete en la subcarpeta correspondiente.</span><span class="sxs-lookup"><span data-stu-id="49a19-139">Expanding means unzipping the package's contents into an appropriate subfolder.</span></span> <span data-ttu-id="49a19-140">También se coloca una copia del propio `.nupkg` en la subcarpeta.</span><span class="sxs-lookup"><span data-stu-id="49a19-140">A copy of the `.nupkg` itself is also placed in the subfolder.</span></span>
    - <span data-ttu-id="49a19-141">Si el paquete se instala en un proyecto de Visual Studio o de .NET Core, solo se expanden los archivos correspondientes a la plataforma de destino del proyecto.</span><span class="sxs-lookup"><span data-stu-id="49a19-141">If the package is being installed into a Visual Studio or .NET Core project, only the files relevant to the project's target framework are expanded.</span></span> <span data-ttu-id="49a19-142">Cuando se instala con la línea de comandos nuget.exe, se expanden todos los ensamblados.</span><span class="sxs-lookup"><span data-stu-id="49a19-142">When installed using the nuget.exe command line, all assemblies are expanded.</span></span>

1. <span data-ttu-id="49a19-143">Si el paquete se instala en Visual Studio o la CLI de dotnet, se agrega una referencia al archivo de proyecto correspondiente (o a `packages.config` en el caso de algunos tipos de proyecto de Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="49a19-143">If the package is installed within Visual Studio or the dotnet CLI, a reference is added to the appropriate project file (or `packages.config` for some project types in Visual Studio).</span></span>

## <a name="related-topics"></a><span data-ttu-id="49a19-144">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="49a19-144">Related topics</span></span>

- [<span data-ttu-id="49a19-145">Información general y flujo de trabajo del consumo de paquetes</span><span class="sxs-lookup"><span data-stu-id="49a19-145">Overview and workflow of package consumption</span></span>](../consume-packages/overview-and-workflow.md)
- [<span data-ttu-id="49a19-146">Búsqueda y selección de paquetes</span><span class="sxs-lookup"><span data-stu-id="49a19-146">Finding and choosing packages</span></span>](../consume-packages/finding-and-choosing-packages.md)
- [<span data-ttu-id="49a19-147">Configuración del comportamiento de NuGet</span><span class="sxs-lookup"><span data-stu-id="49a19-147">Configuring NuGet behavior</span></span>](../consume-packages/configuring-nuget-behavior.md)
- [<span data-ttu-id="49a19-148">Administrar la memoria caché de NuGet</span><span class="sxs-lookup"><span data-stu-id="49a19-148">Managing the NuGet cache</span></span>](managing-the-nuget-cache.md)