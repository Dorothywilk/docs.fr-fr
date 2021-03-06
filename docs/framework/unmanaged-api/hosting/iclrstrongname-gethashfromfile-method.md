---
title: Méthode ICLRStrongName::GetHashFromFile
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromFile method [.NET Framework hosting]
- GetHashFromFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 9e50480a-8ada-4044-b2a5-97bb14ed3525
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 33aab5ee23a1f0d30d1f9f3079856ca30d46d2ec
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48033296"
---
# <a name="iclrstrongnamegethashfromfile-method"></a>Méthode ICLRStrongName::GetHashFromFile
Génère un hachage sur le contenu du fichier spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `szFilePath`  
 [in] Le nom du fichier à hacher.  
  
 `piHashAlg`  
 [in, out] L’algorithme à utiliser lors de la génération du hachage. Les algorithmes valides sont ceux définis par l’interface CryptoAPI Win32. Si `piHashAlg` est définie sur 0, l’algorithme par défaut CALG_SHA-1 est utilisé.  
  
 `pbHash`  
 [out] Tableau d’octets contenant le hachage généré.  
  
 `cchHash`  
 [in] La taille maximale de la mémoire tampon qui `pbHash` pointe vers.  
  
 `pchHash`  
 [out] La taille, en octets, de retourné `pbHash`.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK` Si la méthode a réussi ; Sinon, une valeur HRESULT qui indique un échec (consultez [valeurs HRESULT courantes](https://go.microsoft.com/fwlink/?LinkId=213878) pour obtenir la liste).  
  
## <a name="remarks"></a>Notes  
 Cette méthode est identique à la [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) , à ceci près que le nom du fichier spécification est ANSI au lieu d’Unicode.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MetaHost.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [GetHashFromFileW, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)  
 [ICLRStrongName, interface](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
