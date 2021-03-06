---
title: '#warning (informations de référence sur C#)'
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 59ca63d5089e377627a9116f24f9a0a1681bb4b2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506345"
---
# <a name="warning-c-reference"></a>#warning (référence C#)
`#warning` vous permet de générer un avertissement du compilateur de premier niveau [CS1030](../../misc/cs1030.md) à partir d’un emplacement spécifique dans votre code. Exemple :  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a>Notes
 `#warning` est souvent utilisé dans une directive conditionnelle. Il est aussi possible de générer une erreur définie par l’utilisateur avec [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).  
  
## <a name="example"></a>Exemple  

```csharp
// preprocessor_warning.cs  
// CS1030 expected  
#define DEBUG  
class MainClass
{  
    static void Main()
    {  
#if DEBUG  
#warning DEBUG is defined  
#endif  
    }  
}  
```  

## <a name="see-also"></a>Voir aussi

- [Référence C#](../../../csharp/language-reference/index.md)  
- [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
- [Directives de préprocesseur C#](../../../csharp/language-reference/preprocessor-directives/index.md)
