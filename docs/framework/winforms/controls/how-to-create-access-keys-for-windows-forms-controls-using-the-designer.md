---
title: "Comment : créer des touches d'accès rapide pour les contrôles Windows Forms à l'aide du concepteur"
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4c374c4c-4ca9-4a68-ac96-9dc3ab0f518a
ms.openlocfilehash: d077de1636888f0e3b763344206692fee2cb2296
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502969"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls-using-the-designer"></a>Comment : créer des touches d'accès rapide pour les contrôles Windows Forms à l'aide du concepteur
Un *clé d’accès* est un caractère souligné dans le texte d’un menu, un élément de menu ou l’étiquette d’un contrôle tel qu’un bouton. Il permet à l’utilisateur « cliquer » sur un bouton en appuyant sur la touche ALT conjointement avec la clé d’accès prédéfinies. Par exemple, si un bouton exécute une procédure pour imprimer un formulaire et par conséquent son `Text` propriété est définie sur « Imprimer », ajoutant une esperluette (&) devant la lettre « P » a « P » être soulignées dans le texte du bouton au moment de l’exécution. L’utilisateur peut exécuter la commande associée au bouton en appuyant sur ALT + P. Vous ne pouvez avoir une clé d’accès pour un contrôle qui ne peut pas recevoir le focus.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-an-access-key-for-a-control"></a>Pour créer une clé d’accès pour un contrôle  
  
1.  Dans le **propriétés** fenêtre, définissez le `Text` propriété à une chaîne qui inclut une esperluette (&) avant la lettre qui sera la clé d’accès. Par exemple, pour définir la lettre « P » comme touche d’accès, tapez **& impression** dans la grille.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.Button>  
 [Guide pratique pour répondre à un clic du contrôle Button Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Guide pratique pour définir le texte affiché par un contrôle Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [Création d'étiquettes et de raccourcis pour les contrôles Windows Forms](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
