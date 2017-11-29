---
title: ISymUnmanagedDocument, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument
helpviewer_keywords: ISymUnmanagedDocument interface [.NET Framework debugging]
ms.assetid: 5c26b366-6e81-467c-9dd0-02dd26fee0a3
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8654f28cc4d82a5ed1419215807ec3360522fd55
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocument-interface"></a><span data-ttu-id="02456-102">ISymUnmanagedDocument, interface</span><span class="sxs-lookup"><span data-stu-id="02456-102">ISymUnmanagedDocument Interface</span></span>
<span data-ttu-id="02456-103">Représente un document référencé par un magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="02456-103">Represents a document referenced by a symbol store.</span></span> <span data-ttu-id="02456-104">Un document est défini par un localisateur de ressource uniforme (URL) et un GUID de type de document.</span><span class="sxs-lookup"><span data-stu-id="02456-104">A document is defined by a uniform resource locator (URL) and a document type GUID.</span></span> <span data-ttu-id="02456-105">Vous pouvez localiser le document, quelle que soit la façon dont elle est stockée à l’aide de l’URL et le GUID de type de document.</span><span class="sxs-lookup"><span data-stu-id="02456-105">You can locate the document regardless of how it is stored by using the URL and document type GUID.</span></span> <span data-ttu-id="02456-106">Vous pouvez stocker la source de document dans le magasin de symboles et en la récupérant via cette interface.</span><span class="sxs-lookup"><span data-stu-id="02456-106">You can store the document source in the symbol store and retrieve it through this interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="02456-107">Méthodes</span><span class="sxs-lookup"><span data-stu-id="02456-107">Methods</span></span>  
  
|<span data-ttu-id="02456-108">Méthode</span><span class="sxs-lookup"><span data-stu-id="02456-108">Method</span></span>|<span data-ttu-id="02456-109">Description</span><span class="sxs-lookup"><span data-stu-id="02456-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="02456-110">FindClosestLine (méthode)</span><span class="sxs-lookup"><span data-stu-id="02456-110">FindClosestLine Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-findclosestline-method.md)|<span data-ttu-id="02456-111">Retourne la ligne la plus proche qui est un point de séquence, en fonction d’une ligne dans ce document, qui peut être ou non un point de séquence.</span><span class="sxs-lookup"><span data-stu-id="02456-111">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>|  
|[<span data-ttu-id="02456-112">GetCheckSum, méthode</span><span class="sxs-lookup"><span data-stu-id="02456-112">GetCheckSum Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksum-method.md)|<span data-ttu-id="02456-113">Obtient la somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="02456-113">Gets the checksum.</span></span>|  
|[<span data-ttu-id="02456-114">GetCheckSumAlgorithmId (méthode)</span><span class="sxs-lookup"><span data-stu-id="02456-114">GetCheckSumAlgorithmId Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksumalgorithmid-method.md)|<span data-ttu-id="02456-115">Obtient l’identificateur d’algorithme de somme de contrôle, ou retourne un GUID de tous les zéros s’il n’existe aucune somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="02456-115">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>|  
|[<span data-ttu-id="02456-116">GetDocumentType (méthode)</span><span class="sxs-lookup"><span data-stu-id="02456-116">GetDocumentType Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getdocumenttype-method.md)|<span data-ttu-id="02456-117">Obtient le type de document de ce document.</span><span class="sxs-lookup"><span data-stu-id="02456-117">Gets the document type of this document.</span></span>|  
|[<span data-ttu-id="02456-118">GetLanguage (méthode)</span><span class="sxs-lookup"><span data-stu-id="02456-118">GetLanguage Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguage-method.md)|<span data-ttu-id="02456-119">Obtient l’identificateur de langue de ce document.</span><span class="sxs-lookup"><span data-stu-id="02456-119">Gets the language identifier of this document.</span></span>|  
|[<span data-ttu-id="02456-120">GetLanguageVendor (méthode)</span><span class="sxs-lookup"><span data-stu-id="02456-120">GetLanguageVendor Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguagevendor-method.md)|<span data-ttu-id="02456-121">Obtient le fournisseur de langage de ce document.</span><span class="sxs-lookup"><span data-stu-id="02456-121">Gets the language vendor of this document.</span></span>|  
|[<span data-ttu-id="02456-122">GetSourceLength (méthode)</span><span class="sxs-lookup"><span data-stu-id="02456-122">GetSourceLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcelength-method.md)|<span data-ttu-id="02456-123">Obtient la longueur, en octets, de la source incorporée.</span><span class="sxs-lookup"><span data-stu-id="02456-123">Gets the length, in bytes, of the embedded source.</span></span>|  
|[<span data-ttu-id="02456-124">GetSourceRange (méthode)</span><span class="sxs-lookup"><span data-stu-id="02456-124">GetSourceRange Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcerange-method.md)|<span data-ttu-id="02456-125">Retourne la plage spécifiée de la source incorporée dans la mémoire tampon donnée.</span><span class="sxs-lookup"><span data-stu-id="02456-125">Returns the specified range of the embedded source into the given buffer.</span></span>|  
|[<span data-ttu-id="02456-126">Méthode GetURL.</span><span class="sxs-lookup"><span data-stu-id="02456-126">GetURL Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-geturl-method.md)|<span data-ttu-id="02456-127">Retourne l’URL de ce document.</span><span class="sxs-lookup"><span data-stu-id="02456-127">Returns the URL for this document.</span></span>|  
|[<span data-ttu-id="02456-128">HasEmbeddedSource (méthode)</span><span class="sxs-lookup"><span data-stu-id="02456-128">HasEmbeddedSource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-hasembeddedsource-method.md)|<span data-ttu-id="02456-129">Retourne `true` si le document a la source incorporée dans les symboles de débogage ; sinon, retourne `false`.</span><span class="sxs-lookup"><span data-stu-id="02456-129">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="02456-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02456-130">See Also</span></span>  
 [<span data-ttu-id="02456-131">Interfaces du magasin de symboles de Diagnostics</span><span class="sxs-lookup"><span data-stu-id="02456-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)