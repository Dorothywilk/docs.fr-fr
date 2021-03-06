---
title: 'Comment : définir le mode de sécurité'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Mode property
- WCF, security mode
- WCF, security
ms.assetid: 6e01dd9f-b5dd-4474-b24c-06e124de4ff7
author: BrucePerlerMS
ms.openlocfilehash: 0efa9ecbe384009cc8fc4735ec9fc3db8ed3ce59
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48841454"
---
# <a name="how-to-set-the-security-mode"></a>Comment : définir le mode de sécurité
Sécurité de Windows Communication Foundation (WCF) a trois modes de sécurité courants qui sont trouvent sur des liaisons plus prédéfinies : transport, message et « transport avec informations d’identification de message. » Il existe également deux modes supplémentaires propres à deux liaisons particulières. Il s'agit du mode « informations d'identification de transport uniquement » disponible sur la liaison <xref:System.ServiceModel.BasicHttpBinding> et du mode « les deux » disponible sur la liaison <xref:System.ServiceModel.NetMsmqBinding>. Cette rubrique traite essentiellement des trois principaux modes de sécurité : <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message> et <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.  
  
 Remarque : toutes les liaisons prédéfinies ne prennent pas nécessairement en charge chacun de ces modes. Cette rubrique, dans laquelle le mode est défini à l'aide des classes <xref:System.ServiceModel.WSHttpBinding> et <xref:System.ServiceModel.NetTcpBinding>, illustre comment définir les modes de sécurité à l'aide d'un programme ou dans la configuration.  
  
 Pour plus d’informations, reportez-vous à la section sécurité WCF, consultez [vue d’ensemble de la sécurité](../../../docs/framework/wcf/feature-details/security-overview.md), [sécurisation des Services](../../../docs/framework/wcf/securing-services.md), et [Securing Services and Clients](../../../docs/framework/wcf/feature-details/securing-services-and-clients.md). Pour plus d’informations sur le mode de transport et message, consultez [sécurité du Transport](../../../docs/framework/wcf/feature-details/transport-security.md) et [sécurité de Message](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).  
  
### <a name="to-set-the-security-mode-in-code"></a>Pour définir le mode de sécurité dans le code  
  
1.  Créez une instance de la classe de liaison en cours d’utilisation. Pour obtenir la liste de liaisons prédéfinies, consultez [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md). Cet exemple de code crée une instance de la classe <xref:System.ServiceModel.WSHttpBinding>.  
  
2.  Définissez la propriété `Mode` de l'objet retourné par la propriété `Security`.  
  
     [!code-csharp[c_SettingSecurityMode#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#1)]
     [!code-vb[c_SettingSecurityMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#1)]  
  
     Vous pouvez également affecter la valeur message au mode, comme illustré dans l'exemple de code suivant.  
  
     [!code-csharp[c_SettingSecurityMode#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#2)]
     [!code-vb[c_SettingSecurityMode#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#2)]  
  
     Vous pouvez aussi affecter la valeur transport avec informations d'identification de message au mode, comme illustré dans l'exemple de code suivant.  
  
     [!code-csharp[c_SettingSecurityMode#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#3)]
     [!code-vb[c_SettingSecurityMode#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#3)]  
  
3.  Vous pouvez enfin définir le mode dans le constructeur de la liaison, comme illustré dans l’exemple de code suivant.  
  
     [!code-csharp[c_SettingSecurityMode#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#4)]
     [!code-vb[c_SettingSecurityMode#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#4)]  
  
## <a name="setting-the-clientcredentialtype-property"></a>Définition de la propriété ClientCredentialType  
 La définition de la propriété `ClientCredentialType` dépend de la valeur affectée au mode de sécurité. Par exemple, si vous utilisez la classe <xref:System.ServiceModel.WSHttpBinding> et affectez au mode la valeur `Transport` vous devez affecter à la propriété <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> de la classe <xref:System.ServiceModel.HttpTransportSecurity> une valeur appropriée.  
  
#### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a>Pour définir la propriété ClientCredentialType pour le mode de sécurité de niveau transport  
  
1.  Créez une instance de la liaison.  
  
2.  Affectez à la propriété `Mode` la valeur `Transport`.  
  
3.  Affectez à la propriété `ClientCredential` une valeur appropriée. L'exemple de code suivant affecte à la propriété la valeur `Windows`.  
  
     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]  
  
#### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a>Pour définir la propriété ClientCredentialType pour le mode de sécurité de niveau message  
  
1.  Créez une instance de la liaison.  
  
2.  Affectez à la propriété `Mode` la valeur `Message`.  
  
3.  Affectez à la propriété `ClientCredential` une valeur appropriée. L'exemple de code suivant affecte à la propriété la valeur `Certificate`.  
  
     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]  
  
#### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a>Pour définir le mode et la propriété ClientCredentialType dans la configuration  
  
1.  Ajouter un élément de liaison approprié à la [ \<liaisons >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) élément du fichier de configuration. L’exemple suivant ajoute un [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) élément.  
  
2.  Ajouter un `<binding>` élément et définissez son `name` attribut une valeur appropriée.  
  
3.  Ajoutez un élément `<security>`, puis affectez à l'attribut `mode` les valeurs `Message`, `Transport`ou `TransportWithMessageCredential`.  
  
4.  Si le mode a la valeur `Transport`, ajoutez un élément `<transport>` , puis affectez à l'attribut `clientCredential` une valeur appropriée.  
  
     L'exemple suivant affecte au mode la valeur `Transport"`, puis affecte à l'attribut `clientCredentialType` de l'élément `<transport>` la valeur `Windows"`.  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="TransportSecurity">  
        <security mode="Transport" >  
           <transport clientCredentialType = "Windows" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```  
  
     Vous pouvez également affecter au `security mode` la valeur `Message"`, suivie d'un élément `<"message">`. Cet exemple affecte au `clientCredentialType` la valeur `Certificate"`.  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="MessageSecurity">  
        <security mode="Message" >  
           <message clientCredentialType = "Certificate" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```  
  
     L'utilisation de la valeur <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> forme un cas à part, expliqué ci-dessous.  
  
### <a name="using-transportwithmessagecredential"></a>Utilisation de TransportWithMessageCredential  
 Lorsque vous affectez au mode de sécurité la valeur `TransportWithMessageCredential`, le mécanisme chargé d'offrir la sécurité de niveau transport dépend du transport utilisé. Par exemple, le protocole HTTP utilise la sécurité Secure Sockets Layer (SSL) sur HTTP, c'est-à-dire HTTPS. Par conséquent, la définition d'une propriété `ClientCredentialType` pour tout objet de sécurité de transport (tel que <xref:System.ServiceModel.HttpTransportSecurity>) sera sans effet.  En d'autres termes, vous pouvez uniquement définir la propriété `ClientCredentialType` de l'objet de sécurité de message (pour la liaison `WSHttpBinding`, il s'agit de l'objet <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>).  
  
 Pour plus d’informations, consultez [Comment : utiliser la sécurité Transport et les informations d’identification de Message](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour configurer un port avec un certificat SSL](../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [Guide pratique pour utiliser des informations d’identification de sécurité de transport et de message](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)  
 [Sécurité de transport](../../../docs/framework/wcf/feature-details/transport-security.md)  
 [Sécurité de message](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 [Vue d’ensemble de la sécurité](../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Liaisons fournies par le système](../../../docs/framework/wcf/system-provided-bindings.md)  
 [\<sécurité >](../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)  
 [\<sécurité >](../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)  
 [\<sécurité >](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
