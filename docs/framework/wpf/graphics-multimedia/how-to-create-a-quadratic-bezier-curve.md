---
title: 'Comment : créer une courbe de Bézier quadratique'
ms.date: 03/30/2017
helpviewer_keywords:
- Bezier curves [WPF], creating
- quadratic Bezier curves [WPF], creating
- graphics [WPF], quadratic Bezier curves
ms.assetid: cd8fca4a-504e-4fd8-92ea-2969065a6e02
ms.openlocfilehash: 8481a7e0e6d682a335b22ea6cdf73a23a9f155af
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085830"
---
# <a name="how-to-create-a-quadratic-bezier-curve"></a>Comment : créer une courbe de Bézier quadratique
Cet exemple montre comment créer une courbe de Bézier quadratique.  Pour créer une courbe de Bézier quadratique, utilisez le <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, et <xref:System.Windows.Media.QuadraticBezierSegment> classes.  
  
## <a name="example"></a>Exemple  
 Dans les exemples suivants, une courbe de Bézier quadratique est dessinée de (10,100) à (300,100). La courbe a un point de contrôle de (200,200).  
  
 [xaml]  
  
 Dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], vous pouvez utiliser la syntaxe d’attribut pour décrire un chemin d’accès.  
  
 [!code-xaml[GeometrySample#54](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#54)]  
  
 [xaml]  
  
 (Notez que cette syntaxe d’attribut crée en fait un <xref:System.Windows.Media.StreamGeometry>, une version légère d’une <xref:System.Windows.Media.PathGeometry>. (Pour plus d’informations, consultez la page [Syntaxe XAML pour les tracés](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md).)  
  
 Dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous pouvez également dessiner une courbe de Bézier quadratique à l’aide de la syntaxe d’élément objet. L'exemple suivant est équivalent à l’exemple [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] précédent.  
  
 [!code-xaml[GeometrySample#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 Cet exemple fait partie d’un exemple plus vaste ; pour l’exemple complet, consultez [Géométries, exemple](https://go.microsoft.com/fwlink/?LinkID=159989).  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un arc elliptique](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md)  
 [Créer une courbe de Bézier cubique](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)
