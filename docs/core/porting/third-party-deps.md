---
title: Portage sur .NET Core - Analyser vos dépendances tierces
description: Découvrez comment analyser les dépendances tierces afin de porter votre projet de .NET Framework sur .NET Core.
author: cartermp
ms.author: mairaw
ms.date: 02/15/2018
ms.openlocfilehash: 06d8d36d8369680c54af4d16513b2b871b57079c
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46000997"
---
# <a name="analyze-your-third-party-dependencies"></a>Analyser vos dépendances tierces

Si vous envisagez de porter votre code sur .NET Core ou .NET Standard, la première étape du processus de portage consiste à comprendre les dépendances tierces. Les dépendances tierces sont des [packages NuGet](#analyze-referenced-nuget-packages-on-your-project) ou des [DLL](#analyze-dependencies-that-arent-nuget-packages) que vous référencez dans votre projet. Évaluez chaque dépendance et développez un plan d’urgence pour les dépendances qui ne sont pas compatibles avec .NET Core. Cet article explique comment déterminer si la dépendance est compatible avec .NET Core.

## <a name="analyze-referenced-nuget-packages-in-your-project"></a>Analyser les packages NuGet référencés dans votre projet

Si vous référencez des packages NuGet dans votre projet, vous devez vérifier s’ils sont compatibles avec .NET Core.
Pour cela, vous avez le choix entre :

* [Utiliser l’application NuGet Package Explorer](#analyze-nuget-packages-using-nuget-package-explorer) (la méthode la plus fiable).
* [Utiliser le site nuget.org](#analyze-nuget-packages-using-nugetorg).

Après avoir analysé les packages, s’il s’avère qu’ils ne sont pas compatibles avec .NET Core et ne ciblent que le .NET Framework, vous pouvez vérifier si le [mode de compatibilité du .NET Framework](#net-framework-compatibility-mode) peut vous être utile pour le processus de portage.

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a>Analyser les packages NuGet à l’aide de NuGet Package Explorer

Un package NuGet est lui-même un ensemble de dossiers qui contiennent des assemblys spécifiques aux plateformes. Vous devez donc vérifier s’il existe dans le package un dossier qui contient un assembly compatible.

La méthode la plus facile pour inspecter les dossiers NuGet consiste à utiliser l’outil [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer). Après l’avoir installé, effectuez les étapes suivantes pour afficher les noms de dossiers :

1. Ouvrez NuGet Package Explorer.
2. Cliquez sur **Open package from online feed**.
3. Recherchez le nom du package.
4. Sélectionnez le nom du package dans les résultats de la recherche et cliquez sur **Open**.
5. Développez le dossier *lib* qui se trouve sur la droite et examinez les noms de dossiers.

Recherchez un dossier portant l’un des noms suivants :

```
netstandard1.0
netstandard1.1
netstandard1.2
netstandard1.3
netstandard1.4
netstandard1.5
netstandard1.6
netstandard2.0
netcoreapp1.0
netcoreapp1.1
netcoreapp2.0
netcoreapp2.1
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

Ces valeurs sont les [monikers de framework cible (TFM, Target Framework Monikers)](../../standard/frameworks.md) qui correspondent aux versions des profils de bibliothèques de classes portables [.NET Standard](../../standard/net-standard.md), .NET Core et traditionnels qui sont compatibles avec .NET Core.

> [!IMPORTANT]
> Lorsque vous observez les TFM pris en charge par un package, notez que `netcoreapp*`, bien que compatible, ne s’applique qu’aux projets .NET Core, pas aux projets .NET Standard.
> Une bibliothèque qui cible uniquement `netcoreapp*` et pas `netstandard*` ne peut être consommée que par d’autres applications .NET Core.

Il existe également certains monikers du Framework cible hérités utilisés dans des préversions de .NET Core qui peuvent également être compatibles :

```
dnxcore50
dotnet5.0
dotnet5.1
dotnet5.2
dotnet5.3
dotnet5.4
dotnet5.5
```

Même s’il est probable que ces TFM fonctionnent avec votre code, il n’existe aucune garantie de compatibilité. Les packages avec ces monikers du Framework cible ont été créés avec des packages .NET Core en préversion. Notez quand (et si) les packages utilisant ces TFM sont mis à jour pour être basés sur .NET Standard.

> [!NOTE]
> Pour utiliser un package ciblant une bibliothèque de classes portables ou une cible .NET Core en préversion, vous devez utiliser l’élément MSBuild `PackageTargetFallback` de votre fichier projet.
> Pour plus d’informations sur cet élément MSBuild, consultez [`PackageTargetFallback`](../tools/csproj.md#packagetargetfallback).

### <a name="analyze-nuget-packages-using-nugetorg"></a>Analyser les packages NuGet à l’aide de nuget.org

Vous pouvez également connaître les TFM pris en charge par chaque package sur [nuget.org](https://www.nuget.org/), dans la section **Dependencies** de la page du package spécifique.

Bien qu’il soit plus facile d’utiliser le site pour vérifier la compatibilité, les informations de **dépendances** ne sont pas disponibles sur le site de tous les packages.

### <a name="net-framework-compatibility-mode"></a>Mode de compatibilité du .NET Framework

Après avoir analysé les packages NuGet, vous constaterez peut-être qu’ils ne ciblent que le .NET Framework, comme c’est le cas de la plupart des packages NuGet.

Le mode de compatibilité du .NET Framework a été introduit dans .NET Standard 2.0. Ce mode de compatibilité permet aux projets .NET Standard et .NET Core de référencer des bibliothèques .NET Framework. Le référencement de bibliothèques .NET Framework ne fonctionne pas pour tous les projets, par exemple si la bibliothèque utilise des API WPF (Windows Presentation Foundation), mais cela débloque de nombreux scénarios de portage.

Lorsque vous référencez des packages NuGet qui ciblent le .NET Framework dans votre projet, comme [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), vous obtenez un avertissement de package de secours ([NU1701](/nuget/reference/errors-and-warnings#nu1701)) similaire à l’exemple suivant :

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

Cet avertissement s’affiche lorsque vous ajoutez le package et chaque fois que vous générez une build, pour vous rappeler de tester ce package avec votre projet. Si votre projet fonctionne comme prévu, vous pouvez supprimer cet avertissement en modifiant les propriétés du package dans Visual Studio ou en modifiant manuellement le fichier projet dans votre éditeur de code favori.

Pour supprimer l’avertissement en modifiant le fichier projet, recherchez l’entrée `PackageReference` du package pour lequel vous souhaitez supprimer l’avertissement, puis ajoutez l’attribut `NoWarn`. L’attribut `NoWarn` accepte une liste séparée par des virgules de tous les ID d’avertissement. L’exemple suivant montre comment supprimer l’avertissement `NU1701` pour le package `Huitian.PowerCollections` en modifiant votre fichier projet manuellement :

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

Pour plus d’informations sur la façon de supprimer les avertissements du compilateur dans Visual Studio, consultez [Suppression d’avertissements pour les packages NuGet](/visualstudio/ide/how-to-suppress-compiler-warnings#suppressing-warnings-for-nuget-packages).

### <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a>Ce qu’il faut faire quand votre dépendance de package NuGet ne s’exécute pas sur .NET Core

Voici quelques actions possibles si un package NuGet dont vous dépendez ne s’exécute pas sur .NET Core :

1. Si le projet est open source et hébergé à un endroit comme GitHub, vous pouvez demander aux développeurs de le modifier.
2. Vous pouvez contacter l’auteur directement sur [nuget.org](https://www.nuget.org/). Recherchez le package, puis cliquez sur **Contact Owners** sur le côté gauche de la page du package.
3. Vous pouvez rechercher un autre package qui s’exécute sur .NET Core et qui réalise la même tâche que le package que vous utilisez.
4. Vous pouvez essayer d’écrire vous-même le code qui était exécuté par le package.
5. Vous pouvez éliminer la dépendance du package en modifiant les fonctionnalités de votre application, au moins jusqu’à ce qu’une version compatible du package soit disponible.

N’oubliez pas que les personnes chargées de la maintenance des projets open source et les éditeurs de packages NuGet sont souvent des bénévoles. Ils offrent leur contribution car ils s’intéressent à un domaine donné, ils le font gratuitement et ont souvent un autre travail dans la journée. Pensez-y lorsque vous les contactez pour leur demander de l’aide sur .NET Core.

Si vous ne parvenez pas à résoudre votre problème avec les actions ci-dessus, vous devrez peut-être porter votre code sur .NET Core à une date ultérieure.

L’équipe .NET aimerait savoir quelles bibliothèques doivent être prioritairement prises en charge avec .NET Core. Vous pouvez nous envoyer un e-mail à l’adresse dotnet@microsoft.com afin de nous indiquer les bibliothèques que vous voudriez utiliser.

## <a name="analyze-dependencies-that-arent-nuget-packages"></a>Analyser des dépendances qui ne sont pas des packages NuGet

Vous avez peut-être une dépendance qui n’est pas un package NuGet, comme une DLL dans le système de fichiers. La seule façon de déterminer la portabilité de cette dépendance est d’exécuter l’outil [.NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport). Cet outil peut analyser les assemblys qui ciblent le .NET Framework et identifier les API qui ne sont pas portables sur d’autres plateformes .NET telles que .NET Core. Vous pouvez exécuter cet outil en tant qu’application console ou qu’[extension Visual Studio](../../standard/analyzers/portability-analyzer.md).

## <a name="next-steps"></a>Étapes suivantes

Si vous portez une bibliothèque, consultez [Portage de vos bibliothèques](libraries.md).
