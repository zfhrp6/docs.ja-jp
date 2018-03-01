---
title: "ISymUnmanagedENCUpdate::UpdateMethodLines メソッド"
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
- ISymUnmanagedENCUpdate.UpdateMethodLines
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::UpdateMethodLines
helpviewer_keywords:
- UpdateMethodLines method [.NET Framework debugging]
- ISymUnmanagedENCUpdate::UpdateMethodLines method [.NET Framework debugging]
ms.assetid: 275ef87b-0b53-49f9-af6b-58506335dc06
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2e8ffecba62b6531c852e6510013ba56b9258b64
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a><span data-ttu-id="0b9b6-102">ISymUnmanagedENCUpdate::UpdateMethodLines メソッド</span><span class="sxs-lookup"><span data-stu-id="0b9b6-102">ISymUnmanagedENCUpdate::UpdateMethodLines Method</span></span>
<span data-ttu-id="0b9b6-103">再コンパイルされていないがある行が個別に移動されたメソッドの行情報を更新できるようにします。</span><span class="sxs-lookup"><span data-stu-id="0b9b6-103">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="0b9b6-104">各ステートメントのデルタが許可されます。</span><span class="sxs-lookup"><span data-stu-id="0b9b6-104">A delta for each statement is allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b9b6-105">構文</span><span class="sxs-lookup"><span data-stu-id="0b9b6-105">Syntax</span></span>  
  
```  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0b9b6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0b9b6-106">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="0b9b6-107">[in]メソッドのトークンのメタデータ。</span><span class="sxs-lookup"><span data-stu-id="0b9b6-107">[in] The metadata of the method token.</span></span>  
  
 `pDeltas`  
 <span data-ttu-id="0b9b6-108">[in]配列`INT32`メソッド内の各シーケンス ポイントのデルタを示す値。</span><span class="sxs-lookup"><span data-stu-id="0b9b6-108">[in] An array of `INT32` values that indicates deltas for each sequence point in the method.</span></span>  
  
 `cDeltas`  
 <span data-ttu-id="0b9b6-109">[in]A`ULONG`のサイズを含む、`pDeltas`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="0b9b6-109">[in] A `ULONG` containing the size of the `pDeltas` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b9b6-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="0b9b6-110">Return Value</span></span>  
 <span data-ttu-id="0b9b6-111">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="0b9b6-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b9b6-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="0b9b6-112">Requirements</span></span>  
 <span data-ttu-id="0b9b6-113">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0b9b6-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b9b6-114">参照</span><span class="sxs-lookup"><span data-stu-id="0b9b6-114">See Also</span></span>  
 [<span data-ttu-id="0b9b6-115">ISymUnmanagedENCUpdate インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0b9b6-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
