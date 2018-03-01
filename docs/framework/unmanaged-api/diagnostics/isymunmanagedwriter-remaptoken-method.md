---
title: "ISymUnmanagedWriter::RemapToken メソッド"
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
- ISymUnmanagedWriter.RemapToken
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::RemapToken
helpviewer_keywords:
- ISymUnmanagedWriter::RemapToken method [.NET Framework debugging]
- RemapToken method [.NET Framework debugging]
ms.assetid: bca92682-ee1e-467f-8fb0-d8d4617f82fe
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 86d6c78a49c55bdc9093241952bee00ee331696e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterremaptoken-method"></a><span data-ttu-id="f9e5f-102">ISymUnmanagedWriter::RemapToken メソッド</span><span class="sxs-lookup"><span data-stu-id="f9e5f-102">ISymUnmanagedWriter::RemapToken Method</span></span>
<span data-ttu-id="f9e5f-103">メタデータの生成と、メタデータ トークンが再マップされたシンボル ライターを通知します。</span><span class="sxs-lookup"><span data-stu-id="f9e5f-103">Notifies the symbol writer that a metadata token has been remapped as the metadata was emitted.</span></span> <span data-ttu-id="f9e5f-104">シンボルのライターがシンボル ストア内の古いトークンを格納してある場合、読み込みフェーズ中に再マップする、対応するシンボル リーダーのマップを保存して格納したトークンを新しい値、またはそのどちらかの更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f9e5f-104">If the symbol writer has stored the old token within the symbol store, it must either update the stored token with the new value, or it must save the map for the corresponding symbol reader to remap during the read phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9e5f-105">構文</span><span class="sxs-lookup"><span data-stu-id="f9e5f-105">Syntax</span></span>  
  
```  
HRESULT RemapToken(  
    [in] mdToken  oldToken,  
    [in] mdToken  newToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f9e5f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f9e5f-106">Parameters</span></span>  
 `oldToken`  
 <span data-ttu-id="f9e5f-107">[in]再マップされたメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="f9e5f-107">[in] The metadata token that was remapped.</span></span>  
  
 `newToken`  
 <span data-ttu-id="f9e5f-108">[in]新しいメタデータ トークンを`oldToken`リマップされました。</span><span class="sxs-lookup"><span data-stu-id="f9e5f-108">[in] The new metadata token to which `oldToken` was remapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9e5f-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="f9e5f-109">Return Value</span></span>  
 <span data-ttu-id="f9e5f-110">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="f9e5f-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9e5f-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="f9e5f-111">Requirements</span></span>  
 <span data-ttu-id="f9e5f-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f9e5f-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9e5f-113">参照</span><span class="sxs-lookup"><span data-stu-id="f9e5f-113">See Also</span></span>  
 [<span data-ttu-id="f9e5f-114">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f9e5f-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
