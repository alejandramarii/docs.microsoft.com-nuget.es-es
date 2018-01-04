---
title: "Cómo crear paquetes de símbolos de NuGet | Microsoft Docs"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 9/12/2017
ms.topic: article
ms.prod: nuget
ms.technology: 
ms.assetid: 4667a70d-5a17-4f1e-b2f2-b8d0c6af3882
description: "Cómo crear paquetes de NuGet que solo contienen símbolos para admitir la depuración de otros paquetes de NuGet en Visual Studio."
keywords: "Paquetes de símbolos de NuGet, depuración de paquetes de NuGet, compatibilidad con la depuración de NuGet, símbolos de paquetes, convenciones de paquetes de símbolos"
ms.reviewer:
- anangaur
- karann-msft
- unniravindranathan
ms.openlocfilehash: b1a29fe6e9a3dec6847dbed07761e28fb8eb9b19
ms.sourcegitcommit: d0ba99bfe019b779b75731bafdca8a37e35ef0d9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2017
---
# <a name="creating-symbol-packages"></a><span data-ttu-id="02c11-104">Crear paquetes de símbolos</span><span class="sxs-lookup"><span data-stu-id="02c11-104">Creating symbol packages</span></span>

<span data-ttu-id="02c11-105">Además de crear paquetes para nuget.org u otros orígenes, NuGet también admite la creación de paquetes de símbolos asociados y su publicación en el [repositorio SymbolSource](http://www.symbolsource.org/Public).</span><span class="sxs-lookup"><span data-stu-id="02c11-105">In addition to building packages for nuget.org or other sources, NuGet also supports creating associated symbol packages and publishing them to the [SymbolSource repository](http://www.symbolsource.org/Public).</span></span>

<span data-ttu-id="02c11-106">Los consumidores de paquetes pueden agregar `http://srv.symbolsource.org/pdb/Public` a sus orígenes de símbolos en Visual Studio, que permite entrar en el código del paquete en el depurador de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="02c11-106">Package consumers can then add `http://srv.symbolsource.org/pdb/Public` to their symbol sources in Visual Studio, which allows stepping into package code in the Visual Studio debugger.</span></span> <span data-ttu-id="02c11-107">Vea [Especificar archivos de código fuente y símbolos (.pdb) en el depurador de Visual Studio](https://docs.microsoft.com/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger) para obtener información detallada sobre ese proceso.</span><span class="sxs-lookup"><span data-stu-id="02c11-107">See [Specify symbol (.pdb) and source files in the Visual Studio debugger](https://docs.microsoft.com/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger) for details on that process.</span></span>


## <a name="creating-a-symbol-package"></a><span data-ttu-id="02c11-108">Crear un paquete de símbolos</span><span class="sxs-lookup"><span data-stu-id="02c11-108">Creating a symbol package</span></span>

<span data-ttu-id="02c11-109">Para crear un paquete de símbolos, siga estas convenciones:</span><span class="sxs-lookup"><span data-stu-id="02c11-109">To create a symbol package, follow these conventions:</span></span>

- <span data-ttu-id="02c11-110">Asigne al paquete principal (con el código) el nombre `{identifier}.nupkg` e incluya todos los archivos excepto los archivos `.pdb`.</span><span class="sxs-lookup"><span data-stu-id="02c11-110">Name the primary package (with your code) `{identifier}.nupkg` and include all your files except `.pdb` files.</span></span>
- <span data-ttu-id="02c11-111">Asigne al paquete de símbolos el nombre `{identifier}.symbols.nupkg` e incluya los archivos DLL de ensamblado, los archivos `.pdb`, los archivos XMLDOC y los archivos de origen (vea las secciones siguientes).</span><span class="sxs-lookup"><span data-stu-id="02c11-111">Name the symbol package `{identifier}.symbols.nupkg` and include your assembly DLL, `.pdb` files, XMLDOC files, source files (see the sections that follow).</span></span>

<span data-ttu-id="02c11-112">Puede crear ambos paquetes con la opción `-Symbols`, ya sea desde un archivo `.nuspec` o desde un archivo de proyecto:</span><span class="sxs-lookup"><span data-stu-id="02c11-112">You can create both packages with the `-Symbols` option, either from a `.nuspec` file or a project file:</span></span>

```
nuget pack MyPackage.nuspec -Symbols

nuget pack MyProject.csproj -Symbols
```

<span data-ttu-id="02c11-113">Tenga en cuenta que `pack` requiere Mono 4.4.2 en Mac OS X y no funciona en los sistemas Linux.</span><span class="sxs-lookup"><span data-stu-id="02c11-113">Note that `pack` requires Mono 4.4.2 on Mac OS X and does not work on Linux systems.</span></span> <span data-ttu-id="02c11-114">En los equipos Mac, también debe convertir los nombres de las rutas de acceso de Windows del archivo `.nuspec` a las rutas de acceso de estilo Unix.</span><span class="sxs-lookup"><span data-stu-id="02c11-114">On a Mac, you must also convert Windows pathnames in the `.nuspec` file to Unix-style paths.</span></span>

## <a name="symbol-package-structure"></a><span data-ttu-id="02c11-115">Estructura del paquete de símbolos</span><span class="sxs-lookup"><span data-stu-id="02c11-115">Symbol package structure</span></span>

<span data-ttu-id="02c11-116">Un paquete de símbolos puede tener como destino varias plataformas de destino de la misma manera que un paquete de bibliotecas, por lo que la estructura de la carpeta `lib` debe ser exactamente igual que el paquete principal, incluyendo solo los archivos `.pdb` junto con los archivos DLL.</span><span class="sxs-lookup"><span data-stu-id="02c11-116">A symbol package can target multiple target frameworks in the same way that a library package does, so the structure of the `lib` folder should be exactly the same as the primary package, only including `.pdb` files alongside the DLL.</span></span>

<span data-ttu-id="02c11-117">Por ejemplo, un paquete de símbolos que tenga como destino .NET 4.0 y Silverlight 4 tendría este diseño:</span><span class="sxs-lookup"><span data-stu-id="02c11-117">For example, a symbol package that targets .NET 4.0 and Silverlight 4 would have this layout:</span></span>

    \lib
        \net40
            \MyAssembly.dll
            \MyAssembly.pdb
        \sl40
            \MyAssembly.dll
            \MyAssembly.pdb

<span data-ttu-id="02c11-118">Los archivos de código fuente se colocan en una carpeta especial independiente denominada `src`, que debe seguir la estructura relativa del repositorio de origen.</span><span class="sxs-lookup"><span data-stu-id="02c11-118">Source files are then placed in a separate special folder named `src`, which must follow the relative structure of your source repository.</span></span> <span data-ttu-id="02c11-119">Esto es así porque los archivos PDB contienen rutas de acceso absolutas a los archivos de código fuente que se usan para compilar los archivos DLL correspondientes y se deben buscar durante el proceso de publicación.</span><span class="sxs-lookup"><span data-stu-id="02c11-119">This is because PDBs contain absolute paths to source files used to compile the matching DLL, and they need to be found during the publishing process.</span></span> <span data-ttu-id="02c11-120">Se puede quitar una ruta de acceso base (prefijo de ruta de acceso común). Por ejemplo, imagínese que tiene una biblioteca creada a partir de estos archivos:</span><span class="sxs-lookup"><span data-stu-id="02c11-120">A base path (common path prefix) can be stripped out. For example, consider a library built from these files:</span></span>

    C:\Projects
        \MyProject
            \Common
                \MyClass.cs
            \Full
                \Properties
                    \AssemblyInfo.cs
                \MyAssembly.csproj (producing \lib\net40\MyAssembly.dll)
            \Silverlight
                \Properties
                    \AssemblyInfo.cs
                \MySilverlightExtensions.cs
                \MyAssembly.csproj (producing \lib\sl4\MyAssembly.dll)

<span data-ttu-id="02c11-121">Aparte de la carpeta `lib`, un paquete de símbolos tendría que tener este diseño:</span><span class="sxs-lookup"><span data-stu-id="02c11-121">Apart from the `lib` folder, a symbol package would need to contain this layout:</span></span>

    \src
        \Common
            \MyClass.cs
        \Full
            \Properties
                \AssemblyInfo.cs
        \Silverlight
            \Properties
                \AssemblyInfo.cs
            \MySilverlightExtensions.cs

## <a name="referring-to-files-in-the-nuspec"></a><span data-ttu-id="02c11-122">Hacer referencia a los archivos en el archivo nuspec</span><span class="sxs-lookup"><span data-stu-id="02c11-122">Referring to files in the nuspec</span></span>

<span data-ttu-id="02c11-123">Se puede crear un paquete de símbolos mediante convenciones a partir de una estructura de carpetas, tal y como se describe en la sección anterior, o especificando su contenido en la sección `files` del manifiesto.</span><span class="sxs-lookup"><span data-stu-id="02c11-123">A symbol package can be built by conventions, from a folder structure as described in the previous section, or by specifying its contents in the `files` section of the manifest.</span></span> <span data-ttu-id="02c11-124">Por ejemplo, para crear el paquete que se muestra en la sección anterior, use lo siguiente en el archivo `.nuspec`:</span><span class="sxs-lookup"><span data-stu-id="02c11-124">For example, to build the package shown in the previous section, use the following in the `.nuspec` file:</span></span>

```xml
<files>
    <file src="Full\bin\Debug\*.dll" target="lib\net40" />
    <file src="Full\bin\Debug\*.pdb" target="lib\net40" />
    <file src="Silverlight\bin\Debug\*.dll" target="lib\sl40" />
    <file src="Silverlight\bin\Debug\*.pdb" target="lib\sl40" />
    <file src="**\*.cs" target="src" />
</files>
```

## <a name="publishing-a-symbol-package"></a><span data-ttu-id="02c11-125">Publicar un paquete de símbolos</span><span class="sxs-lookup"><span data-stu-id="02c11-125">Publishing a symbol package</span></span>

> [!Important]
> <span data-ttu-id="02c11-126">Para insertar paquetes en nuget.org debe usar [la versión 4.1.0 o una versión posterior de nuget.exe](https://www.nuget.org/downloads), que implementa los [protocolos de NuGet](../api/nuget-protocols.md) necesarios.</span><span class="sxs-lookup"><span data-stu-id="02c11-126">To push packages to nuget.org you must use [nuget.exe v4.1.0 or above](https://www.nuget.org/downloads), which implements the required [NuGet protocols](../api/nuget-protocols.md).</span></span>

1. <span data-ttu-id="02c11-127">Para mayor comodidad, guarde primero la clave de API con NuGet (vea [Publish a package](../create-packages/publish-a-package.md) [Publicar un paquete]), que se aplicará a nuget.org y a symbolsource.org, porque symbolsource.org comprobará con nuget.org que usted es el propietario del paquete.</span><span class="sxs-lookup"><span data-stu-id="02c11-127">For convenience, first save your API key with NuGet (see [publish a package](../create-packages/publish-a-package.md), which will apply to both nuget.org and symbolsource.org, because symbolsource.org will check with nuget.org to verify that you are the package owner.</span></span>

    ```
    nuget SetApiKey Your-API-Key
    ```

1. <span data-ttu-id="02c11-128">Una vez publicado el paquete principal en nuget.org, inserte el paquete de símbolos del siguiente modo. El paquete usará automáticamente symbolsource.org como destino debido a la aparición de `.symbols` en el nombre de archivo:</span><span class="sxs-lookup"><span data-stu-id="02c11-128">After publishing your primary package to nuget.org, push the symbol package as follows, which will automatically use symbolsource.org as the target because of the `.symbols` in the filename:</span></span>

    ```
    nuget push MyPackage.symbols.nupkg
    ```
> [!Note]
> <span data-ttu-id="02c11-129">Con la versión 4.5.0 o una versión posterior de nuget.exe, los paquetes de símbolos no se insertan automáticamente en symbolsource.org. Tendría que insertar los paquetes de símbolos por separado, tal como se describe en el paso siguiente.</span><span class="sxs-lookup"><span data-stu-id="02c11-129">With nuget.exe 4.5.0 or above, the symbols packages are not automatically pushed to symbolsource.org. You would need to push the symbols packages separately as explained in the next step.</span></span>

1. <span data-ttu-id="02c11-130">Para publicar el paquete en otro repositorio de símbolos, o para insertar un paquete de símbolos que no sigue la convención de nomenclatura, use la opción `-Source`:</span><span class="sxs-lookup"><span data-stu-id="02c11-130">To publish to a different symbol repository, or to push a symbol package that doesn't follow the naming convention, use the `-Source` option:</span></span>

    ```
    nuget push MyPackage.symbols.nupkg -source https://nuget.smbsrc.net/
    ```

1. <span data-ttu-id="02c11-131">También puede insertar el paquete principal y el paquete de símbolos en ambos repositorios a la vez usando lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="02c11-131">You can also push both primary and symbol packages to both repositories at the same time using the following:</span></span>

    ```
    nuget push MyPackage.nupkg
    ```

<span data-ttu-id="02c11-132">En este caso, NuGet publicará `MyPackage.symbols.nupkg`, si existe, en https://nuget.smbsrc.net/ (la dirección URL de inserción para symbolsource.org) después de que haya publicado el paquete principal en nuget.org.</span><span class="sxs-lookup"><span data-stu-id="02c11-132">In this case, NuGet will publish `MyPackage.symbols.nupkg`, if present, to https://nuget.smbsrc.net/ (the push URL for symbolsource.org), after it publishes the primary package to nuget.org.</span></span>

## <a name="see-also"></a><span data-ttu-id="02c11-133">Vea también</span><span class="sxs-lookup"><span data-stu-id="02c11-133">See Also</span></span>

 - <span data-ttu-id="02c11-134"><a href="https://www.symbolsource.org/Public/Wiki/Using" target="_blank">Usar SymbolSource</a> (symbolsource.org)</span><span class="sxs-lookup"><span data-stu-id="02c11-134"><a href="https://www.symbolsource.org/Public/Wiki/Using" target="_blank">Using SymbolSource</a> (symbolsource.org)</span></span>