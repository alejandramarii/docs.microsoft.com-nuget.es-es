---
title: Impacto de project.json para los autores de paquetes de NuGet | Microsoft Docs
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 1/9/2017
ms.topic: article
ms.prod: nuget
ms.technology: 
ms.assetid: 983485df-9375-4827-b58b-70065320ee37
description: "Información detallada sobre cómo afecta la implementación de project.json en NuGet 3.x a los autores de paquetes, como las características, el contenido y el formato de paquetes no admitidos."
keywords: "NuGet y project.json, impacto de project.json, consideraciones sobre la creación de paquetes, características de project.json"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 93a4e9f9cb57c8acbe516a957e01b801bac0e116
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2017
---
# <a name="impact-of-projectjson-when-creating-packages"></a><span data-ttu-id="b2bde-104">Impacto de project.json al crear paquetes</span><span class="sxs-lookup"><span data-stu-id="b2bde-104">Impact of project.json when creating packages</span></span>

<span data-ttu-id="b2bde-105">El sistema `project.json` que se usa en NuGet 3+ afecta a los autores de paquetes de varias maneras, como se describe en las secciones siguientes.</span><span class="sxs-lookup"><span data-stu-id="b2bde-105">The `project.json` system used in NuGet 3+ affects package authors in several ways as described in the following sections.</span></span>

## <a name="changes-affecting-existing-packages-usage"></a><span data-ttu-id="b2bde-106">Cambios que afectan al uso de paquetes existentes</span><span class="sxs-lookup"><span data-stu-id="b2bde-106">Changes affecting existing packages usage</span></span>

<span data-ttu-id="b2bde-107">Los paquetes tradicionales de NuGet admiten una serie de características que no se transmiten al mundo transitivo.</span><span class="sxs-lookup"><span data-stu-id="b2bde-107">Traditional NuGet packages support a set of features that are not carried over to the transitive world.</span></span>

### <a name="install-and-uninstall-scripts-are-ignored"></a><span data-ttu-id="b2bde-108">Los scripts de instalación y desinstalación se omiten</span><span class="sxs-lookup"><span data-stu-id="b2bde-108">Install and uninstall scripts are ignored</span></span>

<span data-ttu-id="b2bde-109">El modelo de restauración transitiva, descrito en [Dependency resolution](../consume-packages/dependency-resolution.md#dependency-resolution-with-packagereference-and-projectjson) (Resolución de dependencias), no tiene un concepto de "período de instalación de paquetes".</span><span class="sxs-lookup"><span data-stu-id="b2bde-109">The transitive restore model, described in [Dependency resolution](../consume-packages/dependency-resolution.md#dependency-resolution-with-packagereference-and-projectjson), does not have a concept of "package install time".</span></span> <span data-ttu-id="b2bde-110">Un paquete está presente o no, pero no hay ningún proceso coherente que tenga lugar cuando se instala un paquete.</span><span class="sxs-lookup"><span data-stu-id="b2bde-110">A package is either present or not present, but there is no consistent process that occurs when a package is installed.</span></span>

<span data-ttu-id="b2bde-111">Además, los scripts de instalación solo se admitían en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b2bde-111">Also, install scripts were supported only in Visual Studio.</span></span> <span data-ttu-id="b2bde-112">Otros IDE tenían que simular la API de extensibilidad de Visual Studio para intentar admitir estos scripts, y no había compatibilidad disponible en los editores y herramientas de línea de comandos comunes.</span><span class="sxs-lookup"><span data-stu-id="b2bde-112">Other IDEs had to mock the Visual Studio extensibility API to attempt to support such scripts, and no support was available in common editors and command-line tools.</span></span>

### <a name="content-transforms-are-not-supported"></a><span data-ttu-id="b2bde-113">No se admiten las transformaciones de contenido.</span><span class="sxs-lookup"><span data-stu-id="b2bde-113">Content transforms are not supported.</span></span>

<span data-ttu-id="b2bde-114">Igual que los scripts de instalación, las transformaciones se ejecutan durante la instalación de los paquetes y no suelen ser idempotentes.</span><span class="sxs-lookup"><span data-stu-id="b2bde-114">Similar to install scripts, transforms run on package install and are typically not idempotent.</span></span> <span data-ttu-id="b2bde-115">Como ya no hay ningún tiempo de instalación, la característica XDT Transform y características similares no se admiten y se omiten si se usa este tipo de paquete en un escenario transitivo.</span><span class="sxs-lookup"><span data-stu-id="b2bde-115">Since there is no install time anymore, XDT Transform and similar features are not supported, and are ignored if such a package is used in a transitive scenario.</span></span>


### <a name="content"></a><span data-ttu-id="b2bde-116">Contenido</span><span class="sxs-lookup"><span data-stu-id="b2bde-116">Content</span></span>

<span data-ttu-id="b2bde-117">Los paquetes de NuGet tradicionales envían archivos de contenido, como archivos de código fuente y archivos de configuración.</span><span class="sxs-lookup"><span data-stu-id="b2bde-117">Traditional NuGet packages are shipping content files such as source code and configuration files.</span></span> <span data-ttu-id="b2bde-118">Se usan normalmente en dos escenarios:</span><span class="sxs-lookup"><span data-stu-id="b2bde-118">There are used typically in two scenarios:</span></span>

1. <span data-ttu-id="b2bde-119">Archivos iniciales colocados en el proyecto para que el usuario pueda editarlos más tarde.</span><span class="sxs-lookup"><span data-stu-id="b2bde-119">Initial files dropped into the project so the user can edit them at a later time.</span></span> <span data-ttu-id="b2bde-120">El ejemplo común son los archivos de configuración predeterminados.</span><span class="sxs-lookup"><span data-stu-id="b2bde-120">The common example is default configuration files.</span></span>

2. <span data-ttu-id="b2bde-121">Archivos de contenido usados como complementos de los ensamblados instalados en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="b2bde-121">Content files used as companions to the assemblies installed in the project.</span></span> <span data-ttu-id="b2bde-122">Este ejemplo sería una imagen de logotipo usada por un ensamblado.</span><span class="sxs-lookup"><span data-stu-id="b2bde-122">The example here would be a logo image used by an assembly.</span></span>

<span data-ttu-id="b2bde-123">La compatibilidad con el contenido está deshabilitada actualmente por motivos parecidos para los scripts y las transformaciones, pero estamos preparando el diseño para ofrecer compatibilidad con el contenido.</span><span class="sxs-lookup"><span data-stu-id="b2bde-123">Support for content is currently disabled for similar reasons for scripts and transforms, but we are in the process of designing support for content.</span></span>

<span data-ttu-id="b2bde-124">Los archivos de contenido todavía se pueden colocar dentro de los paquetes, y actualmente se omiten, pero el usuario final todavía puede copiarlos en el sitio adecuado.</span><span class="sxs-lookup"><span data-stu-id="b2bde-124">Content files can still be carried inside the packages, and are ignored currently, however the end user can still copy them into the right spot.</span></span>

<span data-ttu-id="b2bde-125">Puede ver una de las propuestas para devolver archivos de contenido y seguir su progreso aquí: [https://github.com/NuGet/Home/issues/627](https://github.com/NuGet/Home/issues/627).</span><span class="sxs-lookup"><span data-stu-id="b2bde-125">You can see one of the proposals for bringing back content files, and follow its progress, here: [https://github.com/NuGet/Home/issues/627](https://github.com/NuGet/Home/issues/627).</span></span>

## <a name="impact-for-package-authors"></a><span data-ttu-id="b2bde-126">Impacto para los autores de paquetes</span><span class="sxs-lookup"><span data-stu-id="b2bde-126">Impact for package authors</span></span>

<span data-ttu-id="b2bde-127">Los paquetes que usan las características anteriores tendrían que usar un mecanismo diferente.</span><span class="sxs-lookup"><span data-stu-id="b2bde-127">Packages using the above features would have to use a different mechanism.</span></span> <span data-ttu-id="b2bde-128">El mecanismo más útil para ello serían los destinos/propiedades de MSBuild, que siguen disponiendo de compatibilidad total.</span><span class="sxs-lookup"><span data-stu-id="b2bde-128">The most commonly useful mechanism for this would be the MSBuild targets/props that continues to get fully supported.</span></span> <span data-ttu-id="b2bde-129">El sistema de compilación puede optar por seleccionar otras convenciones en el paquete.</span><span class="sxs-lookup"><span data-stu-id="b2bde-129">The build system can choose to pick up other conventions in the package.</span></span> <span data-ttu-id="b2bde-130">Es de esta forma cómo se ofrece compatibilidad para los destinos de MSBuild, así como para los analizadores de Roslyn.</span><span class="sxs-lookup"><span data-stu-id="b2bde-130">This is how MSBuild targets are supported as well as Roslyn analyzers.</span></span> <span data-ttu-id="b2bde-131">Es posible compilar paquetes que admitan los destinos y los analizadores de los escenarios `packages.config` y `project.json`.</span><span class="sxs-lookup"><span data-stu-id="b2bde-131">It is possible to build packages that supports targets and analyzers for `packages.config` and `project.json` scenarios.</span></span>

<span data-ttu-id="b2bde-132">Los paquetes que intentan modificar el proyecto para facilitar el inicio suelen funcionar en un número muy restringido de escenarios y deberían proporcionar un archivo Léame o instrucciones sobre cómo usar el paquete.</span><span class="sxs-lookup"><span data-stu-id="b2bde-132">Packages that attempt to modify the project to ease startup typically work in a very limited set of scenarios, and should instead provide a readme, or guidance on how to use the package.</span></span>

<span data-ttu-id="b2bde-133">La mayoría de los paquetes existentes no deberían necesitar usar el formato de paquete que se describe a continuación.</span><span class="sxs-lookup"><span data-stu-id="b2bde-133">Most existing packages should not need to use the package format described below.</span></span>

<span data-ttu-id="b2bde-134">El formato permite que el contenido nativo se trate como un escenario de primera clase.</span><span class="sxs-lookup"><span data-stu-id="b2bde-134">The format enables native content as a first class scenario.</span></span> <span data-ttu-id="b2bde-135">Esto significa que los ensamblados administrados que dependen de implementaciones próximas al hardware distribuyen implementaciones binarias junto con los ensamblados administrados en función de la plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="b2bde-135">This means that managed assemblies depending on close to hardware implementations to ship binary implementations alongside the managed assemblies based on the target platform.</span></span> <span data-ttu-id="b2bde-136">Por ejemplo, el paquete System.IO.Compression emplea esta tecnología.</span><span class="sxs-lookup"><span data-stu-id="b2bde-136">For example System.IO.Compression package is utilizing this technology.</span></span> [<span data-ttu-id="b2bde-137">https://www.nuget.org/packages/System.IO.Compression</span><span class="sxs-lookup"><span data-stu-id="b2bde-137">https://www.nuget.org/packages/System.IO.Compression</span></span>](https://www.nuget.org/packages/System.IO.Compression)

<span data-ttu-id="b2bde-138">En resumen, si la funcionalidad anterior no es estrictamente necesaria, le recomendamos que se quede con el formato de paquete existente, ya que el formato descrito aquí solo es compatible con NuGet 3.x+.</span><span class="sxs-lookup"><span data-stu-id="b2bde-138">In summary if the functionality above is not absolutely necessary, we recommend sticking with the existing package format, as the format described here is supported only by NuGet 3.x+.</span></span>

<span data-ttu-id="b2bde-139">Se podrían crear paquetes que funcionaran para los escenarios `packages.config` y `project.json` a través de las correcciones de compatibilidad (shim), pero a veces resulta más sencillo estructurar los paquetes de la forma tradicional, sin las características en desuso mencionadas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="b2bde-139">It would be possible to build packages to work for both `packages.config` and `project.json` scenarios through shimming, however it is often simpler to just structure the packages the traditional way, without the deprecated features mentioned above.</span></span>


## <a name="3x-package-format"></a><span data-ttu-id="b2bde-140">Formato de paquete 3.x</span><span class="sxs-lookup"><span data-stu-id="b2bde-140">3.x package format</span></span>  ##

<span data-ttu-id="b2bde-141">El formato de paquete 3.x admite varias características adicionales más allá de NuGet 2.x:</span><span class="sxs-lookup"><span data-stu-id="b2bde-141">The 3.x package format allows for several additional features beyond NuGet 2.x:</span></span>

1. <span data-ttu-id="b2bde-142">Define un ensamblado de referencia que se usa para la compilación y un conjunto de ensamblados de implementación que se usan en tiempo de ejecución en distintas plataformas y dispositivos.</span><span class="sxs-lookup"><span data-stu-id="b2bde-142">Defining a reference assembly used for compilation and a set of implementation assemblies used for runtime on different platforms/devices.</span></span> <span data-ttu-id="b2bde-143">Esto le permite aprovechar las ventajas de las API específicas de las plataformas y ofrecer un área expuesta común para los consumidores.</span><span class="sxs-lookup"><span data-stu-id="b2bde-143">Which allows you to take advantage of platform specific APIs while providing a common surface area for your consumers.</span></span> <span data-ttu-id="b2bde-144">En concreto, facilita la escritura de bibliotecas portátiles intermedias.</span><span class="sxs-lookup"><span data-stu-id="b2bde-144">Specifically this makes writing intermediate portable libraries easier.</span></span>

2. <span data-ttu-id="b2bde-145">Permite que los paquetes se dinamicen en las plataformas (por ejemplo, en los sistemas operativos o en la arquitectura de CPU).</span><span class="sxs-lookup"><span data-stu-id="b2bde-145">Allows packages to pivot on platforms e.g. operating systems or CPU architecture.</span></span>

3. <span data-ttu-id="b2bde-146">Permite la separación de implementaciones específicas de plataforma en paquetes complementarios.</span><span class="sxs-lookup"><span data-stu-id="b2bde-146">Allows for separation of platform specific implementations to companion packages.</span></span>

4. <span data-ttu-id="b2bde-147">Admite las dependencias nativas como un ciudadano de primera clase.</span><span class="sxs-lookup"><span data-stu-id="b2bde-147">Support Native dependencies as a first class citizen.</span></span>