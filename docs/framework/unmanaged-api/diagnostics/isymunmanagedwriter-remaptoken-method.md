---
title: "ISymUnmanagedWriter::RemapToken メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.RemapToken
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::RemapToken
helpviewer_keywords:
- ISymUnmanagedWriter::RemapToken method [.NET Framework debugging]
- RemapToken method [.NET Framework debugging]
ms.assetid: bca92682-ee1e-467f-8fb0-d8d4617f82fe
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 857b68c0443e7b23af30ed64ecc9b78af0b40880
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriterremaptoken-method"></a><span data-ttu-id="00d94-102">ISymUnmanagedWriter::RemapToken メソッド</span><span class="sxs-lookup"><span data-stu-id="00d94-102">ISymUnmanagedWriter::RemapToken Method</span></span>
<span data-ttu-id="00d94-103">メタデータの生成と、メタデータ トークンが再マップされたシンボル ライターを通知します。</span><span class="sxs-lookup"><span data-stu-id="00d94-103">Notifies the symbol writer that a metadata token has been remapped as the metadata was emitted.</span></span> <span data-ttu-id="00d94-104">シンボルのライターがシンボル ストア内の古いトークンを格納してある場合、読み込みフェーズ中に再マップする、対応するシンボル リーダーのマップを保存して格納したトークンを新しい値、またはそのどちらかの更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="00d94-104">If the symbol writer has stored the old token within the symbol store, it must either update the stored token with the new value, or it must save the map for the corresponding symbol reader to remap during the read phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00d94-105">構文</span><span class="sxs-lookup"><span data-stu-id="00d94-105">Syntax</span></span>  
  
```  
HRESULT RemapToken(  
    [in] mdToken  oldToken,  
    [in] mdToken  newToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="00d94-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="00d94-106">Parameters</span></span>  
 `oldToken`  
 <span data-ttu-id="00d94-107">[in]再マップされたメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="00d94-107">[in] The metadata token that was remapped.</span></span>  
  
 `newToken`  
 <span data-ttu-id="00d94-108">[in]新しいメタデータ トークンを`oldToken`リマップされました。</span><span class="sxs-lookup"><span data-stu-id="00d94-108">[in] The new metadata token to which `oldToken` was remapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00d94-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="00d94-109">Return Value</span></span>  
 <span data-ttu-id="00d94-110">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="00d94-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00d94-111">要件</span><span class="sxs-lookup"><span data-stu-id="00d94-111">Requirements</span></span>  
 <span data-ttu-id="00d94-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="00d94-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00d94-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="00d94-113">See Also</span></span>  
 [<span data-ttu-id="00d94-114">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="00d94-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
