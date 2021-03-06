---
title: Génération de classes de type de données à partir de XML
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: 6b38a0aea3101c70b3c3ec0c8feb4ee88018b64e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="generating-data-type-classes-from-xml"></a>Génération de classes de type de données à partir de XML
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] inclut une nouvelle fonctionnalité pour générer les classes de type de données XML. Cette rubrique explique comment générer automatiquement des types de données pour les flux RSS du Blog .NET.  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a>Obtention du code XML du RSS du Blog .NET de flux  
  
1.  Dans Internet Explorer, accédez à la [RSS du Blog .NET flux](https://blogs.msdn.microsoft.com/dotnet/feed/).  
  
2.  Avec le bouton droit de la page et sélectionnez **afficher la Source**.  
  
3.  Copiez le texte du flux en appuyant sur **Ctrl + A** pour sélectionner tout le texte, et **Ctrl + C** à copier.  
  
### <a name="creating-the-data-types"></a>Création des types de données  
  
1.  Ouvrez un fichier de code où le proxy doit être utilisé. Ce fichier doit faire partie d'un projet [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].  
  
2.  Placez le curseur dans un emplacement du fichier à l'extérieur des classes existantes.  
  
3.  Sélectionnez **modifier**, **Collage spécial**, **collez du code XML en tant que Classes**.  
  
4.  Classes appelées `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` et `rssChannelItemGuid` sont créés avec les membres nécessaires pour accéder aux éléments dans le flux RSS.  
  
### <a name="using-the-generated-classes"></a>Utilisation des classes générées  
  
1.  Une fois les classes générées, elles peuvent être utilisées dans le code comme toute autre classe. L'exemple suivant retourne une nouvelle instance de la classe `rssChannelImage`.  
  
    ```  
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
    ```
