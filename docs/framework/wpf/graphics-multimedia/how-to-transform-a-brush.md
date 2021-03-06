---
title: 'Comment : transformer un pinceau'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], rotating contents
- brushes [WPF], Transform property
- rotating contents of brushes [WPF]
ms.assetid: ebada2f9-f01f-4863-9ea2-c2e4e51610f1
ms.openlocfilehash: ebc8d4c6cb36d76b70691cce183f9e6070d19822
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507045"
---
# <a name="how-to-transform-a-brush"></a>Comment : transformer un pinceau
Cet exemple montre comment transformer <xref:System.Windows.Media.Brush> objets à l’aide de leurs deux propriétés de transformation : <xref:System.Windows.Media.Brush.RelativeTransform%2A> et <xref:System.Windows.Media.Brush.Transform%2A>.  
  
 Les exemples suivants utilisent une <xref:System.Windows.Media.RotateTransform> pour faire pivoter le contenu d’un <xref:System.Windows.Media.ImageBrush> de 45 degrés.  
  
 L’illustration suivante montre le <xref:System.Windows.Media.ImageBrush> sans un <xref:System.Windows.Media.RotateTransform>, avec le <xref:System.Windows.Media.RotateTransform> appliqué à la <xref:System.Windows.Media.Brush.RelativeTransform%2A> propriété et avec le <xref:System.Windows.Media.RotateTransform> appliqué à la <xref:System.Windows.Media.Brush.Transform%2A> propriété.  
  
 ![Paramètres de Brush RelativeTransform et Transform](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
## <a name="example"></a>Exemple  
 Le premier exemple applique un <xref:System.Windows.Media.RotateTransform> à la <xref:System.Windows.Media.Brush.RelativeTransform%2A> propriété d’un <xref:System.Windows.Media.ImageBrush>. Le <xref:System.Windows.Media.RotateTransform.CenterX%2A> et <xref:System.Windows.Media.RotateTransform.CenterY%2A> propriétés d’un <xref:System.Windows.Media.RotateTransform> de l’objet sont toutes deux définies sur 0,5, ce qui est la coordonnée relative du point central de ce contenu. Par conséquent, le <xref:System.Windows.Media.ImageBrush> contenu pivote autour de son centre.  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 Le deuxième exemple applique également une <xref:System.Windows.Media.RotateTransform> à un <xref:System.Windows.Media.ImageBrush>; Toutefois, cet exemple utilise le <xref:System.Windows.Media.Brush.Transform%2A> propriété au lieu du <xref:System.Windows.Media.Brush.RelativeTransform%2A> propriété.  
  
 Pour faire pivoter le pinceau autour de son centre, l’exemple définit le <xref:System.Windows.Media.RotateTransform.CenterX%2A> et <xref:System.Windows.Media.RotateTransform.CenterY%2A> propriétés de la <xref:System.Windows.Media.RotateTransform> objet sur des coordonnées absolues. Étant donné que le pinceau peint un rectangle de 175 par 90 pixels, le point central du rectangle est (87,5, 45).  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 Pour obtenir une description de la façon dont <xref:System.Windows.Media.Brush.RelativeTransform%2A> et <xref:System.Windows.Media.Brush.Transform%2A> propriétés, consultez le [vue d’ensemble de la Transformation de pinceau](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md).  
  
 Pour l’exemple complet, consultez [Exemples de pinceaux](https://go.microsoft.com/fwlink/?LinkID=159973). Pour plus d’informations sur les pinceaux, consultez [Vue d’ensemble de la peinture avec des couleurs unies ou des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d'ensemble des transformations du pinceau](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md)  
 [Vue d’ensemble de la peinture avec des couleurs unies ou des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Vue d’ensemble des transformations](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
