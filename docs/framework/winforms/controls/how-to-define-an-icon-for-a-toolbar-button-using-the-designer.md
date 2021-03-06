---
title: "Comment : définir une icône pour un bouton ToolBar à l'aide du concepteur"
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- buttons [Windows Forms], images
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: d848f38e-67f2-49d4-8e88-01c845c06c02
ms.openlocfilehash: f26e21d824420fc4ff0480de21f260309c5c2e11
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43856606"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a>Comment : définir une icône pour un bouton ToolBar à l'aide du concepteur
> [!NOTE]
>  Le contrôle <xref:System.Windows.Forms.ToolStrip> remplace le contrôle <xref:System.Windows.Forms.ToolBar> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.ToolBar> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  
  
 <xref:System.Windows.Forms.ToolBar> boutons sont en mesure d’afficher des icônes pour faciliter l’identification par les utilisateurs. Cela s’effectue via l’ajout d’images à le <xref:System.Windows.Forms.ImageList> composant et son association avec la <xref:System.Windows.Forms.ToolBar> contrôle.  
  
 La procédure suivante nécessite un **Windows Application** projet avec un formulaire contenant un <xref:System.Windows.Forms.ToolBar> contrôle et un <xref:System.Windows.Forms.ImageList> composant. Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’Application Windows](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a>Pour définir une icône pour un bouton de barre d’outils au moment du design  
  
1.  Ajouter des images à le <xref:System.Windows.Forms.ImageList> composant. Pour plus d’informations, consultez [Comment : ajouter ou supprimer des Images ImageList avec le concepteur](../../../../docs/framework/winforms/controls/how-to-add-or-remove-imagelist-images-with-the-designer.md).  
  
2.  Sélectionnez le <xref:System.Windows.Forms.ToolBar> contrôle sur votre formulaire.  
  
3.  Dans le **propriétés** fenêtre, définissez la <xref:System.Windows.Forms.ToolBar> du contrôle <xref:System.Windows.Forms.ToolBar.ImageList%2A> propriété le <xref:System.Windows.Forms.ImageList> composant.  
  
4.  Cliquez sur le <xref:System.Windows.Forms.ToolBar> du contrôle <xref:System.Windows.Forms.ToolBar.Buttons%2A> propriété pour le sélectionner, puis cliquez sur le bouton de sélection (![d’écran de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) pour ouvrir la **Éditeur de collections ToolBarButton**.  
  
5.  Utilisez le **ajouter** pour ajouter des boutons à la <xref:System.Windows.Forms.ToolBar> contrôle.  
  
6.  Dans le **propriétés** fenêtre qui s’affiche dans le volet situé à droite de la **éditeur de collections ToolBarButton**, définissez le <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> propriété de chaque bouton de barre d’outils à une des valeurs dans la liste, qui est dessiné à partir d’images ajoutées à la <xref:System.Windows.Forms.ImageList> composant.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.ToolBar>  
 [Guide pratique pour déclencher des événements de menu pour les boutons de barre d’outils](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 [ToolBar, contrôle](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)  
 [ImageList, composant](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
