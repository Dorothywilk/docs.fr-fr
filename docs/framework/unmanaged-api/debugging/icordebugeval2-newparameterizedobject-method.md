---
title: "ICorDebugEval2::NewParameterizedObject, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2.NewParameterizedObject
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2::NewParameterizedObject
helpviewer_keywords:
- NewParameterizedObject method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObject method [.NET Framework debugging]
ms.assetid: 3d705463-e640-4249-8036-4e8206d03cfe
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 29b2470f50e96307ad91428fe1c712e7340baa32
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugeval2newparameterizedobject-method"></a><span data-ttu-id="54057-102">ICorDebugEval2::NewParameterizedObject, méthode</span><span class="sxs-lookup"><span data-stu-id="54057-102">ICorDebugEval2::NewParameterizedObject Method</span></span>
<span data-ttu-id="54057-103">Instancie un nouvel objet de type paramétré et appelle la méthode de constructeur de l’objet.</span><span class="sxs-lookup"><span data-stu-id="54057-103">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54057-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54057-104">Syntax</span></span>  
  
```  
HRESULT NewParameterizedObject (  
    [in] ICorDebugFunction     *pConstructor,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="54057-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="54057-105">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="54057-106">[in] Pointeur vers un objet ICorDebugFunction qui représente le constructeur de l’objet à instancier.</span><span class="sxs-lookup"><span data-stu-id="54057-106">[in] A pointer to an ICorDebugFunction object that represents the constructor of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="54057-107">[in] Le nombre d’arguments de type passés.</span><span class="sxs-lookup"><span data-stu-id="54057-107">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="54057-108">[in] Tableau de pointeurs, chacun pointant vers un objet ICorDebugType qui représente un argument de type pour l’objet qui est en cours d’instanciation.</span><span class="sxs-lookup"><span data-stu-id="54057-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="54057-109">[in] Le nombre d’arguments passés au constructeur.</span><span class="sxs-lookup"><span data-stu-id="54057-109">[in] The number of arguments passed to the constructor.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="54057-110">[in] Tableau de pointeurs, chacun pointant vers un objet ICorDebugValue qui représente une valeur d’argument est passée au constructeur.</span><span class="sxs-lookup"><span data-stu-id="54057-110">[in] An array of pointers, each of which points to an ICorDebugValue object that represents an argument value that is passed to the constructor.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54057-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="54057-111">Remarks</span></span>  
 <span data-ttu-id="54057-112">Constructeur de l’objet peut prendre <xref:System.Type> paramètres.</span><span class="sxs-lookup"><span data-stu-id="54057-112">The object's constructor may take <xref:System.Type> parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54057-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="54057-113">Requirements</span></span>  
 <span data-ttu-id="54057-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54057-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54057-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="54057-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="54057-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54057-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54057-117">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54057-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>