---
title: "QualifierSet_BeginEnumeration (fonction) (référence des API non managées)"
description: "La fonction QualifierSet_BeginEnumeration réinitialise l’énumérateur des qualificateurs d’un objet."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_BeginEnumeration
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_BeginEnumeration
helpviewer_keywords: QualifierSet_BeginEnumeration function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f66df772032b8e96b4956f3ed9a5818e961bd919
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="qualifiersetbeginenumeration-function"></a><span data-ttu-id="8d9f7-103">QualifierSet_BeginEnumeration (fonction)</span><span class="sxs-lookup"><span data-stu-id="8d9f7-103">QualifierSet_BeginEnumeration function</span></span>
<span data-ttu-id="8d9f7-104">Réinitialise l’énumérateur des qualificateurs d’un objet au début de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="8d9f7-104">Resets an enumerator of the qualifiers of an object to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="8d9f7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d9f7-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="8d9f7-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8d9f7-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="8d9f7-107">[in] Ce paramètre est inutilisé.</span><span class="sxs-lookup"><span data-stu-id="8d9f7-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="8d9f7-108">[in] Un pointeur vers un [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span><span class="sxs-lookup"><span data-stu-id="8d9f7-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`lFlags`   
<span data-ttu-id="8d9f7-109">[in] Une combinaison au niveau du bit des indicateurs ou des valeurs décrites dans le [notes](#remarks) section qui spécifie les qualificateurs à inclure dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="8d9f7-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that specifies the qualifiers to include in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="8d9f7-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8d9f7-110">Return value</span></span>

<span data-ttu-id="8d9f7-111">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="8d9f7-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="8d9f7-112">Constante</span><span class="sxs-lookup"><span data-stu-id="8d9f7-112">Constant</span></span>  |<span data-ttu-id="8d9f7-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="8d9f7-113">Value</span></span>  |<span data-ttu-id="8d9f7-114">Description</span><span class="sxs-lookup"><span data-stu-id="8d9f7-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="8d9f7-115">0 x 80041008</span><span class="sxs-lookup"><span data-stu-id="8d9f7-115">0x80041008</span></span> | <span data-ttu-id="8d9f7-116">Le `lFlags` paramètre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="8d9f7-116">The `lFlags` parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="8d9f7-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="8d9f7-117">0x8004101d</span></span> | <span data-ttu-id="8d9f7-118">Un deuxième appel à `QualifierSet_BeginEnumeration` a été effectuée sans appel intermédiaire à [ `QualifierSet_EndEnumeration` ](qualifierset-endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="8d9f7-118">A second call to `QualifierSet_BeginEnumeration` was made without an intervening call to [`QualifierSet_EndEnumeration`](qualifierset-endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="8d9f7-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="8d9f7-119">0x80041006</span></span> | <span data-ttu-id="8d9f7-120">Pas assez de mémoire est disponible pour commencer une nouvelle énumération.</span><span class="sxs-lookup"><span data-stu-id="8d9f7-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="8d9f7-121">0</span><span class="sxs-lookup"><span data-stu-id="8d9f7-121">0</span></span> | <span data-ttu-id="8d9f7-122">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="8d9f7-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="8d9f7-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="8d9f7-123">Remarks</span></span>

<span data-ttu-id="8d9f7-124">Cette fonction encapsule un appel à la [IWbemQualifierSet::BeginEnumeration](https://msdn.microsoft.com/library/aa391861(v=vs.85).aspx) (méthode).</span><span class="sxs-lookup"><span data-stu-id="8d9f7-124">This function wraps a call to the [IWbemQualifierSet::BeginEnumeration](https://msdn.microsoft.com/library/aa391861(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="8d9f7-125">Pour énumérer tous les qualificateurs sur un objet, cette méthode doit être appelée avant le premier appel à [QualifierSet_Next](qualifierset-next.md).</span><span class="sxs-lookup"><span data-stu-id="8d9f7-125">To enumerate all of the qualifiers on an object, this method must be called before the first call to [QualifierSet_Next](qualifierset-next.md).</span></span> <span data-ttu-id="8d9f7-126">L’ordre dans lequel les qualificateurs sont énumérées est garanti être indifférente pour une énumération spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8d9f7-126">The order in which qualifiers are enumerated is guaranteed to be invariant for a given enumeration.</span></span>

<span data-ttu-id="8d9f7-127">Les indicateurs qui peuvent être passés en tant que le `lEnumFlags` argument sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code.</span><span class="sxs-lookup"><span data-stu-id="8d9f7-127">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>   

|<span data-ttu-id="8d9f7-128">Constante</span><span class="sxs-lookup"><span data-stu-id="8d9f7-128">Constant</span></span>  |<span data-ttu-id="8d9f7-129">Valeur</span><span class="sxs-lookup"><span data-stu-id="8d9f7-129">Value</span></span>  |<span data-ttu-id="8d9f7-130">Description</span><span class="sxs-lookup"><span data-stu-id="8d9f7-130">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="8d9f7-131">0</span><span class="sxs-lookup"><span data-stu-id="8d9f7-131">0</span></span> | <span data-ttu-id="8d9f7-132">Retourner les noms de tous les qualificateurs.</span><span class="sxs-lookup"><span data-stu-id="8d9f7-132">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="8d9f7-133">0 x 10</span><span class="sxs-lookup"><span data-stu-id="8d9f7-133">0x10</span></span> | <span data-ttu-id="8d9f7-134">Retourner uniquement les noms des qualificateurs spécifiques à l’objet ou la propriété actuelle.</span><span class="sxs-lookup"><span data-stu-id="8d9f7-134">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="8d9f7-135">Pour une propriété : retourner uniquement les qualificateurs spécifiques à la propriété (y compris les substitutions), et pas ces qualificateurs propagés à partir de la définition de classe.</span><span class="sxs-lookup"><span data-stu-id="8d9f7-135">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="8d9f7-136">Pour une instance : retourner uniquement des noms spécifiques à l’instance qualificateur.</span><span class="sxs-lookup"><span data-stu-id="8d9f7-136">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="8d9f7-137">Pour une classe : retourner uniquement les qualificateurs spécifiques à la beiong de la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="8d9f7-137">For a class: Return only qualifiers specific to the class beiong derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="8d9f7-138">0 x 20</span><span class="sxs-lookup"><span data-stu-id="8d9f7-138">0x20</span></span> | <span data-ttu-id="8d9f7-139">Retourne uniquement les noms des qualificateurs propagés à partir d’un autre objet.</span><span class="sxs-lookup"><span data-stu-id="8d9f7-139">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="8d9f7-140">Pour une propriété : retour uniquement les qualificateurs propagées à cette propriété à partir de la définition de classe et non celles de la propriété proprement dite.</span><span class="sxs-lookup"><span data-stu-id="8d9f7-140">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="8d9f7-141">Pour une instance : retour uniquement ces qualificateurs propagés à partir de la définition de classe.</span><span class="sxs-lookup"><span data-stu-id="8d9f7-141">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="8d9f7-142">Pour une classe : retour uniquement les noms de qualificateur héritées des classes parentes.</span><span class="sxs-lookup"><span data-stu-id="8d9f7-142">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="8d9f7-143">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8d9f7-143">Requirements</span></span>  
 <span data-ttu-id="8d9f7-144">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d9f7-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d9f7-145">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="8d9f7-145">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="8d9f7-146">**Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8d9f7-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d9f7-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d9f7-147">See also</span></span>  
[<span data-ttu-id="8d9f7-148">WMI et les compteurs de Performance (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="8d9f7-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)