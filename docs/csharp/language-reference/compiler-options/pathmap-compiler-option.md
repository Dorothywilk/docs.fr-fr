---
title: -pathmap (Options du compilateur C#)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 277ab8e094f28fd5e3cbba4de12e742bb9614730
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47425782"
---
# <a name="-pathmap-c-compiler-options"></a>-pathmap (Options du compilateur C#)

L’option de compilateur **-pathmap** spécifie comment mapper des chemins physiques aux noms de chemin source générés en sortie par le compilateur.

## <a name="syntax"></a>Syntaxe

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a>Arguments

 `path1` : chemin complet aux fichiers sources dans l’environnement actuel

 `sourcePath1` : chemin source remplaçant `path1` dans les fichiers de sortie.

Pour spécifier plusieurs chemins sources mappés, séparez-les par des virgules.

## <a name="remarks"></a>Notes

Le compilateur écrit le chemin source dans sa sortie dans les cas suivants :

1. Le chemin source est remplacé par un argument quand <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> est appliqué à un paramètre facultatif.
1. Le chemin source est incorporé dans un fichier PDB.
1. Le chemin du fichier PDB est incorporé dans un fichier exécutable portable (PE).

Cette option mappe chaque chemin physique de l’ordinateur sur lequel le compilateur s’exécute à un chemin correspondant qui doit être écrit dans les fichiers de sortie.

## <a name="example"></a>Exemple

Compilez `t.cs` dans le répertoire **C:\\work\\tests** et mappez ce répertoire à **\publish** dans la sortie :

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a>Voir aussi

- [Options du compilateur C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
