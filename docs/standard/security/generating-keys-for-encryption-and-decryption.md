---
title: Génération de clés pour le chiffrement et le déchiffrement
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keys, encryption and decryption
- keys, asymmetric
- keys, symmetric
- encryption [.NET Framework], keys
- symmetric keys
- asymmetric keys [.NET Framework]
- cryptography [.NET Framework], keys
ms.assetid: c197dfc9-a453-4226-898d-37a16638056e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 839a04d8a06e782582705cf0d9ad92d2e2df6af6
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47173120"
---
# <a name="generating-keys-for-encryption-and-decryption"></a>Génération de clés pour le chiffrement et le déchiffrement
La création et la gestion des clés constituent une part importante du processus de chiffrement. Les algorithmes symétriques nécessitent la création d'une clé et d'un vecteur d'initialisation. La clé ne doit pas être divulguée aux personnes qui ne sont pas autorisées à déchiffrer vos données. Le vecteur d'initialisation peut être divulgué, mais doit être modifié à chaque session. Les algorithmes asymétriques nécessitent la création d'une clé publique et d'une clé privée. La clé publique peut être donnée à tout le monde. Toutefois, la clé privée ne doit être connue que de la partie chargée du déchiffrement des données chiffrées à l'aide de la clé publique. Cette section décrit comment générer et gérer des clés pour les algorithmes symétriques et asymétriques.  
  
## <a name="symmetric-keys"></a>Clés symétriques  
 Les classes de chiffrement symétrique fournies par .NET Framework nécessitent une clé et un nouveau vecteur d'initialisation pour chiffrer et déchiffrer les données. Quand vous créez une instance de l'une des classes de chiffrement symétrique managées à l'aide du constructeur par défaut, une nouvelle clé et un nouveau vecteur d'initialisation sont créés automatiquement. Toute personne que vous autorisez à déchiffrer vos données doit posséder la même clé et le même vecteur d'initialisation, et doit utiliser le même algorithme. En général, une nouvelle clé et un nouveau vecteur d'initialisation doivent être créés pour chaque session. Ni la clé, ni le vecteur d'initialisation ne doivent être stockés en vue d'être utilisés dans une session ultérieure.  
  
 Pour communiquer une clé symétrique et un vecteur d'initialisation à une partie distante, vous devez, en général, chiffrer la clé symétrique à l'aide du chiffrement asymétrique. L'envoi d'une clé non chiffrée vers un réseau non sécurisé est risqué, car toute personne qui intercepte la clé et le vecteur d'initialisation peut ensuite déchiffrer vos données. Pour plus d'informations sur l'échange de données à l'aide du chiffrement, consultez [Création d'un modèle de chiffrement](../../../docs/standard/security/creating-a-cryptographic-scheme.md).  
  
 L'exemple suivant illustre la création d'une nouvelle instance de la classe <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> qui implémente l'algorithme TripleDES.  
  
```vb  
Dim TDES As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
```  
  
```csharp  
TripleDESCryptoServiceProvider TDES = new TripleDESCryptoServiceProvider();  
```  
  
 Quand le code précédent est exécuté, une nouvelle clé et un nouveau vecteur d'initialisation sont générés, puis placés dans les propriétés **Key** et **IV** , respectivement.  
  
 Vous devrez parfois générer plusieurs clés. Dans ce cas, vous pouvez créer une instance d'une classe qui implémente un algorithme symétrique et ensuite créer une nouvelle clé et un nouveau vecteur d'initialisation en appelant les méthodes **GenerateKey** et **GenerateIV** . L'exemple de code suivant montre comment créer de nouvelles clés et de nouveaux vecteurs d'initialisation après la création d'une nouvelle instance de la classe de chiffrement asymétrique.  
  
```vb  
Dim TDES As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
TDES.GenerateIV()  
TDES.GenerateKey()  
```  
  
```csharp  
TripleDESCryptoServiceProvider TDES = new TripleDESCryptoServiceProvider();  
TDES.GenerateIV();  
TDES.GenerateKey();  
```  
  
 Quand le code précédent est exécuté, une clé et un vecteur d'initialisation sont générés quand la nouvelle instance de **TripleDESCryptoServiceProvider** est créée. Une autre clé et un autre vecteur d'initialisation sont créés quand les méthodes **GenerateKey** et **GenerateIV** sont appelées.  
  
## <a name="asymmetric-keys"></a>Clés asymétriques  
 .NET Framework fournit les classes <xref:System.Security.Cryptography.RSACryptoServiceProvider> et <xref:System.Security.Cryptography.DSACryptoServiceProvider> pour le chiffrement asymétrique. Ces classes créent une paire de clés publique/privée quand vous utilisez le constructeur par défaut pour créer une instance. Les clés asymétriques peuvent être stockées en vue d'être utilisées pour plusieurs sessions, ou bien être générées pour une session unique. La clé publique peut être connue de tous, contrairement à la clé privée qui ne doit être divulguée qu'à certaines personnes.  
  
 Une paire de clés publique/privée est générée chaque fois qu'une nouvelle instance d'une classe d'algorithme asymétrique est créée. Après la création d'une nouvelle instance de la classe, les informations de clé peuvent être extraites à l'aide de deux méthodes :  
  
-   La méthode <xref:System.Security.Cryptography.RSA.ToXmlString%2A> , qui retourne une représentation XML des informations de clé.  
  
-   La méthode <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A> qui retourne une structure <xref:System.Security.Cryptography.RSAParameters> qui contient les informations de clé.  
  
 Les deux méthodes acceptent une valeur booléenne qui indique s'il faut retourner uniquement les informations concernant la clé publique ou retourner les informations concernant la clé publique et la clé privée. Une classe **RSACryptoServiceProvider** peut être initialisée à la valeur d'une structure **RSAParameters** à l'aide de la méthode <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> .  
  
 Les clés privées asymétriques ne doivent jamais être stockées textuellement ou en texte brut sur l'ordinateur local. Si vous avez besoin de stocker une clé privée, vous devez utiliser un conteneur de clé. Pour plus d’informations sur le stockage d’une clé privée dans un conteneur de clé, consultez [Comment : stocker des clés asymétriques dans un conteneur de clé](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).  
  
 L'exemple de code suivant crée une nouvelle instance de la classe **RSACryptoServiceProvider** , en créant une paire de clés publique/privée et en enregistrant les informations de clé publique dans une structure **RSAParameters** .  
  
```vb  
'Generate a public/private key pair.  
Dim RSA as RSACryptoServiceProvider = new RSACryptoServiceProvider()  
'Save the public key information to an RSAParameters structure.  
Dim RSAKeyInfo As RSAParameters = RSA.ExportParameters(false)  
```  
  
```csharp  
//Generate a public/private key pair.  
RSACryptoServiceProvider RSA = new RSACryptoServiceProvider();  
//Save the public key information to an RSAParameters structure.  
RSAParameters RSAKeyInfo = RSA.ExportParameters(false);  
```  
  
## <a name="see-also"></a>Voir aussi

- [Chiffrement de données](../../../docs/standard/security/encrypting-data.md)  
- [Déchiffrement de données](../../../docs/standard/security/decrypting-data.md)  
- [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md)  
- [Comment : stocker des clés asymétriques dans un conteneur de clés](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md)
