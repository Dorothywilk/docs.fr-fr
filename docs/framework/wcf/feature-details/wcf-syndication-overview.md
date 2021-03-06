---
title: Vue d'ensemble de la syndication WCF
ms.date: 03/30/2017
ms.assetid: af6d4c39-e5e8-4099-aee6-5261feff9107
ms.openlocfilehash: cba14edc5743966c53f23b3dbf965c5472ed2702
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48837184"
---
# <a name="wcf-syndication-overview"></a>Vue d'ensemble de la syndication WCF
Windows Communication Foundation (WCF) prend en charge pour l’exposition des flux de syndication à partir d’un service WCF. La syndication est un mécanisme d'intégration d'application par lequel un serveur expose des données d'application dans un format interopérable appelé « flux ». Un flux est une collection de données d’application incluant des métadonnées (titre, auteur, URL et autres métadonnées) au niveau du flux et une série d’éléments de flux. Dans le flux, les éléments de flux sont habituellement ordonnés par ordre chronologique inverse. Un élément de flux se compose d'un jeu standard de métadonnées au niveau de l'élément (titre, URL, date de création, catégorie et autres métadonnées au niveau de l'élément) et une quantité arbitraire de données d'application spécifiques. Les deux types courants de flux de syndication sont Syndication RSS (Really Simple) 2.0 et Atom 1.0, qui sont prises en charge par WCF.  
  
## <a name="object-model"></a>Modèle objet  
 WCF définit un ensemble de classes spécifiques à la syndication qui vous permettent d’utiliser des flux, les éléments de flux et les métadonnées associées de façon indépendante du format : <xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, <xref:System.ServiceModel.Syndication.SyndicationPerson>, <xref:System.ServiceModel.Syndication.SyndicationLink>et d’autres classes spécifiques à la syndication. WCF définit également des classes d’infrastructure qui s’appuient sur le modèle de programmation WCF REST pour fournir la prise en charge de syndication, y compris : <xref:System.ServiceModel.Syndication.Atom10FeedFormatter>, et <xref:System.ServiceModel.Syndication.Rss20FeedFormatter>. Les classes du module de formatage du flux prennent en charge la sérialisation du modèle objet depuis et vers RSS 2.0 et Atom 1.0.  
  
## <a name="scenarios"></a>Scénarios  
 Aujourd'hui, la syndication est généralement utilisée pour la création de blogs, où l'auteur du blog publie périodiquement des informations. Il peut s'agir de texte, d'images, de musique ou d'autres types d'informations. De nombreux journaux et magazines publient également des actualités ou des articles en utilisant la syndication. En s'abonnant à ce flux, un utilisateur peut se tenir à jour des nouvelles informations publiées par ces sites. Bien que la syndication soit généralement associée aux blogs et aux éditeurs, elle peut être utilisée avec toute application qui expose une collection d’informations ; par exemple, une base de données des bogues que vous souhaitez exposer à l’aide d’un flux de syndication. Vous pouvez créer un service WCF qui expose une opération appelée `CodeDefects`. Cette opération peut prendre un paramètre qui spécifie l'adresse de messagerie de la personne dont vous souhaitez récupérer les bogues. Un client peut utiliser l’URL suivante pour appeler l’opération : `http://someserver/bugDatabase/CodeDefects?user=johndoe`.  
  
## <a name="syndication-formats"></a>Formats de syndication  
 La plate-forme de syndication WCF prend en charge RSS 2.0 et Atom 1.0.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèle de programmation HTTP web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
