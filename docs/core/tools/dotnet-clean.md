---
title: Commande dotnet clean - Interface CLI .NET Core
description: La commande dotnet clean nettoie le répertoire actif.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 5553e4b4423a2d824c05caf7114c47b5f1c20477
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "45988333"
---
# <a name="dotnet-clean"></a>dotnet clean

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Name

`dotnet clean` : Nettoie la sortie d’un projet.

## <a name="synopsis"></a>Résumé

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-v|--verbosity]
dotnet clean [-h|--help]
```
---

## <a name="description"></a>Description

La commande `dotnet clean` nettoie la sortie de la génération précédente. Comme elle est implémentée en tant que [cible MSBuild](/visualstudio/msbuild/msbuild-targets), le projet est évalué lorsque la commande est exécutée. Seules les sorties créées lors de la génération sont nettoyées. Les dossiers de sortie intermédiaire (*obj*) et de sortie finale (*bin*) sont tous deux nettoyés.

## <a name="arguments"></a>Arguments

`PROJECT`

Le projet MSBuild à nettoyer. Si vous ne spécifiez pas de fichier projet, MSBuild recherche dans le répertoire de travail actuel un fichier avec une extension se terminant par *proj* et l’utilise.

## <a name="options"></a>Options

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

Définit la configuration de build. La valeur par défaut est `Debug`. Cette option est uniquement requise durant le nettoyage si vous l’avez spécifiée au moment de la génération.

`-f|--framework <FRAMEWORK>`

Le [framework](../../standard/frameworks.md) spécifié au moment de la génération. Le framework doit être défini dans le [fichier projet](csproj.md). Si vous avez spécifié le framework au moment de la génération, vous devez spécifier le framework lors du nettoyage.

`-h|--help`

Affiche une aide brève pour la commande.

`-o|--output <OUTPUT_DIRECTORY>`

Répertoire dans lequel les sorties générées sont placées. Spécifiez le commutateur `-f|--framework <FRAMEWORK>` avec le commutateur de répertoire de sortie si vous avez spécifié le framework lorsque le projet a été généré.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Nettoie le dossier de sortie du runtime spécifié. Cette option est utilisée à la création d’un [déploiement autonome](../deploying/index.md#self-contained-deployments-scd).

`-v|--verbosity <LEVEL>`

Définit le niveau de détail de la commande. Niveaux autorisés : q[uiet], m[inimal], n[ormal], d[etailed] et diag[nostic].

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

Définit la configuration de build. La valeur par défaut est `Debug`. Cette option est uniquement requise durant le nettoyage si vous l’avez spécifiée au moment de la génération.

`-f|--framework <FRAMEWORK>`

Le [framework](../../standard/frameworks.md) spécifié au moment de la génération. Le framework doit être défini dans le [fichier projet](csproj.md). Si vous avez spécifié le framework au moment de la génération, vous devez spécifier le framework lors du nettoyage.

`-h|--help`

Affiche une aide brève pour la commande.

`-o|--output <OUTPUT_DIRECTORY>`

Répertoire dans lequel les sorties générées sont placées. Spécifiez le commutateur `-f|--framework <FRAMEWORK>` avec le commutateur de répertoire de sortie si vous avez spécifié le framework lorsque le projet a été généré.

`-v|--verbosity <LEVEL>`

Définit le niveau de détail de la commande. Niveaux autorisés : q[uiet], m[inimal], n[ormal], d[etailed] et diag[nostic].

---

## <a name="examples"></a>Exemples

Nettoyez une génération par défaut du projet :

`dotnet clean`

Nettoyez un projet généré à l’aide de la configuration Release :

`dotnet clean --configuration Release`
