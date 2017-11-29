---
title: "ISymUnmanagedReader::GetDocuments メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetDocuments
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetDocuments
helpviewer_keywords:
- GetDocuments method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocuments method [.NET Framework debugging]
ms.assetid: e3b73a3f-d089-4101-a9a9-5e0765d05b61
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 27268b7f32f2c9aa667790c6d4516f1b8e015f96
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetdocuments-method"></a><span data-ttu-id="d2a41-102">ISymUnmanagedReader::GetDocuments メソッド</span><span class="sxs-lookup"><span data-stu-id="d2a41-102">ISymUnmanagedReader::GetDocuments Method</span></span>
<span data-ttu-id="d2a41-103">シンボル ストアで定義されているすべてのドキュメントの配列を返します。</span><span class="sxs-lookup"><span data-stu-id="d2a41-103">Returns an array of all the documents defined in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2a41-104">構文</span><span class="sxs-lookup"><span data-stu-id="d2a41-104">Syntax</span></span>  
  
```  
HRESULT GetDocuments (  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,  
    [out, size_is (cDocs),  
        length_is (*pcDocs)] ISymUnmanagedDocument *pDocs[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d2a41-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d2a41-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="d2a41-106">[in] `pDocs` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="d2a41-106">[in] The size of the `pDocs` array.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="d2a41-107">[out]配列の長さを受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="d2a41-107">[out] A pointer to a variable that receives the array length.</span></span>  
  
 `pDocs`  
 <span data-ttu-id="d2a41-108">[out]ドキュメントの配列を受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="d2a41-108">[out] A pointer to a variable that receives the document array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d2a41-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="d2a41-109">Return Value</span></span>  
 <span data-ttu-id="d2a41-110">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="d2a41-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2a41-111">要件</span><span class="sxs-lookup"><span data-stu-id="d2a41-111">Requirements</span></span>  
 <span data-ttu-id="d2a41-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d2a41-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2a41-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="d2a41-113">See Also</span></span>  
 [<span data-ttu-id="d2a41-114">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d2a41-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
