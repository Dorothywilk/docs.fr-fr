---
title: '&#39;&lt;InterfaceName&gt;.&lt; MemberName&gt; &#39; est déjà implémenté par la classe de base &#39; &lt;nom_classe_base&gt;&#39;. Réimplémentation de &lt;type&gt; pris par défaut'
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 9054c293ede9db4637f23579407f2f76db29f2ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588968"
---
# <a name="39ltinterfacenamegtltmembernamegt39-is-already-implemented-by-the-base-class-39ltbaseclassnamegt39-re-implementation-of-lttypegt-assumed"></a>&#39;&lt;InterfaceName&gt;.&lt; MemberName&gt; &#39; est déjà implémenté par la classe de base &#39; &lt;nom_classe_base&gt;&#39;. Réimplémentation de &lt;type&gt; pris par défaut
Une propriété, une procédure ou un événement dans une classe dérivée utilise une `Implements` clause qui spécifie un membre d’interface qui est déjà implémenté dans la classe de base.  
  
 Une classe dérivée peut réimplémenter un membre d’interface qui est implémenté par sa classe de base. La substitution de l’implémentation de la classe de base est une procédure différente. Pour plus d’informations, consultez [implémente](../../../visual-basic/language-reference/statements/implements-clause.md).  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** BC42015  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Si vous comptez réimplémenter le membre d’interface, aucune mesure n’est nécessaire. Code de votre classe dérivée accède au membre réimplémenté, sauf si vous utilisez le `MyBase` mot clé pour accéder à l’implémentation de classe de base.  
  
-   Si vous ne comptez pas réimplémenter le membre d’interface, supprimez la clause `Implements` de la déclaration de la propriété, de la procédure ou de l’événement.  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
