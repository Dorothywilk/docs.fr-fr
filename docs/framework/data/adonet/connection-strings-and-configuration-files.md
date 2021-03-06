---
title: Chaînes de connexion et fichiers de configuration
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 37df2641-661e-407a-a3fb-7bf9540f01e8
ms.openlocfilehash: 8030c0323a2f742de19a4761e24c66294c6dd5d4
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865824"
---
# <a name="connection-strings-and-configuration-files"></a>Chaînes de connexion et fichiers de configuration
L'incorporation de chaînes de connexion dans le code de votre application peut entraîner des vulnérabilités de sécurité et des problèmes de maintenance. Les chaînes de connexion non chiffrées compilées dans le code source d’une application peuvent être affichées à l’aide de l’outil [Ildasm.exe (IL Disassembler)](../../../../docs/framework/tools/ildasm-exe-il-disassembler.md). En outre, si la chaîne de connexion change, votre application doit être recompilée. Pour ces raisons, nous vous recommandons de stocker les chaînes de connexion dans un fichier de configuration de l'application.  
  
## <a name="working-with-application-configuration-files"></a>Utilisation de fichiers de configuration de l'application  
 Les fichiers de configuration de l'application contiennent des paramètres spécifiques à une application particulière. Par exemple, une application ASP.NET peut avoir un ou plusieurs fichiers **web.config**, alors qu’une application Windows peut avoir un fichier **app.config** facultatif. Les fichiers de configuration partagent des éléments communs, bien que le nom et l'emplacement d'un fichier de configuration varient selon l'hôte de l'application.  
  
### <a name="the-connectionstrings-section"></a>Section connectionStrings  
 Les chaînes de connexion peuvent être stockées en tant que paires clé-valeur dans la section **connectionStrings** de l’élément **configuration** d’un fichier de configuration de l’application. Les éléments enfants incluent **add**, **clear** et **remove**.  
  
 Le fragment de fichier de configuration ci-dessous illustre le schéma et la syntaxe utilisés stocker une chaîne de connexion. L’attribut **name** est un nom que vous fournissez pour identifier de façon unique une chaîne de connexion afin qu’elle puisse être extraite au moment de l’exécution. **providerName** correspond au nom invariant du fournisseur de données .NET Framework qui figure dans le fichier machine.config.  
  
```xml  
<?xml version='1.0' encoding='utf-8'?>  
  <configuration>  
    <connectionStrings>  
      <clear />  
      <add name="Name"   
       providerName="System.Data.ProviderName"   
       connectionString="Valid Connection String;" />  
    </connectionStrings>  
  </configuration>  
```  
  
> [!NOTE]
>  Vous pouvez enregistrer une partie d'une chaîne de connexion dans un fichier de configuration et utiliser la classe <xref:System.Data.Common.DbConnectionStringBuilder> pour la compléter au moment de l'exécution. Cela est utile dans des scénarios où vous ne connaissez pas à l'avance les éléments de la chaîne de connexion ou lorsque vous ne voulez pas enregistrer des informations sensibles dans un fichier de configuration. Pour plus d’informations, consultez [Builders de chaînes de connexion](../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
### <a name="using-external-configuration-files"></a>Utilisation de fichiers de configuration externes  
 Les fichiers de configuration externes sont des fichiers distincts qui contiennent un fragment d'un fichier de configuration composé d'une section unique. Le fichier de configuration externe est ensuite référencé par le fichier de configuration principal. Le stockage de la section **connectionStrings** dans un fichier physique distinct est utile dans des situations où les chaînes de connexion peuvent être modifiées après le déploiement de l’application. Par exemple, le comportement ASP.NET standard consiste à redémarrer un domaine d'application lorsque les fichiers de configuration sont modifiés, ce qui entraîne la perte des informations d'état. Toutefois, la modification d'un fichier de configuration externe n'entraîne pas le redémarrage d'une application. Les fichiers de configuration externes ne sont pas limités à ASP.NET ; ils peuvent également être utilisés par des applications Windows. En outre, la sécurité et les autorisations d'accès aux fichiers permettent de limiter l'accès aux fichiers de configuration externes. L'utilisation de fichiers de configuration externes au moment de l'exécution est transparente et ne requiert aucun codage spécial.  
  
 Pour stocker des chaînes de connexion dans un fichier de configuration externe, créez un fichier distinct contenant seulement la section **connectionStrings**. N'incluez aucun élément, section ou attribut supplémentaire. L'exemple ci-dessous illustre la syntaxe pour un fichier de configuration externe.  
  
```xml  
<connectionStrings>  
  <add name="Name"   
   providerName="System.Data.ProviderName"   
   connectionString="Valid Connection String;" />  
</connectionStrings>  
```  
  
 Dans le fichier de configuration principal de l’application, vous utilisez l’attribut **configSource** pour spécifier le nom complet et l’emplacement du fichier externe. Cet exemple fait référence à un fichier de configuration externe nommé `connections.config`.  
  
```xml  
<?xml version='1.0' encoding='utf-8'?>  
<configuration>  
    <connectionStrings configSource="connections.config"/>  
</configuration>  
```  
  
## <a name="retrieving-connection-strings-at-run-time"></a>Extraction de chaînes de connexion au moment de l'exécution  
 Le .NET Framework 2.0 a introduit de nouvelles classes dans l'espace de noms <xref:System.Configuration> afin de simplifier l'extraction des chaînes de connexion à partir des fichiers de configuration au moment de l'exécution. Vous pouvez extraire par programme une chaîne de connexion en utilisant son nom ou le nom du fournisseur.  
  
> [!NOTE]
>  Le fichier **machine.config** contient également une section **connectionStrings**, qui contient les chaînes de connexion utilisées par Visual Studio. Lors de l’extraction de chaînes de connexion à l’aide du nom du fournisseur à partir du fichier **app.config** dans une application Windows, les chaînes de connexion figurant dans **machine.config** sont chargées les premières, avant les entrées figurant dans **app.config**. L’ajout de **clear** immédiatement après l’élément **connectionStrings** supprime toutes les références héritées de la structure de données en mémoire, de sorte que seules les chaînes de connexion définies dans le fichier **app.config** local sont prises en compte.  
  
### <a name="working-with-the-configuration-classes"></a>Utilisation des classes de configuration  
 À partir du .NET Framework 2.0, <xref:System.Configuration.ConfigurationManager>est utilisé lors de l'utilisation de fichiers de configuration sur l'ordinateur local, pour remplacer la <xref:System.Configuration.ConfigurationSettings> déconseillée. <xref:System.Web.Configuration.WebConfigurationManager> permet d'utiliser des fichiers de configuration ASP.NET. Il est conçu pour fonctionner avec les fichiers de configuration sur un serveur web et il permet un accès par programmation à des sections des fichiers de configuration telles que **system.web**.  
  
> [!NOTE]
>  L'accès aux fichiers de configuration au moment de l'exécution exige d'accorder des autorisations à l'appelant ; les autorisations requises dépendent du type d'application, du fichier de configuration et de l'emplacement. Pour plus d’informations, consultez [Utilisation des classes de configuration](https://msdn.microsoft.com/library/98d2b386-baf6-4a17-974b-76e3b4c87acc) et <xref:System.Web.Configuration.WebConfigurationManager> pour les applications ASP.NET, et <xref:System.Configuration.ConfigurationManager> pour les applications Windows.  
  
 Vous pouvez utiliser <xref:System.Configuration.ConnectionStringSettingsCollection> pour extraire les chaînes de connexion à partir des fichiers de configuration de l'application. Il contient une collection d’objets <xref:System.Configuration.ConnectionStringSettings>, dont chacun représente une entrée unique dans la section **connectionStrings**. Ses propriétés correspondent aux attributs des chaînes de connexion, ce qui vous permet d'extraire une chaîne de connexion en spécifiant son nom ou le nom du fournisseur.  
  
|Propriété|Description|  
|--------------|-----------------|  
|<xref:System.Configuration.ConnectionStringSettings.Name%2A>|Nom de la chaîne de connexion. Correspond à l’attribut **name**.|  
|<xref:System.Configuration.ConnectionStringSettings.ProviderName%2A>|Nom complet du fournisseur. Correspond à l’attribut **providerName**.|  
|<xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A>|Chaîne de connexion Correspond à l’attribut **connectionString**.|  
  
### <a name="example-listing-all-connection-strings"></a>Exemple : répertorier toutes les chaînes de connexion  
 Cet exemple itère au sein de la collection `ConnectionStringSettings` et affiche les propriétés <xref:System.Configuration.ConnectionStringSettings.Name%2A>, <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> et <xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A> dans la fenêtre de console.  
  
> [!NOTE]
>  Le fichier System.Configuration.dll n'est pas inclus dans tous les types de projets et vous pouvez être amené à définir une référence à ce fichier afin d'utiliser les classes de configuration. Le nom et l'emplacement d'un fichier de configuration particulier de l'application varient selon le type d'application et le processus d'hébergement.  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfig#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfig/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-name"></a>Exemple : extraction d'une chaîne de connexion à l'aide de son nom  
 Cet exemple montre comment extraire une chaîne de connexion à partir d'un fichier de configuration en spécifiant son nom. Le code crée un objet <xref:System.Configuration.ConnectionStringSettings>, en faisant correspondre le paramètre d'entrée fourni au nom <xref:System.Configuration.ConfigurationManager.ConnectionStrings%2A>. Si aucun nom correspondant n'est trouvé, la fonction retourne `null` (`Nothing` en Visual Basic).  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByName#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByName/VB/source.vb#1)]  
  
### <a name="example-retrieving-a-connection-string-by-provider-name"></a>Exemple : extraction d'une chaîne de connexion à l'aide du nom du fournisseur  
 Cet exemple montre comment extraire une chaîne de connexion en spécifiant le nom invariant du fournisseur au format *System.Data.ProviderName*. Le code itère au sein de <xref:System.Configuration.ConnectionStringSettingsCollection> et retourne la chaîne de connexion du premier <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> trouvé. Si le nom du fournisseur est introuvable, la fonction retourne `null` (`Nothing` en Visual Basic).  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="encrypting-configuration-file-sections-using-protected-configuration"></a>Chiffrement de sections de fichier de configuration à l'aide d'une configuration protégée  
 ASP.NET 2.0 a introduit une nouvelle fonctionnalité, appelée *configuration protégée*, qui vous permet de chiffrer les informations sensibles dans un fichier de configuration. Bien qu'elle ait été conçu à l'origine pour les applications ASP.NET, la configuration protégée peut également servir à chiffrer les sections des fichiers de configuration dans les applications Windows. Pour une description détaillée des fonctionnalités de configuration protégée, consultez [Chiffrement des informations de configuration à l’aide de la configuration protégée](https://msdn.microsoft.com/library/51cdfe5b-9d82-458c-94ff-c551c4f38ed1).  
  
 Le fragment de fichier de configuration suivant illustre la section **connectionStrings** après le chiffrement. Le **configProtectionProvider** spécifie le fournisseur de configuration protégée pour chiffrer et déchiffrer les chaînes de connexion. La section **EncryptedData** contient le texte de chiffrement.  
  
```xml  
<connectionStrings configProtectionProvider="DataProtectionConfigurationProvider">  
  <EncryptedData>  
    <CipherData>  
      <CipherValue>AQAAANCMnd8BFdERjHoAwE/Cl+sBAAAAH2... </CipherValue>  
    </CipherData>  
  </EncryptedData>  
</connectionStrings>  
```  
  
 Quand la chaîne de connexion chiffrée est extraite au moment de l’exécution, le .NET Framework utilise le fournisseur spécifié pour déchiffrer **CipherValue** et le tenir à la disposition de votre application. Il est inutile d'écrire du code supplémentaire pour gérer le processus de déchiffrement.  
  
### <a name="protected-configuration-providers"></a>Fournisseurs de configuration protégée  
 Les fournisseurs de configuration protégée sont enregistrés dans la section **configProtectedData** du fichier **machine.config** sur l’ordinateur local, comme indiqué dans le fragment suivant, qui représente les deux fournisseurs de configuration protégée inclus avec le .NET Framework. Les valeurs indiquées ici ont été tronquées pour améliorer la lisibilité.  
  
```xml  
<configProtectedData defaultProvider="RsaProtectedConfigurationProvider">  
  <providers>  
    <add name="RsaProtectedConfigurationProvider"   
      type="System.Configuration.RsaProtectedConfigurationProvider, ... />  
    <add name="DataProtectionConfigurationProvider"   
      type="System.Configuration.DpapiProtectedConfigurationProvider, ... />  
  </providers>  
</configProtectedData>  
```  
  
 Vous pouvez configurer des fournisseurs de configuration protégée supplémentaires en les ajoutant au fichier **machine.config**. Vous pouvez également créer votre propre fournisseur de configuration protégée en héritant de la classe de base abstraite <xref:System.Configuration.ProtectedConfigurationProvider>. Le tableau suivant décrit les deux fichiers de configuration inclus avec le .NET Framework.  
  
|Fournisseur|Description|  
|--------------|-----------------|  
|<xref:System.Configuration.RsaProtectedConfigurationProvider>|Utilise l'algorithme de chiffrement RSA pour chiffrer et déchiffrer des données. L'algorithme RSA peut être utilisé pour le chiffrement de clé publique et les signatures numériques. Il est également appelé « clé publique » ou chiffrement asymétrique, car il utilise deux clés différentes. Vous pouvez utiliser l’[Outil d’inscription IIS ASP.NET (aspnet_regiis.exe)](https://msdn.microsoft.com/library/6491c41e-e2b0-481f-9863-db3614d5f96b) pour chiffrer des sections dans un fichier Web.config et gérer les clés de chiffrement. ASP.NET déchiffre le fichier de configuration lorsqu'il traite le fichier. L'identité de l'application ASP.NET doit disposer d'un accès à la clé de chiffrement utilisée pour chiffrer et déchiffrer les sections chiffrées.|  
|<xref:System.Configuration.DpapiProtectedConfigurationProvider>|Utilise l'API de protection de données (DPAPI) Windows pour chiffrer les sections de configuration. Il utilise les services de chiffrement intégrés de Windows et peut être configuré pour une protection spécifique à un ordinateur ou spécifique à un compte d'utilisateur. La protection spécifique à un ordinateur est utile pour plusieurs applications sur le même serveur qui doivent partager des informations. La protection spécifique à un compte d'utilisateur peut être utilisée avec des services qui s'exécutent avec une identité d'utilisateur spécifique, telle qu'un environnement d'hébergement partagé. Chaque application s'exécute sous une identité différente qui restreint l'accès aux ressources telles que les fichiers et les bases de données.|  
  
 Les deux fournisseurs offrent un chiffrement renforcé des données. Cependant, si vous prévoyez d'utiliser le même fichier de configuration chiffré sur plusieurs serveurs, comme une batterie de serveurs Web, seul `RsaProtectedConfigurationProvider` vous permet d'exporter les clefs de chiffrement utilisées pour chiffrer les données et les importer sur un autre serveur. Pour plus d’informations, consultez [Importation et exportation des conteneurs de clé RSA de la configuration protégée](https://msdn.microsoft.com/library/f3022b39-f17f-48c1-b067-025eab0ce8bc).  
  
### <a name="using-the-configuration-classes"></a>Utilisation des classes de configuration  
 L'espace de noms <xref:System.Configuration> fournit des classes pour utiliser des paramètres de configuration par programme. La classe <xref:System.Configuration.ConfigurationManager> fournit un accès aux fichiers de configuration d'ordinateur, d'application et d'utilisateur. Si vous créez une application ASP.NET, vous pouvez utiliser la classe <xref:System.Web.Configuration.WebConfigurationManager>, qui fournit la même fonctionnalité tout en vous permettant également d’accéder à des paramètres qui sont uniques aux applications ASP.NET, comme celles qui se trouvent dans **\<system.web>**.  
  
> [!NOTE]
>  L'espace de noms <xref:System.Security.Cryptography> contient des classes qui fournissent des options supplémentaires pour le chiffrement et déchiffrement de données. Utilisez ces classes si vous avez besoin de services de chiffrement qui ne sont pas disponibles via la configuration protégée. Certaines de ces classes sont des wrappers pour l'interface Microsoft CryptoAPI non managée, tandis que d'autres ne sont purement que des implémentations managées. Pour plus d’informations, consultez [Services de cryptographie](https://msdn.microsoft.com/library/68a1e844-c63c-44af-9247-f6716eb23781).  
  
### <a name="appconfig-example"></a>Exemple App.config  
 Cet exemple montre comment basculer le chiffrement de la section **connectionStrings** dans un fichier **app.config** pour une application Windows. Dans cet exemple, la procédure prend le nom de l’application en tant qu’argument, par exemple, « MyApplication.exe ». Le fichier **app.config** est ensuite chiffré et copié dans le dossier qui contient le fichier exécutable sous le nom « MyApplication.exe.config ».  
  
> [!NOTE]
>  La chaîne de connexion peut uniquement être déchiffrée sur l'ordinateur sur lequel elle a été chiffrée.  
  
 Le code utilise la méthode <xref:System.Configuration.ConfigurationManager.OpenExeConfiguration%2A> pour ouvrir le fichier **app.config** à des fins de modification, puis la méthode <xref:System.Configuration.ConfigurationManager.GetSection%2A> retourne la section **connectionStrings**. Le code vérifie ensuite la propriété <xref:System.Configuration.SectionInformation.IsProtected%2A>, en appelant le <xref:System.Configuration.SectionInformation.ProtectSection%2A> pour chiffrer la section si elle n'est pas chiffrée. La méthode <xref:System.Configuration.SectionInformation.UnprotectSection%2A> est appelée pour déchiffrer la section. La méthode <xref:System.Configuration.Configuration.Save%2A> termine l'opération et enregistre les modifications.  
  
> [!NOTE]
>  Vous devez définir une référence à `System.Configuration.dll` dans votre projet pour le code à exécuter.  
  
 [!code-csharp[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStrings.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStrings.Encrypt/VB/source.vb#1)]  
  
### <a name="webconfig-example"></a>Exemple Web.config  
 Cet exemple utilise la méthode <xref:System.Web.Configuration.WebConfigurationManager.OpenWebConfiguration%2A> de `WebConfigurationManager`. Notez que dans ce cas vous pouvez fournir le chemin relatif au fichier **Web.config** à l’aide d’un tilde. Le code requiert une référence à la classe `System.Web.Configuration`.  
  
 [!code-csharp[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringsWeb.Encrypt#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringsWeb.Encrypt/VB/source.vb#1)]  
  
 Pour plus d’informations sur la sécurisation des applications ASP.NET, consultez [Sécurisation de sites Web ASP.NET](https://msdn.microsoft.com/library/04b37532-18d9-40b4-8e5f-ee09a70b311d) et la [Présentation des pratiques de sécurité ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=59997) dans le Centre de développement ASP.NET.  
  
## <a name="see-also"></a>Voir aussi  
 [Générateurs de chaînes de connexion](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 [Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 [Utilisation des classes de configuration](https://msdn.microsoft.com/library/98d2b386-baf6-4a17-974b-76e3b4c87acc)  
 [Configuration d'applications](../../../../docs/framework/configure-apps/index.md)  
 [Administration de site web ASP.NET](https://msdn.microsoft.com/library/1298034b-5f7d-464d-abd1-ad9e6b3eeb7e)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
