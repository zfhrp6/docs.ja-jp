---
title: "ISymUnmanagedReader::GetDocument メソッド"
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
- ISymUnmanagedReader.GetDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocument
helpviewer_keywords:
- ISymUnmanagedReader::GetDocument method [.NET Framework debugging]
- GetDocument method [.NET Framework debugging]
ms.assetid: bb203853-6a6d-4027-b9e9-603a7f28b9d3
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 00ded0e7e88cacbcedb66e1cef27e4f5eaaf4d29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetdocument-method"></a><span data-ttu-id="4be4c-102">ISymUnmanagedReader::GetDocument メソッド</span><span class="sxs-lookup"><span data-stu-id="4be4c-102">ISymUnmanagedReader::GetDocument Method</span></span>
<span data-ttu-id="4be4c-103">ドキュメントを検索します。</span><span class="sxs-lookup"><span data-stu-id="4be4c-103">Finds a document.</span></span> <span data-ttu-id="4be4c-104">ドキュメントの言語、ベンダ、および型は省略できます。</span><span class="sxs-lookup"><span data-stu-id="4be4c-104">The document language, vendor, and type are optional.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4be4c-105">構文</span><span class="sxs-lookup"><span data-stu-id="4be4c-105">Syntax</span></span>  
  
```  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4be4c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4be4c-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="4be4c-107">[in]ドキュメントを識別する URL です。</span><span class="sxs-lookup"><span data-stu-id="4be4c-107">[in] The URL that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="4be4c-108">[in]ドキュメントの言語。</span><span class="sxs-lookup"><span data-stu-id="4be4c-108">[in] The document language.</span></span> <span data-ttu-id="4be4c-109">このパラメーターは省略できます。</span><span class="sxs-lookup"><span data-stu-id="4be4c-109">This parameter is optional.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="4be4c-110">[in]ドキュメントの言語のベンダーの id。</span><span class="sxs-lookup"><span data-stu-id="4be4c-110">[in] The identity of the vendor for the document language.</span></span> <span data-ttu-id="4be4c-111">このパラメーターは省略できます。</span><span class="sxs-lookup"><span data-stu-id="4be4c-111">This parameter is optional.</span></span>  
  
 `documentType`  
 <span data-ttu-id="4be4c-112">[in]ドキュメントの種類。</span><span class="sxs-lookup"><span data-stu-id="4be4c-112">[in] The type of the document.</span></span> <span data-ttu-id="4be4c-113">このパラメーターは省略できます。</span><span class="sxs-lookup"><span data-stu-id="4be4c-113">This parameter is optional.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="4be4c-114">[out]返されたインターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="4be4c-114">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4be4c-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="4be4c-115">Return Value</span></span>  
 <span data-ttu-id="4be4c-116">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="4be4c-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4be4c-117">必要条件</span><span class="sxs-lookup"><span data-stu-id="4be4c-117">Requirements</span></span>  
 <span data-ttu-id="4be4c-118">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4be4c-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4be4c-119">参照</span><span class="sxs-lookup"><span data-stu-id="4be4c-119">See Also</span></span>  
 [<span data-ttu-id="4be4c-120">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4be4c-120">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
