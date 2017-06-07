---
title: "S&#233;curisation des messages &#224; l&#39;aide de la s&#233;curit&#233; de message | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a17ebe67-836b-4c52-9a81-2c3d58e225ee
caps.latest.revision: 16
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 16
---
# S&#233;curisation des messages &#224; l&#39;aide de la s&#233;curit&#233; de message
Cette section présente la sécurité de message [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] lors de l'utilisation de <xref:System.ServiceModel.NetMsmqBinding>.  
  
> [!NOTE]
>  Avant de lire cette rubrique, il est recommandé de lire [Concepts relatifs à la sécurité](../../../../docs/framework/wcf/feature-details/security-concepts.md).  
  
 L'illustration suivante fournit un modèle conceptuel de la communication mise en file d'attente à l'aide de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].Cette illustration et la terminologie permettent d'expliquer  
  
 les concepts de sécurité de transport.  
  
 ![Diagramme des applications en file d'attente](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "Distributed\-Queue\-Figure")  
  
 Lors de l'envoi de messages mis en file d'attente à l'aide de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], le message [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est joint en tant que corps du message Message Queuing \(MSMQ\).Alors que la sécurité de transport sécurise le message MSMQ entier, la sécurité de message \(ou SOAP\) sécurise uniquement le corps du message MSMQ.  
  
 Le concept clé de la sécurité de message est que le client sécurise le message pour l'application réceptrice \(service\), contrairement à la sécurité de transport où le client sécurise le message pour la file d'attente cible.Ainsi, MSMQ ne joue aucun rôle lors de la sécurisation du message [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à l'aide de la sécurité de message.  
  
 La sécurité de message [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ajoute des en\-têtes de sécurité au message [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui s'intègrent avec les infrastructures de sécurité existantes, telles qu'un certificat ou le protocole Kerberos.  
  
## Type d'informations d'identification de message  
 Grâce à la sécurité de message, le service et le client peuvent présenter des informations d'identification pour s'authentifier mutuellement.Vous pouvez sélectionner la sécurité de message en définissant le mode <xref:System.ServiceModel.NetMsmqBinding.Security%2A> sur `Message` ou sur `Both` \(c'est\-à\-dire en utilisant la sécurité de transport et la sécurité de message\).  
  
 Le service peut utiliser la propriété <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> pour inspecter les informations d'identification permettant d'authentifier le client.Elle peut également être utilisée pour des vérifications d'autorisation supplémentaires que le service choisit d'implémenter.  
  
 Cette section présente les différents types d'informations d'identification et explique comment les utiliser avec les files d'attente.  
  
### Certificat  
 Le type d'informations d'identification de certificat utilise un certificat X.509 pour identifier le service et le client.  
  
 Dans un scénario classique, un certificat valide est émis pour le client et le service par une autorité de certification de confiance.Lorsque la connexion est établie, le client authentifie la validité du service à l'aide du certificat du service pour décider s'il peut faire confiance au service.De la même façon, le service utilise le certificat du client pour valider l'approbation du client.  
  
 Étant donné la nature déconnectée des files d'attente, le client et le service peuvent ne pas être en ligne au même moment.Par conséquent, le client et le service doivent échanger des certificats hors bande.En particulier, le client, du fait qu'il détient le certificat du service \(lequel peut être chaîné à une autorité de certification\) dans son magasin approuvé, doit croire qu'il communique avec le service correct.Pour authentifier le client, le service utilise le certificat X.509 joint au message pour le mettre en correspondance avec le certificat dans son magasin afin de vérifier l'authenticité du client.De nouveau, le certificat doit être chaîné à une autorité de certification.  
  
 Sur un ordinateur exécutant Windows, les certificats sont conservés dans plusieurs types de magasins.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] les différents magasins, consultez [Magasins de certificats](http://go.microsoft.com/fwlink/?LinkId=87787).  
  
### Windows  
 Le type d'informations d'identification de message Windows utilise le protocole Kerberos.  
  
 Le protocole Kerberos est un mécanisme de sécurité qui authentifie les utilisateurs sur un domaine et permet aux utilisateurs authentifiés d'établir des contextes sécurisés avec d'autres entités sur un domaine.  
  
 Le problème lié à l'utilisation du protocole Kerberos pour la communication mise en file d'attente est que les tickets qui contiennent l'identité du client que le centre de distribution de clés distribue sont relativement éphémères.Une *durée de vie* est associée au ticket Kerberos qui indique la validité du ticket.Ainsi, étant donné la latence élevée, vous ne pouvez pas être sûr que le jeton est encore valide pour le service qui authentifie le client.  
  
 Notez que lors de l'utilisation de ce type d'informations d'identification, le service doit s'exécuter sous le compte SERVICE.  
  
 Le protocole Kerberos est utilisé par défaut lors du choix des informations d'identification d'un message.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Étude de Kerberos, le protocole de sécurité distribuée dans Windows 2000](http://go.microsoft.com/fwlink/?LinkId=87790) \(page pouvant être en anglais\).  
  
### Username Password  
 À l'aide de cette propriété, le client peut s'authentifier auprès du serveur en utilisant un mot de passe de nom d'utilisateur dans l'en\-tête de sécurité du message.  
  
### IssuedToken  
 Le client peut utiliser le service de jeton de sécurité pour émettre un jeton qui peut ensuite être joint au message pour que le service authentifie le client.  
  
## Utilisation de la sécurité de transport et de message  
 Lorsque vous utilisez à la fois la sécurité de transport et la sécurité de message, le certificat utilisé pour sécuriser le message au niveau du transport et du message SOAP doit être le même.  
  
## Voir aussi  
 [Sécurisation des messages à l'aide de la sécurité de transport](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)   
 [Message Security over Message Queuing](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)   
 [Concepts relatifs à la sécurité](../../../../docs/framework/wcf/feature-details/security-concepts.md)   
 [Sécurisation des services et des clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)