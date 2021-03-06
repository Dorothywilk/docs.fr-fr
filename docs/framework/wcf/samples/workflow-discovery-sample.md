---
title: Exemple Workflow Discovery
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: 1076e7045ca546fed7e6902f69406bfc002c4c26
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45964421"
---
# <a name="workflow-discovery-sample"></a>Exemple Workflow Discovery
Cet exemple montre comment rendre un service de workflow détectable et comment créer une activité de code personnalisée qui recherche un service particulier.  
  
## <a name="demonstrates"></a>Démonstrations  
 Activité de recherche de découverte et utilisation de workflow  
  
## <a name="discussion"></a>Discussion  
 Dans la première partie de l'exemple, un service de workflow est rendu détectable à l'aide de la configuration. La configuration peut également être utilisée pour appliquer convenablement le service avec des métadonnées personnalisées (telles que des portées). Sur le client, l'exemple utilise une activité de code personnalisée, qui utilise la découverte pour rechercher un service correspondant à un contrat particulier. L'activité de code produit un URI, utilisé ultérieurement par une activité d'envoi.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Cet exemple utilise des points de terminaison HTTP, qui doivent avoir les ACL appropriées d’URL à exécuter (consultez [configuration de HTTP et HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) pour plus d’informations). L'exécution de la commande suivante à partir d'une invite de commandes avec élévation de privilèges doit ajouter les ACL appropriées. Substituez vos domaine et nom d’utilisateur aux arguments suivants si votre interpréteur de commandes ne comprend pas le format variable.  
  
     **netsh http ajouter urlacl url =http://+:8000/ utilisateur = domaine %\\%UserName%**  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples de Windows Workflow Foundation (WF) pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples. Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
