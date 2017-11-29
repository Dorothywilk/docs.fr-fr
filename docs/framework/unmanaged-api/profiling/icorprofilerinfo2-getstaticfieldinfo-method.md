---
title: "ICorProfilerInfo2::GetStaticFieldInfo, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetStaticFieldInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetStaticFieldInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo method [.NET Framework profiling]
- GetStaticFieldInfo method [.NET Framework profiling]
ms.assetid: fc663e76-e23f-49a8-bdd5-52cdf1a3b2b3
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7cf16a0fae7f3e2afd095534b2e7f7957d44e3e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getstaticfieldinfo-method"></a><span data-ttu-id="19506-102">ICorProfilerInfo2::GetStaticFieldInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="19506-102">ICorProfilerInfo2::GetStaticFieldInfo Method</span></span>
<span data-ttu-id="19506-103">Obtient une valeur qui indique le type de champ statique qui s’applique au champ spécifié.</span><span class="sxs-lookup"><span data-stu-id="19506-103">Gets a value that indicates the kind of static that applies to the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19506-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19506-104">Syntax</span></span>  
  
```  
HRESULT GetStaticFieldInfo (  
    [in] ClassID               classId,  
    [in] mdFieldDef            fieldToken,  
    [out] COR_PRF_STATIC_TYPE  *pFieldInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="19506-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="19506-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="19506-106">[in] L’ID de la classe dans laquelle le champ statique est défini.</span><span class="sxs-lookup"><span data-stu-id="19506-106">[in] The ID of the class in which the static field is defined.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="19506-107">[in] Le jeton de métadonnées pour le champ statique.</span><span class="sxs-lookup"><span data-stu-id="19506-107">[in] The metadata token for the static field.</span></span>  
  
 `pFieldInfo`  
 <span data-ttu-id="19506-108">[out] Un pointeur vers une valeur de la [COR_PRF_STATIC_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md) énumération qui indique si le champ spécifié est statique et si, par conséquent, le type de champ statique qui s’applique au champ.</span><span class="sxs-lookup"><span data-stu-id="19506-108">[out] A pointer to a value of the [COR_PRF_STATIC_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md) enumeration that indicates whether the specified field is static, and if so, the kind of static that applies to the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19506-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="19506-109">Remarks</span></span>  
 <span data-ttu-id="19506-110">Ces informations peuvent être utilisées pour déterminer la fonction à appeler pour obtenir l’adresse du champ statique.</span><span class="sxs-lookup"><span data-stu-id="19506-110">This information can be used to determine which function to call to get the address of the static field.</span></span>  
  
 <span data-ttu-id="19506-111">Le profileur de code doit toujours vérifier les métadonnées pour un champ statique pour vous assurer qu’il a réellement une adresse.</span><span class="sxs-lookup"><span data-stu-id="19506-111">The profiler code should still check the metadata for a static field to ensure that it actually has an address.</span></span> <span data-ttu-id="19506-112">Littéraux statiques (autrement dit, les constantes) existent uniquement dans les métadonnées et n’ayant pas d’adresse.</span><span class="sxs-lookup"><span data-stu-id="19506-112">Static literals (that is, constants) exist only in the metadata and do not have an address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19506-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="19506-113">Requirements</span></span>  
 <span data-ttu-id="19506-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19506-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19506-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="19506-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="19506-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19506-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19506-117">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19506-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19506-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19506-118">See Also</span></span>  
 [<span data-ttu-id="19506-119">ICorProfilerInfo (Interface)</span><span class="sxs-lookup"><span data-stu-id="19506-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="19506-120">ICorProfilerInfo2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="19506-120">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)