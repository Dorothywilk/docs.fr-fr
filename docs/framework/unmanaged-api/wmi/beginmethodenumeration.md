---
title: "BeginMethodEnumeration (fonction) (référence des API non managées)"
description: "La fonction BeginMethodEnumeration commence une énumération des méthodes de l’objet"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: BeginMethodEnumeration
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: BeginMethodEnumeration
helpviewer_keywords: BeginMethodEnumeration function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2e44c432f9503f96ad4dab9e25b78e6dd148f94c
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="beginenumeration-function"></a><span data-ttu-id="a87a6-103">BeginEnumeration (fonction)</span><span class="sxs-lookup"><span data-stu-id="a87a6-103">BeginEnumeration function</span></span>
<span data-ttu-id="a87a6-104">Commence une énumération des méthodes disponibles pour l’objet.</span><span class="sxs-lookup"><span data-stu-id="a87a6-104">Begins an enumeration of the methods available for the object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="a87a6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a87a6-105">Syntax</span></span>  
  
``` 
HRESULT BeginMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="a87a6-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a87a6-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="a87a6-107">[in] Ce paramètre est inutilisé.</span><span class="sxs-lookup"><span data-stu-id="a87a6-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="a87a6-108">[in] Un pointeur vers un [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="a87a6-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="a87a6-109">[in] Zéro (0) pour toutes les méthodes, ou un indicateur qui spécifie la portée de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="a87a6-109">[in] Zero (0) for all methods, or a flag that specifies the scope of the enumeration.</span></span> <span data-ttu-id="a87a6-110">Les indicateurs suivants sont définis dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="a87a6-110">The following flags are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

<span data-ttu-id="a87a6-111">Constante</span><span class="sxs-lookup"><span data-stu-id="a87a6-111">Constant</span></span>  |<span data-ttu-id="a87a6-112">Valeur</span><span class="sxs-lookup"><span data-stu-id="a87a6-112">Value</span></span>  |<span data-ttu-id="a87a6-113">Description</span><span class="sxs-lookup"><span data-stu-id="a87a6-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="a87a6-114">0 x 10</span><span class="sxs-lookup"><span data-stu-id="a87a6-114">0x10</span></span> | <span data-ttu-id="a87a6-115">Limiter l’énumération pour les méthodes qui sont définies dans la classe elle-même.</span><span class="sxs-lookup"><span data-stu-id="a87a6-115">Limit the enumeration to methods that are defined in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="a87a6-116">0 x 20</span><span class="sxs-lookup"><span data-stu-id="a87a6-116">0x20</span></span> | <span data-ttu-id="a87a6-117">Limiter l’énumération de propriétés qui sont héritées de classes de base.</span><span class="sxs-lookup"><span data-stu-id="a87a6-117">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="return-value"></a><span data-ttu-id="a87a6-118">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a87a6-118">Return value</span></span>

<span data-ttu-id="a87a6-119">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="a87a6-119">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a87a6-120">Constante</span><span class="sxs-lookup"><span data-stu-id="a87a6-120">Constant</span></span>  |<span data-ttu-id="a87a6-121">Valeur</span><span class="sxs-lookup"><span data-stu-id="a87a6-121">Value</span></span>  |<span data-ttu-id="a87a6-122">Description</span><span class="sxs-lookup"><span data-stu-id="a87a6-122">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="a87a6-123">0 x 80041008</span><span class="sxs-lookup"><span data-stu-id="a87a6-123">0x80041008</span></span> | <span data-ttu-id="a87a6-124">`lEnnumFlags`est différent de zéro et n’est pas un des indicateurs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="a87a6-124">`lEnnumFlags` is non-zero and is not one of the specified flags.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="a87a6-125">0</span><span class="sxs-lookup"><span data-stu-id="a87a6-125">0</span></span> | <span data-ttu-id="a87a6-126">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="a87a6-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="a87a6-127">Remarques</span><span class="sxs-lookup"><span data-stu-id="a87a6-127">Remarks</span></span>

<span data-ttu-id="a87a6-128">Cette fonction encapsule un appel à la [IWbemClassObject::BeginMethodEnumeration](https://msdn.microsoft.com/library/aa391435(v=vs.85).aspx) (méthode).</span><span class="sxs-lookup"><span data-stu-id="a87a6-128">This function wraps a call to the [IWbemClassObject::BeginMethodEnumeration](https://msdn.microsoft.com/library/aa391435(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="a87a6-129">Cet appel de méthode n’est possible que si l’objet actuel est une définition de classe.</span><span class="sxs-lookup"><span data-stu-id="a87a6-129">This method call is only supported if the current object is a class definition.</span></span> <span data-ttu-id="a87a6-130">Manipulation de la méthode n’est pas disponible à partir de [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) pointeurs qui pointent vers les instances.</span><span class="sxs-lookup"><span data-stu-id="a87a6-130">Method manipulation is not available from [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) pointers that point to instances.</span></span> <span data-ttu-id="a87a6-131">L’ordre dans lequel les méthodes sont énumérées est garanti être indifférente pour une instance donnée de [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx).</span><span class="sxs-lookup"><span data-stu-id="a87a6-131">The order in which methods are enumerated is guaranteed to be invariant for a given instance of [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx).</span></span>

## <a name="requirements"></a><span data-ttu-id="a87a6-132">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a87a6-132">Requirements</span></span>  
 <span data-ttu-id="a87a6-133">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a87a6-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a87a6-134">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="a87a6-134">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="a87a6-135">**Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a87a6-135">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a87a6-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a87a6-136">See also</span></span>  
[<span data-ttu-id="a87a6-137">WMI et les compteurs de Performance (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="a87a6-137">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)