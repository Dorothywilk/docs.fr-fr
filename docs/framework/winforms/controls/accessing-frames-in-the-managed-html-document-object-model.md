---
title: Accès aux frames dans le modèle objet de document HTML managé
ms.date: 03/30/2017
helpviewer_keywords:
- HTML [Windows Forms], dOM
- managed HTML DOM
- HTML [Windows Forms], managed
- HTML DOM [Windows Forms], managed
- frames [Windows Forms], accessing
- DOM [Windows Forms], accessing frames in managed HTML
ms.assetid: cdeeaa22-0be4-4bbf-9a75-4ddc79199f8d
ms.openlocfilehash: b1a858e88ff27de19e2ebbd69c14060813873c13
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2018
ms.locfileid: "49308485"
---
# <a name="accessing-frames-in-the-managed-html-document-object-model"></a>Accès aux frames dans le modèle objet de document HTML managé
Certains documents HTML sont composés de *frames*, ou windows qui peuvent contenir leurs propres documents HTML. L'utilisation de frames simplifie la création de pages HTML dans lesquelles un ou plusieurs éléments de la page (tels qu'une barre de navigation) restent statiques, tandis que d'autres frames changent constamment de contenu.  
  
 Les auteurs de code HTML peuvent créer des frames de deux façons :  
  
-   à l'aide des balises `FRAMESET` et `FRAME`, qui créent des fenêtres fixes.  
  
 ou  
  
-   à l'aide de la balise `IFRAME`, qui crée une fenêtre flottante pouvant être repositionnée au moment de l'exécution.  
  
1.  Les frames contenant des documents HTML, ils sont représentés dans le modèle DOM en tant qu'éléments de fenêtre et éléments de cadre.  
  
2.  Quand vous accédez à une balise `FRAME` ou `IFRAME` à l'aide de la collection Frames de <xref:System.Windows.Forms.HtmlWindow>, vous récupérez l'élément de fenêtre correspondant au frame. Il représente toutes les propriétés dynamiques du frame, telles que son URL, son document et sa taille actuels.  
  
3.  Quand vous accédez à une balise `FRAME` ou `IFRAME` à l'aide de la propriété <xref:System.Windows.Forms.HtmlWindow.WindowFrameElement%2A> de <xref:System.Windows.Forms.HtmlWindow>, de la collection <xref:System.Windows.Forms.HtmlElement.Children%2A> ou de méthodes telles que <xref:System.Windows.Forms.HtmlElementCollection.GetElementsByName%2A> ou <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A>, vous récupérez l'élément de frame. Il représente les propriétés statiques du frame, y compris l'URL spécifiée dans le fichier HTML d'origine.  
  
## <a name="frames-and-security"></a>Frames et sécurité  
 L’accès aux frames est compliqué par le fait que le modèle DOM HTML managé implémente une mesure de sécurité connu sous le nom *inter-frame sécurité des scripts*. Si un document contient un `FRAMESET` avec plusieurs `FRAME` dans différents domaines, ces `FRAME` ne peuvent pas interagir. En d’autres termes, une `FRAME` qu’affiche le contenu de votre site Web ne peut pas accéder aux informations dans un `FRAME` qui héberge un site tiers comme `http://www.adatum.com/`. Cette sécurité est implémentée au niveau de la classe <xref:System.Windows.Forms.HtmlWindow>. Vous pouvez obtenir des informations générales sur un `FRAME` qui héberge un autre site web, telles que son URL, mais vous ne pourrez pas accéder à son <xref:System.Windows.Forms.HtmlWindow.Document%2A> ni modifier la taille ou l'emplacement de son `FRAME` ou `IFRAME` hébergeur.  
  
 Cette règle s'applique également aux fenêtres que vous ouvrez à l'aide des méthodes <xref:System.Windows.Forms.HtmlWindow.Open%2A> et <xref:System.Windows.Forms.HtmlWindow.OpenNew%2A>. Si la fenêtre que vous ouvrez est dans un domaine différent de celui de la page hébergée dans le contrôle <xref:System.Windows.Forms.WebBrowser>, vous ne pourrez pas déplacer cette fenêtre ni examiner son contenu. Ces restrictions s'appliquent également si vous utilisez le contrôle <xref:System.Windows.Forms.WebBrowser> pour afficher un site web différent de celui utilisé pour déployer votre application Windows Forms. Si vous utilisez la technologie de déploiement [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] pour installer votre application à partir du site web A et que vous utilisez <xref:System.Windows.Forms.WebBrowser> pour afficher le site web B, vous ne pourrez pas accéder aux données du site web B.  
  
 Pour plus d’informations sur les scripts intersites, consultez [About Cross-Frame Scripting and Security](https://msdn.microsoft.com/library/ms533028.aspx).  
  
## <a name="see-also"></a>Voir aussi  
 [Élément FRAME &#124; objet frame](https://msdn.microsoft.com/library/ms535250.aspx)  
 [Utilisation du modèle DOM HTML managé](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
