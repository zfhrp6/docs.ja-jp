---
title: "ISymUnmanagedDocument インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument
helpviewer_keywords:
- ISymUnmanagedDocument interface [.NET Framework debugging]
ms.assetid: 5c26b366-6e81-467c-9dd0-02dd26fee0a3
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2e176679b4fdb4d0a2c5c4fbcbc09403e45f1ad1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanageddocument-interface"></a><span data-ttu-id="eba9a-102">ISymUnmanagedDocument インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eba9a-102">ISymUnmanagedDocument Interface</span></span>
<span data-ttu-id="eba9a-103">シンボル ストアによって参照されるドキュメントを表します。</span><span class="sxs-lookup"><span data-stu-id="eba9a-103">Represents a document referenced by a symbol store.</span></span> <span data-ttu-id="eba9a-104">ドキュメントは、uniform resource locator (URL) と GUID のドキュメント型によって定義されます。</span><span class="sxs-lookup"><span data-stu-id="eba9a-104">A document is defined by a uniform resource locator (URL) and a document type GUID.</span></span> <span data-ttu-id="eba9a-105">URL を使用して格納方法に関係なく、ドキュメントを検索し、ドキュメントの種類の GUID できます。</span><span class="sxs-lookup"><span data-stu-id="eba9a-105">You can locate the document regardless of how it is stored by using the URL and document type GUID.</span></span> <span data-ttu-id="eba9a-106">ドキュメントのソースをシンボル ストアに格納でき、このインターフェイスを通じて取得できます。</span><span class="sxs-lookup"><span data-stu-id="eba9a-106">You can store the document source in the symbol store and retrieve it through this interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eba9a-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="eba9a-107">Methods</span></span>  
  
|<span data-ttu-id="eba9a-108">メソッド</span><span class="sxs-lookup"><span data-stu-id="eba9a-108">Method</span></span>|<span data-ttu-id="eba9a-109">説明</span><span class="sxs-lookup"><span data-stu-id="eba9a-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eba9a-110">FindClosestLine メソッド</span><span class="sxs-lookup"><span data-stu-id="eba9a-110">FindClosestLine Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-findclosestline-method.md)|<span data-ttu-id="eba9a-111">行を指定した場合も、シーケンス ポイントができない可能性があります、このドキュメントでは、シーケンス ポイントである最も近い行を返します。</span><span class="sxs-lookup"><span data-stu-id="eba9a-111">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>|  
|[<span data-ttu-id="eba9a-112">GetCheckSum メソッド</span><span class="sxs-lookup"><span data-stu-id="eba9a-112">GetCheckSum Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksum-method.md)|<span data-ttu-id="eba9a-113">チェックサムを取得します。</span><span class="sxs-lookup"><span data-stu-id="eba9a-113">Gets the checksum.</span></span>|  
|[<span data-ttu-id="eba9a-114">GetCheckSumAlgorithmId メソッド</span><span class="sxs-lookup"><span data-stu-id="eba9a-114">GetCheckSumAlgorithmId Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksumalgorithmid-method.md)|<span data-ttu-id="eba9a-115">チェックサム アルゴリズム識別子を取得またはチェックサムがない場合に、すべてがゼロの GUID を取得します。</span><span class="sxs-lookup"><span data-stu-id="eba9a-115">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>|  
|[<span data-ttu-id="eba9a-116">GetDocumentType メソッド</span><span class="sxs-lookup"><span data-stu-id="eba9a-116">GetDocumentType Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getdocumenttype-method.md)|<span data-ttu-id="eba9a-117">このドキュメントのドキュメントの種類を取得します。</span><span class="sxs-lookup"><span data-stu-id="eba9a-117">Gets the document type of this document.</span></span>|  
|[<span data-ttu-id="eba9a-118">GetLanguage メソッド</span><span class="sxs-lookup"><span data-stu-id="eba9a-118">GetLanguage Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguage-method.md)|<span data-ttu-id="eba9a-119">このドキュメントの言語識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="eba9a-119">Gets the language identifier of this document.</span></span>|  
|[<span data-ttu-id="eba9a-120">GetLanguageVendor メソッド</span><span class="sxs-lookup"><span data-stu-id="eba9a-120">GetLanguageVendor Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguagevendor-method.md)|<span data-ttu-id="eba9a-121">このドキュメントの言語の販売元を取得します。</span><span class="sxs-lookup"><span data-stu-id="eba9a-121">Gets the language vendor of this document.</span></span>|  
|[<span data-ttu-id="eba9a-122">GetSourceLength メソッド</span><span class="sxs-lookup"><span data-stu-id="eba9a-122">GetSourceLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcelength-method.md)|<span data-ttu-id="eba9a-123">埋め込まれたソースの長さをバイト数で取得します。</span><span class="sxs-lookup"><span data-stu-id="eba9a-123">Gets the length, in bytes, of the embedded source.</span></span>|  
|[<span data-ttu-id="eba9a-124">GetSourceRange メソッド</span><span class="sxs-lookup"><span data-stu-id="eba9a-124">GetSourceRange Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcerange-method.md)|<span data-ttu-id="eba9a-125">指定されたバッファーに埋め込まれたソースの指定した範囲を返します。</span><span class="sxs-lookup"><span data-stu-id="eba9a-125">Returns the specified range of the embedded source into the given buffer.</span></span>|  
|[<span data-ttu-id="eba9a-126">GetURL メソッド</span><span class="sxs-lookup"><span data-stu-id="eba9a-126">GetURL Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-geturl-method.md)|<span data-ttu-id="eba9a-127">このドキュメントの URL を返します。</span><span class="sxs-lookup"><span data-stu-id="eba9a-127">Returns the URL for this document.</span></span>|  
|[<span data-ttu-id="eba9a-128">HasEmbeddedSource メソッド</span><span class="sxs-lookup"><span data-stu-id="eba9a-128">HasEmbeddedSource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-hasembeddedsource-method.md)|<span data-ttu-id="eba9a-129">返します`true`場合は、ドキュメントには、デバッグ シンボルに埋め込まれたソースを返しますそれ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="eba9a-129">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eba9a-130">参照</span><span class="sxs-lookup"><span data-stu-id="eba9a-130">See Also</span></span>  
 [<span data-ttu-id="eba9a-131">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eba9a-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
