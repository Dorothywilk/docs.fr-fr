---
title: "ICLRAssemblyReferenceList::IsAssemblyReferenceInList, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyReferenceList.IsAssemblyReferenceInList
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyReferenceList::IsAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsAssemblyReferenceInList method [.NET Framework hosting]
- IsAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: 8a570813-21be-407e-92a6-7ae8de3bc728
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 923f7f4178d3c310b51ebb7e7df06040ba69f9c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyreferencelistisassemblyreferenceinlist-method"></a><span data-ttu-id="34255-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList, méthode</span><span class="sxs-lookup"><span data-stu-id="34255-102">ICLRAssemblyReferenceList::IsAssemblyReferenceInList Method</span></span>
<span data-ttu-id="34255-103">Obtient une valeur qui indique si le pointeur fourni fait référence à un assembly dans la liste.</span><span class="sxs-lookup"><span data-stu-id="34255-103">Gets a value that indicates whether the supplied pointer refers to an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34255-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34255-104">Syntax</span></span>  
  
```  
HRESULT IsAssemblyReferenceInList (  
    [in] IUnknown *pName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="34255-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="34255-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="34255-106">[in] Un pointeur d’interface à l’assembly à rechercher.</span><span class="sxs-lookup"><span data-stu-id="34255-106">[in] An interface pointer to the assembly for which to search.</span></span> <span data-ttu-id="34255-107">Les valeurs valides sont de type `IAssemblyName` ou `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="34255-107">Valid values are of type `IAssemblyName` or `IReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34255-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="34255-108">Return Value</span></span>  
  
|<span data-ttu-id="34255-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="34255-109">HRESULT</span></span>|<span data-ttu-id="34255-110">Description</span><span class="sxs-lookup"><span data-stu-id="34255-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="34255-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="34255-111">S_OK</span></span>|<span data-ttu-id="34255-112">La chaîne apparaît dans la liste.</span><span class="sxs-lookup"><span data-stu-id="34255-112">The string appears in the list.</span></span>|  
|<span data-ttu-id="34255-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="34255-113">S_FALSE</span></span>|<span data-ttu-id="34255-114">La chaîne n’apparaît pas dans la liste.</span><span class="sxs-lookup"><span data-stu-id="34255-114">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="34255-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="34255-115">E_FAIL</span></span>|<span data-ttu-id="34255-116">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="34255-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="34255-117">Une fois une méthode retourne E_FAIL, le common language runtime n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="34255-117">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="34255-118">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="34255-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="34255-119">Spécifications</span><span class="sxs-lookup"><span data-stu-id="34255-119">Requirements</span></span>  
 <span data-ttu-id="34255-120">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34255-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34255-121">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="34255-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="34255-122">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="34255-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="34255-123">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34255-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34255-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34255-124">See Also</span></span>  
 [<span data-ttu-id="34255-125">ICLRAssemblyIdentityManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="34255-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="34255-126">ICLRAssemblyReferenceList (Interface)</span><span class="sxs-lookup"><span data-stu-id="34255-126">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="34255-127">IHostAssemblyManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="34255-127">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="34255-128">IHostAssemblyStore (Interface)</span><span class="sxs-lookup"><span data-stu-id="34255-128">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)