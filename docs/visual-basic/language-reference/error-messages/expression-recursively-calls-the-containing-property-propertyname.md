---
title: Récursive de l’expression appelle la propriété conteneur &#39; &lt;propertyname&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: f14e2645772b22a8f6ff2385dcd316a42d1d5cf0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588841"
---
# <a name="expression-recursively-calls-the-containing-property-39ltpropertynamegt39"></a>Récursive de l’expression appelle la propriété conteneur &#39; &lt;propertyname&gt;&#39;
Une instruction dans le `Set` d’une définition de propriété stocke une valeur dans le nom de la propriété.  
  
 L’approche recommandée pour stocker la valeur d’une propriété consiste à définir un `Private` variable dans le conteneur de la propriété et l’utiliser à la fois dans le `Get` et `Set` procédures. Le `Set` procédure doit ensuite stocker la valeur entrante dans cette `Private` variable.  
  
 Le `Get` procédure se comporte comme un `Function` procédure, donc il peut affecter une valeur au nom de propriété et retourner le contrôle en utilisant la `End Get` instruction. L’approche recommandée, toutefois, est à inclure le `Private` variable comme valeur dans un [instruction Return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 Le `Set` procédure se comporte comme un `Sub` procédure qui ne retourne pas de valeur. Par conséquent, le nom de la procédure ou la propriété a une signification spéciale dans un `Set` et vous ne peut pas y stocker une valeur.  
  
 L’exemple suivant illustre l’approche qui peut provoquer cette erreur, suivie de l’approche recommandée.  
  
```  
Public Class illustrateProperties  
' The code in the following property causes this error.  
    Public Property badProp() As Char  
        Get  
            Dim charValue As Char  
            ' Insert code to update charValue.  
            badProp = charValue  
        End Get  
        Set(ByVal Value As Char)  
            ' The following statement causes this error.  
            badProp = Value  
            ' The value stored in the local variable badProp  
            ' is not used by the Get procedure in this property.  
        End Set  
    End Property  
' The following code uses the recommended approach.  
    Private propValue As Char  
    Public Property goodProp() As Char  
        Get  
            ' Insert code to update propValue.  
            Return propValue  
        End Get  
        Set(ByVal Value As Char)  
            propValue = Value  
        End Set  
    End Property  
End Class  
```  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [configuration des avertissements en Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** BC42026  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Réécrivez la définition de propriété pour utiliser l’approche recommandée, comme illustré dans l’exemple précédent.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures de propriété](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Set (instruction)](../../../visual-basic/language-reference/statements/set-statement.md)
