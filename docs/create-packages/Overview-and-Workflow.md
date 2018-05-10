---
title: Información general y flujo de trabajo de la creación de paquetes NuGet
description: Información general del proceso de creación y publicación de un paquete de NuGet, con vínculos a otras partes específicas del proceso.
author: kraigb
ms.author: kraigb
manager: douge
ms.date: 07/26/2017
ms.topic: conceptual
ms.openlocfilehash: a9dd4439f2aa72424187eaa2d9555d5af0e7843d
ms.sourcegitcommit: 3eab9c4dd41ea7ccd2c28bb5ab16f6fbbec13708
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="package-creation-workflow"></a><span data-ttu-id="8e44c-103">Flujo de trabajo de creación de paquetes</span><span class="sxs-lookup"><span data-stu-id="8e44c-103">Package creation workflow</span></span>

<span data-ttu-id="8e44c-104">La creación de un paquete empieza con el código compilado (normalmente los ensamblados .NET) que quiera empaquetar y compartir con otros usuarios, ya sea a través de la galería pública de nuget.org o mediante una galería privada de su organización.</span><span class="sxs-lookup"><span data-stu-id="8e44c-104">Creating a package starts with the compiled code (typically .NET assemblies) that you want to package and share with others, either through the public nuget.org gallery or a private gallery within your organization.</span></span> <span data-ttu-id="8e44c-105">El paquete también puede incluir otros archivos (como un archivo Léame que se muestre en el momento de instalar el paquete), así como transformaciones de determinados archivos de proyecto.</span><span class="sxs-lookup"><span data-stu-id="8e44c-105">The package can also include additional files such as a readme that is displayed when the package is installed, and can include transformations to certain project files.</span></span>

<span data-ttu-id="8e44c-106">Un paquete también puede servir para solo sacar una determinada cifra de dependencias, sin que contenga código propio.</span><span class="sxs-lookup"><span data-stu-id="8e44c-106">A package can also serve to only pull in any number of other dependencies, without containing any code of its own.</span></span> <span data-ttu-id="8e44c-107">Este tipo de paquete es un método cómodo para entregar un SDK que está formado por varios paquetes independientes.</span><span class="sxs-lookup"><span data-stu-id="8e44c-107">Such a package is a convenient way to deliver an SDK that's composed of multiple independent packages.</span></span> <span data-ttu-id="8e44c-108">En otros casos, un paquete puede contener solo archivos de símbolos (`.pdb`) para facilitar la depuración.</span><span class="sxs-lookup"><span data-stu-id="8e44c-108">In other cases, a package may contain only symbol (`.pdb`) files to aid debugging.</span></span>

> [!Note]
> <span data-ttu-id="8e44c-109">Al crear un paquete para que lo usen otros desarrolladores, es importante tener en cuenta que están tomando una dependencia de su trabajo.</span><span class="sxs-lookup"><span data-stu-id="8e44c-109">When you create a package for use by other developers, it's important to understand that they are taking a dependency on your work.</span></span> <span data-ttu-id="8e44c-110">Por definición, crear y publicar un paquete también implican un compromiso para corregir errores y efectuar otras actualizaciones, o por lo menos hacer que el paquete esté disponible como código abierto para que otros usuarios puedan colaborar en su mantenimiento.</span><span class="sxs-lookup"><span data-stu-id="8e44c-110">As such, creating and publishing a package also implies a commitment to fixing bugs and making other updates, or at the very least making the package available as open source so others can help to maintain it.</span></span>

<span data-ttu-id="8e44c-111">En cualquier caso, el proceso de creación de un paquete comienza por decidir qué ensamblados y otros archivos se van a empaquetar.</span><span class="sxs-lookup"><span data-stu-id="8e44c-111">Whatever the case, creating a package begins with deciding which assemblies and other files to package.</span></span> <span data-ttu-id="8e44c-112">Luego se crea un archivo de manifiesto, conocido como archivo `.nuspec`, para describir el contenido del paquete junto con su identificador, el número de versión, la información de copyright, los destinos y las propiedades de MSBuild, etc.</span><span class="sxs-lookup"><span data-stu-id="8e44c-112">You then create a manifest file, referred to as a `.nuspec` file, to describe the package's contents along with its identifier, version number, copyright information, MSBuild props and targets, and much more.</span></span>

<span data-ttu-id="8e44c-113">Cuando haya preparado todos los archivos necesarios en las carpetas adecuadas y haya creado el archivo `.nuspec` correspondiente, deberá usar el comando `nuget pack` (o el [destino pack de MSBuild](../reference/msbuild-targets.md)) para ponerlo todo en un archivo `.nupkg`.</span><span class="sxs-lookup"><span data-stu-id="8e44c-113">When you've prepared all the necessary files in the appropriate folders and have created the appropriate `.nuspec` file, you then use the `nuget pack` command (or the [MSBuild pack target](../reference/msbuild-targets.md)) to put everything together into a `.nupkg` file.</span></span> <span data-ttu-id="8e44c-114">Entonces estará a punto para implementar el paquete en cualquier host que lo ponga a disposición de otros desarrolladores.</span><span class="sxs-lookup"><span data-stu-id="8e44c-114">You're then ready to deploy the package to whatever host makes it available to other developers.</span></span>

> [!Tip]
> <span data-ttu-id="8e44c-115">Un paquete de NuGet con la extensión `.nupkg` es un simple archivo ZIP.</span><span class="sxs-lookup"><span data-stu-id="8e44c-115">A NuGet package with the `.nupkg` extension is simply a ZIP file.</span></span> <span data-ttu-id="8e44c-116">Para examinar fácilmente el contenido de cualquier paquete, cambie la extensión a `.zip` y expanda su contenido como de costumbre.</span><span class="sxs-lookup"><span data-stu-id="8e44c-116">To easily examine any package's contents, change the extension to `.zip` and expand its contents as usual.</span></span> <span data-ttu-id="8e44c-117">Asegúrese de volver a cambiar la extensión a `.nupkg` antes de intentar cargarla en un host.</span><span class="sxs-lookup"><span data-stu-id="8e44c-117">Just be sure to change the extension back to `.nupkg` before attempting to upload it to a host.</span></span>

<span data-ttu-id="8e44c-118">Para aprender y entender el proceso de creación, comience [creando un paquete](../create-packages/creating-a-package.md), que le guiará a través de los procesos básicos comunes para todos los paquetes.</span><span class="sxs-lookup"><span data-stu-id="8e44c-118">To learn and understand the creation process, start with [Creating a package](../create-packages/creating-a-package.md) which guides you through the core processes common to all packages.</span></span>

<span data-ttu-id="8e44c-119">Desde ahí podrá plantearse una serie de opciones más para el paquete:</span><span class="sxs-lookup"><span data-stu-id="8e44c-119">From there, you can consider a number of other options for your package:</span></span>

- <span data-ttu-id="8e44c-120">En [Compatibilidad con varias plataformas de destino](../create-packages/supporting-multiple-target-frameworks.md) se describe cómo crear un paquete con varias variantes para diferentes versiones de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8e44c-120">[Supporting Multiple Target Frameworks](../create-packages/supporting-multiple-target-frameworks.md) describes how to create a package with multiple variants for different .NET Frameworks.</span></span>
- <span data-ttu-id="8e44c-121">En [Creación de paquetes localizados](../create-packages/creating-localized-packages.md) se describe cómo estructurar un paquete con varios recursos de idioma y cómo usar paquetes satélite localizados e independientes.</span><span class="sxs-lookup"><span data-stu-id="8e44c-121">[Creating Localized Packages](../create-packages/creating-localized-packages.md) describes how to structure a package with multiple language resources and how to use separate localized satellite packages.</span></span>
- <span data-ttu-id="8e44c-122">En [Paquetes de versión preliminar](../create-packages/prerelease-packages.md) se muestra cómo liberar paquetes alfa, beta y rc a aquellos clientes que estén interesados.</span><span class="sxs-lookup"><span data-stu-id="8e44c-122">[Pre-release Packages](../create-packages/prerelease-packages.md) demonstrates how to release alpha, beta, and rc packages to those customers who are interested.</span></span>
- <span data-ttu-id="8e44c-123">En [Origen y transformaciones del archivo de configuración](../create-packages/source-and-config-file-transformations.md) se describe cómo se pueden hacer reemplazos de tokens unidireccionales en archivos que se agregan a un proyecto y cómo modificar `web.config` y `app.config` con una configuración que también se retira cuando se desinstala el paquete.</span><span class="sxs-lookup"><span data-stu-id="8e44c-123">[Source and Config File Transformations](../create-packages/source-and-config-file-transformations.md) describes how you can do both one-way token replacements in files that are added to a project, and modify `web.config` and `app.config` with settings that are also backed out when the package is uninstalled.</span></span>
- <span data-ttu-id="8e44c-124">En [Paquetes de símbolos](../create-packages/symbol-packages.md) se ofrecen consejos para proporcionar símbolos para su biblioteca que permiten a los consumidores entrar en el código durante la depuración.</span><span class="sxs-lookup"><span data-stu-id="8e44c-124">[Symbol Packages](../create-packages/symbol-packages.md) offers guidance for supplying symbols for your library that allow consumers to step into your code while debugging.</span></span>
- <span data-ttu-id="8e44c-125">En [Package versioning](../reference/package-versioning.md) (Control de versiones de paquetes) se describe cómo identificar las versiones exactas que se permiten para las dependencias (otros paquetes que se usan en el paquete).</span><span class="sxs-lookup"><span data-stu-id="8e44c-125">[Package versioning](../reference/package-versioning.md) discusses how to identify the exact versions that you allow for your dependencies (other packages that you consume from your package).</span></span>
- <span data-ttu-id="8e44c-126">En [Paquetes nativos](../create-packages/native-packages.md) se describe el proceso de creación de un paquete para los consumidores de C++.</span><span class="sxs-lookup"><span data-stu-id="8e44c-126">[Native Packages](../create-packages/native-packages.md) describes the process for creating a package for C++ consumers.</span></span>
- <span data-ttu-id="8e44c-127">En [Firma de paquetes NuGet](../create-packages/sign-a-package.md) se describe el proceso para agregar una firma digital a un paquete.</span><span class="sxs-lookup"><span data-stu-id="8e44c-127">[Signing Packages](../create-packages/sign-a-package.md) describes the process for adding a digital signature to a package.</span></span>

<span data-ttu-id="8e44c-128">Cuando esté preparado para publicar un paquete en nuget.org, siga el proceso simple en [Publicar un paquete](../create-packages/publish-a-package.md).</span><span class="sxs-lookup"><span data-stu-id="8e44c-128">When you're then ready to publish a package to nuget.org, follow the simple process in [Publish a package](../create-packages/publish-a-package.md).</span></span>

<span data-ttu-id="8e44c-129">Si quiere usar una fuente privada en lugar de nuget.org, vea la [información general sobre el hospedaje de paquetes](../hosting-packages/overview.md).</span><span class="sxs-lookup"><span data-stu-id="8e44c-129">If you want to use a private feed instead of nuget.org, see the [Hosting Packages Overview](../hosting-packages/overview.md)</span></span>