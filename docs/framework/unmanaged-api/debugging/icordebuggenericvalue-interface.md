---
title: ICorDebugGenericValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugGenericValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugGenericValue
helpviewer_keywords: ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: bc14f408-b359-4c8c-ade2-888ccdf7261b
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 61c159e30efb33dca4043e5b5306c9544acd614a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebuggenericvalue-interface1"></a><span data-ttu-id="5ad11-102">ICorDebugGenericValue Interface1</span><span class="sxs-lookup"><span data-stu-id="5ad11-102">ICorDebugGenericValue Interface1</span></span>
<span data-ttu-id="5ad11-103">Une sous-classe de « ICorDebugValue » qui s’applique à toutes les valeurs.</span><span class="sxs-lookup"><span data-stu-id="5ad11-103">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="5ad11-104">Cette interface fournit les méthodes Get et Set pour la valeur.</span><span class="sxs-lookup"><span data-stu-id="5ad11-104">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5ad11-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="5ad11-105">Methods</span></span>  
  
|<span data-ttu-id="5ad11-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="5ad11-106">Method</span></span>|<span data-ttu-id="5ad11-107">Description</span><span class="sxs-lookup"><span data-stu-id="5ad11-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5ad11-108">GetValue (méthode)</span><span class="sxs-lookup"><span data-stu-id="5ad11-108">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="5ad11-109">Copie la valeur dans la mémoire tampon spécifiée.</span><span class="sxs-lookup"><span data-stu-id="5ad11-109">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="5ad11-110">SetValue (méthode)</span><span class="sxs-lookup"><span data-stu-id="5ad11-110">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="5ad11-111">Copie une nouvelle valeur à partir de la mémoire tampon spécifiée.</span><span class="sxs-lookup"><span data-stu-id="5ad11-111">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ad11-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="5ad11-112">Remarks</span></span>  
 <span data-ttu-id="5ad11-113">`ICorDebugGenericValue`est une interface secondaire, car il est non accessible à distance.</span><span class="sxs-lookup"><span data-stu-id="5ad11-113">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="5ad11-114">Pour les types référence, la valeur est la référence plutôt que le contenu de la référence.</span><span class="sxs-lookup"><span data-stu-id="5ad11-114">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="5ad11-115">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="5ad11-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5ad11-116">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="5ad11-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ad11-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5ad11-117">Requirements</span></span>  
 <span data-ttu-id="5ad11-118">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ad11-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ad11-119">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5ad11-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5ad11-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ad11-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ad11-121">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ad11-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ad11-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ad11-122">See Also</span></span>  
    
 [<span data-ttu-id="5ad11-123">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="5ad11-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)