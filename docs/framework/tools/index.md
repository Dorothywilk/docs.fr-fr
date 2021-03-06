---
title: Outils du .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- command line, .NET Framework tools
- .NET Framework, tools
- tools [.NET Framework]
- running .NET Framework tools
ms.assetid: a2ca532d-91f7-426a-9303-417c2ee1247c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 208dc3048b52cc895a5142a7686829390d1d4503
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44041484"
---
# <a name="net-framework-tools"></a>Outils du .NET Framework
Les outils du .NET Framework facilitent la création, le déploiement et la gestion d'applications et de composants qui ciblent le .NET Framework.  
  
La plupart des outils .NET Framework décrits dans cette section sont installés automatiquement avec Visual Studio. Pour télécharger Visual Studio, visitez la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).
  
 Vous pouvez exécuter tous les outils à partir de la ligne de commande, à l'exception de la visionneuse du cache d'assembly (Shfusion.dll). Vous devez accéder à Shfusion.dll à partir de l'Explorateur de fichiers.  
  
 Le meilleur moyen d'exécuter l'outil en ligne de commande consiste à utiliser l'invite de commandes développeur Visual Studio. Ces utilitaires vous permettent d’exécuter facilement les outils, sans naviguer jusqu’au dossier d’installation. Pour plus d'informations, consultez [Invites de commandes](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
> [!NOTE]
>  Certains outils sont spécifiques aux ordinateurs 32 bits ou aux ordinateurs 64 bits. Veillez à exécuter la version appropriée de l'outil pour votre ordinateur.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Al.exe (Assembly Linker)](../../../docs/framework/tools/al-exe-assembly-linker.md)  
 Génère un fichier qui possède un manifeste de l'assembly issu de modules ou de fichiers de ressources.  
  
 [Aximp.exe (importateur de contrôles Active X Windows Forms)](../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md)  
 Convertit les définitions de types d'une bibliothèque de types COM d'un contrôle ActiveX en contrôle Windows Forms.  
  
 [Caspol.exe (outil de stratégie de sécurité d’accès du code)](../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md)  
 Permet d'afficher et de configurer la stratégie de sécurité au niveau de l'ordinateur, de l'utilisateur et de l'entreprise. Dans le [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] et versions ultérieures, cet outil n’affecte pas la stratégie de sécurité d’accès du code (CAS), à moins que l’[élément \<legacyCasPolicy>](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) ait la valeur `true`. Pour plus d’informations, consultez [Changements en matière de sécurité](../../../docs/framework/security/security-changes.md).  
  
 [Cert2spc.exe (outil de test de certificat d’éditeur de logiciels)](../../../docs/framework/tools/cert2spc-exe-software-publisher-certificate-test-tool.md)  
 Crée un certificat SPC (Software Publisher's Certificate) à partir d'un ou plusieurs certificats X.509. Cet outil ne doit être utilisé qu'à des fins de test.  
  
 [Certmgr.exe (outil de gestionnaire de certificats)](../../../docs/framework/tools/certmgr-exe-certificate-manager-tool.md)  
 Gère les certificats, les listes de certificats de confiance (CTL) et les listes de révocation de certificats (CRL).  
  
 [Clrver.exe (outil CLR Version)](../../../docs/framework/tools/clrver-exe-clr-version-tool.md)  
 Rapporte toutes les versions installées du CLR (Common Runtime Language) sur l'ordinateur.  
  
 [CorFlags.exe (outil de conversion CorFlags)](../../../docs/framework/tools/corflags-exe-corflags-conversion-tool.md)  
 Vous permet de configurer la section CorFlags de l'en-tête d'une image exécutable portable (PE).  
  
 [Fuslogvw.exe (visionneuse du journal de liaison d’assembly)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md)  
 Affiche des informations sur les liaisons d'assembly pour vous aider à diagnostiquer ce qui empêche le .NET Framework de trouver l'assembly au moment de l'exécution.  
  
 [Gacutil.exe (outil Global Assembly Cache)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)  
 Vous permet de visualiser et de manipuler le contenu du Global Assembly Cache et du cache de téléchargement.  
  
 [Ilasm.exe (assembleur IL)](../../../docs/framework/tools/ilasm-exe-il-assembler.md)  
 Génère un fichier PE (exécutable portable) en langage IL (Intermediate Language). Vous pouvez exécuter le fichier exécutable obtenu pour déterminer si le langage IL fonctionne comme prévu.  
  
 [Ildasm.exe (désassembleur IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)  
 Utilise un fichier PE qui contient le code IL (Intermediate Language) et crée un fichier texte qu'il peut utiliser en entrée dans l'Assembleur IL (Ilasm.exe).  
  
 [Installutil.exe (outil Installer)](../../../docs/framework/tools/installutil-exe-installer-tool.md)  
 Permet d'installer et de désinstaller des ressources serveur en exécutant les composants d'installation d'un assembly spécifié. (Utilise les classes dans l'espace de noms <xref:System.Configuration.Install>.) Permet d'installer et de désinstaller des ressources serveur en exécutant les composants d'installation d'un assembly spécifié. (Utilise les classes dans l'espace de noms <xref:System.Configuration.Install>.)  
  
 [Lc.exe (License Compiler)](../../../docs/framework/tools/lc-exe-license-compiler.md)  
 Lit les fichiers texte qui contiennent des informations de licence et produit un fichier .licenses qui peut être incorporé en tant que ressource dans un exécutable du Common Language Runtime. Lit les fichiers texte qui contiennent des informations de licence et produit un fichier .licenses qui peut être incorporé en tant que ressource dans un exécutable du Common Language Runtime.  
  
 [Mage.exe (outil Manifest Generation and Editing)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md)  
 Permet de créer, de modifier et de signer des manifestes d'application et de déploiement. En tant qu'outil en ligne de commande, Mage.exe peut être exécuté à partir de scripts de commandes et d'autres applications Windows, notamment les applications ASP.NET.  
  
 [MageUI.exe (outil Manifest Generation and Editing, client graphique)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)  
 Prend en charge les mêmes fonctionnalités que l'outil en ligne de commande Mage.exe, mais utilise une interface utilisateur de type Windows. Prend en charge les mêmes fonctionnalités que l'outil en ligne de commande Mage.exe, mais utilise une interface utilisateur de type Windows.  
  
 [MDbg.exe (débogueur de ligne de commande du .NET Framework)](../../../docs/framework/tools/mdbg-exe.md)  
 Permet aux fournisseurs d'outils et aux développeurs d'applications de trouver et de corriger les bogues dans les programmes qui ont pour cible le Common Language Runtime du .NET Framework. Cet outil utilise l'API de débogage du runtime pour fournir des services de débogage.  
  
 [Mgmtclassgen.exe (générateur de classes de gestion fortement typées)](../../../docs/framework/tools/mgmtclassgen-exe.md)  
 Permet de générer une classe managée à liaison anticipée pour une classe Windows Management Instrumentation spécifiée (WMI).  
  
 [Mpgo.exe (outil d’optimisation guidée par profil managé)](../../../docs/framework/tools/mpgo-exe-managed-profile-guided-optimization-tool.md)  
 Vous permet d'ajuster les assemblys d'image native en utilisant des scénarios courants d'utilisateurs finaux. Mpgo.exe permet la génération et la consommation des données de profil pour les assemblys d’application d’image native (pas les assemblys .NET Framework) à l’aide de scénarios de formation sélectionnés par le développeur d’applications.  
  
 [Ngen.exe (générateur d’images natives)](../../../docs/framework/tools/ngen-exe-native-image-generator.md)  
 Améliore les performances des applications managées via l'utilisation d'images natives (fichiers qui contiennent le code machine spécifique au processeur compilé). Le runtime peut utiliser des images natives du cache plutôt que le compilateur juste-à-temps (JIT) pour compiler l'assembly d'origine.  
  
 [Peverify.exe (outil PEVerify)](../../../docs/framework/tools/peverify-exe-peverify-tool.md)  
 Permet de vérifier si votre code MSIL (Microsoft Intermediate Language) et les métadonnées associées satisfont aux exigences de cohérence des types. Permet de vérifier si votre code MSIL (Microsoft Intermediate Language) et les métadonnées associées satisfont aux exigences de cohérence des types.  
  
 [Regasm.exe (outil d’inscription d’assemblys)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md)  
 Lit les métadonnées dans un assembly et ajoute les entrées nécessaires au Registre. Cela permet aux clients COM d'apparaître en tant que classes .NET Framework.  
  
 [Regsvcs.exe (outil d’installation des services .NET)](../../../docs/framework/tools/regsvcs-exe-net-services-installation-tool.md)  
 Charge et enregistre un assembly, génère et installe une bibliothèque de types dans une application COM+ version 1.0 spécifiée et configure les services que vous avez ajoutés par programmation à une classe.  
  
 [Resgen.exe (Resource File Generator)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)  
 Convertit les fichiers texte (.txt ou .restext) et les fichiers .resx (format de ressources XML) en fichiers .resources binaires du Common Language Runtime qui peuvent être incorporés dans un exécutable binaire runtime ou compilés en assemblys satellites.  
  
 [SecAnnotate.exe (outil .NET Security Annotator)](../../../docs/framework/tools/secannotate-exe-net-security-annotator-tool.md)  
 Identifie les parties SecurityCritical et SecuritySafeCritical d'un assembly. Identifie les parties `SecurityCritical` et `SecuritySafeCritical` d'un assembly.  
  
 [SignTool.exe (outil de signature)](../../../docs/framework/tools/signtool-exe.md)  
 Signe numériquement les fichiers, vérifie les signatures dans les fichiers et insère un horodatage dans les fichiers.  
  
 [Sn.exe (outil Strong Name)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
 Facilite la création d'assemblys avec des noms forts. Cet outil fournit des options de gestion des clés, de génération des signatures et de vérification des signatures.  
  
 [SOS.dll (extension de débogage SOS)](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md)  
 Vous aide à déboguer des programmes managés dans le débogueur WinDbg.exe et dans Visual Studio en fournissant des informations sur l'environnement interne du CLR (Common Language Runtime).  
  
 [SqlMetal.exe (outil de génération de code)](../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 Génère le code et le mappage pour le composant LINQ to SQL du .NET Framework.  
  
 [Storeadm.exe (outil Isolated Storage)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md)  
 Gère le stockage isolé en proposant des options pour répertorier les magasins de l'utilisateur et les supprimer.  
  
 [Tlbexp.exe (exportateur de bibliothèques de types)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)  
 Génère une bibliothèque de types décrivant les types définis dans un assembly du Common Language Runtime.  
  
 [Tlbimp.exe (importateur de bibliothèques de types)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)  
 Convertit les définitions de types présentes dans une bibliothèque de types COM en définitions équivalentes dans un assembly de Common Language Runtime.  
  
 [Winmdexp.exe (outil d’exportation de métadonnées Windows Runtime)](../../../docs/framework/tools/winmdexp-exe-windows-runtime-metadata-export-tool.md)  
 Exporte un assembly .NET Framework. compilé comme fichier .winmdobj dans un composant Windows Runtime, qui est empaqueté comme fichier .winmd qui contient à la fois les métadonnées Windows Runtime et des informations d'implémentation.  
  
 [Winres.exe (éditeur de ressources Windows Forms)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)  
 Aide à localiser des ressources d'interface utilisateur (fichiers .resx ou .resources) utilisées par les Windows Forms. Vous pouvez traduire des chaînes puis dimensionner, déplacer et masquer les contrôles comme vous le souhaitez afin de placer les chaînes localisées.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Outils](https://msdn.microsoft.com/library/f533241c-317c-445e-88ca-c80c8d078fca)  
 Inclut des outils comme l’outil isXPS Conformance (isXPS.exe) et les outils de profilage des performances.  
  
 [Outils Windows Communication Foundation](../../../docs/framework/wcf/tools.md)  
 Inclut des outils qui facilitent la création, le déploiement et la gestion d'applications Windows Communication Foundation (WCF).
