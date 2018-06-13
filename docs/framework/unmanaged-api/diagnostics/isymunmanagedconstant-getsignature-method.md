---
title: ISymUnmanagedConstant::GetSignature メソッド
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ce9ce768e32434e0a1acd2fad67a0cdc99f49e18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430147"
---
# <a name="isymunmanagedconstantgetsignature-method"></a><span data-ttu-id="df14b-102">ISymUnmanagedConstant::GetSignature メソッド</span><span class="sxs-lookup"><span data-stu-id="df14b-102">ISymUnmanagedConstant::GetSignature Method</span></span>
<span data-ttu-id="df14b-103">定数の署名を取得します。</span><span class="sxs-lookup"><span data-stu-id="df14b-103">Gets the signature of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df14b-104">構文</span><span class="sxs-lookup"><span data-stu-id="df14b-104">Syntax</span></span>  
  
```  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="df14b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="df14b-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="df14b-106">[in]バッファーの長さを`pcSig`パラメーターをポイントします。</span><span class="sxs-lookup"><span data-stu-id="df14b-106">[in] The length of the buffer that the `pcSig` parameter points to.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="df14b-107">[out]ポインター、`ULONG32`シグネチャの格納に必要なバッファーの文字のサイズを受け取る。</span><span class="sxs-lookup"><span data-stu-id="df14b-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="df14b-108">[out]署名を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="df14b-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="df14b-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="df14b-109">Return Value</span></span>  
 <span data-ttu-id="df14b-110">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="df14b-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df14b-111">要件</span><span class="sxs-lookup"><span data-stu-id="df14b-111">Requirements</span></span>  
 <span data-ttu-id="df14b-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="df14b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df14b-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="df14b-113">See Also</span></span>  
 [<span data-ttu-id="df14b-114">ISymUnmanagedConstant インターフェイス</span><span class="sxs-lookup"><span data-stu-id="df14b-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 [<span data-ttu-id="df14b-115">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="df14b-115">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)  
 [<span data-ttu-id="df14b-116">GetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="df14b-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
