---
title: "ISymUnmanagedConstant::GetSignature メソッド"
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
- ISymUnmanagedConstant.GetSignature
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetSignature method [.NET Framework debugging]
ms.assetid: 3eb41151-a228-43e3-ba8f-e6dd3ceb8542
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 10bdf7b8b83b56ff856d966d2764ed04e06090aa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedconstantgetsignature-method"></a><span data-ttu-id="c83c6-102">ISymUnmanagedConstant::GetSignature メソッド</span><span class="sxs-lookup"><span data-stu-id="c83c6-102">ISymUnmanagedConstant::GetSignature Method</span></span>
<span data-ttu-id="c83c6-103">定数の署名を取得します。</span><span class="sxs-lookup"><span data-stu-id="c83c6-103">Gets the signature of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c83c6-104">構文</span><span class="sxs-lookup"><span data-stu-id="c83c6-104">Syntax</span></span>  
  
```  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c83c6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c83c6-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="c83c6-106">[in]バッファーの長さを`pcSig`パラメーターをポイントします。</span><span class="sxs-lookup"><span data-stu-id="c83c6-106">[in] The length of the buffer that the `pcSig` parameter points to.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="c83c6-107">[out]ポインター、`ULONG32`シグネチャの格納に必要なバッファーの文字のサイズを受け取る。</span><span class="sxs-lookup"><span data-stu-id="c83c6-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="c83c6-108">[out]署名を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="c83c6-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c83c6-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="c83c6-109">Return Value</span></span>  
 <span data-ttu-id="c83c6-110">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="c83c6-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c83c6-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="c83c6-111">Requirements</span></span>  
 <span data-ttu-id="c83c6-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c83c6-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c83c6-113">参照</span><span class="sxs-lookup"><span data-stu-id="c83c6-113">See Also</span></span>  
 [<span data-ttu-id="c83c6-114">ISymUnmanagedConstant インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c83c6-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 [<span data-ttu-id="c83c6-115">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="c83c6-115">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)  
 [<span data-ttu-id="c83c6-116">GetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="c83c6-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
