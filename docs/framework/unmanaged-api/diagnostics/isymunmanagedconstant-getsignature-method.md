---
title: "ISymUnmanagedConstant::GetSignature メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedConstant.GetSignature
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedConstant::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetSignature method [.NET Framework debugging]
ms.assetid: 3eb41151-a228-43e3-ba8f-e6dd3ceb8542
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 314d9115fdba7d57538e5b24c56863944db517fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedconstantgetsignature-method"></a><span data-ttu-id="09633-102">ISymUnmanagedConstant::GetSignature メソッド</span><span class="sxs-lookup"><span data-stu-id="09633-102">ISymUnmanagedConstant::GetSignature Method</span></span>
<span data-ttu-id="09633-103">定数の署名を取得します。</span><span class="sxs-lookup"><span data-stu-id="09633-103">Gets the signature of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09633-104">構文</span><span class="sxs-lookup"><span data-stu-id="09633-104">Syntax</span></span>  
  
```  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="09633-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="09633-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="09633-106">[in]バッファーの長さを`pcSig`パラメーターをポイントします。</span><span class="sxs-lookup"><span data-stu-id="09633-106">[in] The length of the buffer that the `pcSig` parameter points to.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="09633-107">[out]ポインター、`ULONG32`シグネチャの格納に必要なバッファーの文字のサイズを受け取る。</span><span class="sxs-lookup"><span data-stu-id="09633-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="09633-108">[out]署名を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="09633-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09633-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="09633-109">Return Value</span></span>  
 <span data-ttu-id="09633-110">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="09633-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09633-111">要件</span><span class="sxs-lookup"><span data-stu-id="09633-111">Requirements</span></span>  
 <span data-ttu-id="09633-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="09633-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09633-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="09633-113">See Also</span></span>  
 [<span data-ttu-id="09633-114">ISymUnmanagedConstant インターフェイス</span><span class="sxs-lookup"><span data-stu-id="09633-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 [<span data-ttu-id="09633-115">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="09633-115">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)  
 [<span data-ttu-id="09633-116">GetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="09633-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
