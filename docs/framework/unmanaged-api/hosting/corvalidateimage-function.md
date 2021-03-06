---
title: _CorValidateImage, fonction
ms.date: 03/30/2017
api_name:
- _CorValidateImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorValidateImage
helpviewer_keywords:
- _CorValidateImage function [.NET Framework hosting]
ms.assetid: 0117e080-05f9-4772-885d-e1847230947c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 101271823f7b7877bb7f007588b6a164233e5b45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="corvalidateimage-function"></a>_CorValidateImage, fonction
Valide les images de modules managés et notifie le chargeur du système d’exploitation après avoir été chargés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDAPI _CorValidateImage (   
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ImageBase`  
 [in] Un pointeur vers l’emplacement de départ de l’image à valider en tant que le code managé. L’image doit être déjà chargée en mémoire.  
  
 `FileName`  
 [in] Le nom de fichier de l’image.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette fonction retourne les valeurs standard `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, et `E_FAIL`, ainsi que les valeurs suivantes.  
  
|Valeur de retour|Description|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|L’image n’est pas valide. Cette valeur possède le HRESULT 0xC000007BL.|  
|`STATUS_SUCCESS`|L’image est valide. Cette valeur possède le HRESULT 0x00000000L.|  
  
## <a name="remarks"></a>Notes  
 Dans Windows XP et versions ultérieures, le chargeur du système d’exploitation recherche des modules managés en examinant le bit du répertoire du descripteur COM dans l’en-tête common object file format (COFF). Un bit défini indique un module managé. Si le chargeur détecte un module managé, il charge MsCorEE.dll et appelle `_CorValidateImage`, qui effectue les actions suivantes :  
  
-   Confirme que l’image est un module managé valid.  
  
-   Modifie le point d’entrée dans l’image à un point d’entrée dans le common language runtime (CLR).  
  
-   Pour les versions 64 bits de Windows, modifie l’image en mémoire en la transformant du format PE32 au format PE32 +.  
  
-   Retourne au chargeur lorsque les images de modules managés sont chargées.  
  
 Pour les images exécutables, le chargeur du système d’exploitation appelle ensuite la [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) (fonction), quel que soit le point d’entrée spécifié dans le fichier exécutable. Pour les images d’assembly DLL, le chargeur appelle la [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) (fonction).  
  
 `_CorExeMain` ou `_CorDllMain` effectue les actions suivantes :  
  
-   Initialise le CLR.  
  
-   Recherche le point d’entrée managé à partir de l’en-tête du CLR de l’assembly.  
  
-   Commence l’exécution.  
  
 Les appels de chargeur du [_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) fonctionner lorsque gérés images sont déchargées. Toutefois, cette fonction n’effectue pas d’action ; elle renvoie simplement.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions statiques globales des métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
