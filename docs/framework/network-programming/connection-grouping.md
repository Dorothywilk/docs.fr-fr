---
title: Regroupement de connexions
ms.date: 03/30/2017
helpviewer_keywords:
- Internet, connections
- connections [.NET Framework], grouping
- WebRequest class, connection grouping
- network resources, connections
- connection pooling
ms.assetid: 2ec502e8-4ba0-4c22-9410-f28eaf4eee63
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 5d7a13172c32d7ae47cbe290587ff7620e6060da
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47200865"
---
# <a name="connection-grouping"></a>Regroupement de connexions
Le regroupement de connexions associe des requêtes spécifiques au sein d’une application unique à un pool de connexions défini. Cela peut être requis par une application de couche intermédiaire qui se connecte à un serveur principal pour le compte d’un utilisateur et qui utilise un protocole d’authentification prenant en charge la délégation, tel que Kerberos, ou par une application de couche intermédiaire qui fournit ses propres informations d’identification, comme dans l’exemple ci-dessous. Par exemple, supposez qu’un utilisateur (Jean) visite un site web interne qui affiche des informations sur son salaire. Après avoir authentifié Jean, le serveur d’applications de couche intermédiaire utilise ses informations d’identification pour se connecter au serveur principal afin de récupérer des informations sur son salaire. Ensuite, Suzanne accède au site et demande à consulter les informations relatives à son salaire. Étant donné que l’application de couche intermédiaire a déjà établi une connexion à l’aide des informations d’identification de Jean, le serveur principal répond avec les informations relatives à Jean. Toutefois, si l’application assigne chaque requête envoyée au serveur principal à un groupe de connexions formé à partir du nom d’utilisateur, alors chaque utilisateur appartient à un pool de connexions distinct et ne peut pas partager accidentellement des informations d’authentification avec un autre utilisateur.  
  
 Pour assigner une requête à un groupe de connexions spécifique, vous devez affecter un nom à la propriété <xref:System.Net.WebRequest.ConnectionGroupName%2A> de votre <xref:System.Net.WebRequest> avant d’exécuter la requête.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des connexions](../../../docs/framework/network-programming/managing-connections.md)  
 [Guide pratique pour assigner des informations utilisateur aux connexions de groupe](../../../docs/framework/network-programming/how-to-assign-user-information-to-group-connections.md)
