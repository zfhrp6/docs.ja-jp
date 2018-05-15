---
title: ISymUnmanagedConstant::GetName メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetName
helpviewer_keywords:
- ISymUnmanagedConstant::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedConstant interface [.NET Framework debugging]
ms.assetid: cbaca4e1-4473-459b-ba34-f1f59ce7c0ba
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ae532b20ec3486fe56e2dff340a5ad89941a8df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedconstantgetname-method"></a><span data-ttu-id="8ede2-102">ISymUnmanagedConstant::GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="8ede2-102">ISymUnmanagedConstant::GetName Method</span></span>
<span data-ttu-id="8ede2-103">定数の名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="8ede2-103">Gets the name of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ede2-104">構文</span><span class="sxs-lookup"><span data-stu-id="8ede2-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8ede2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8ede2-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="8ede2-106">[in]バッファーの長さを`szName`パラメーターをポイントします。</span><span class="sxs-lookup"><span data-stu-id="8ede2-106">[in] The length of the buffer that the `szName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="8ede2-107">[out]ポインター、`ULONG32`文字、終端の null を含む、名前を格納するために必要なバッファーのサイズを受け取る。</span><span class="sxs-lookup"><span data-stu-id="8ede2-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="8ede2-108">[out]名前を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="8ede2-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ede2-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="8ede2-109">Return Value</span></span>  
 <span data-ttu-id="8ede2-110">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="8ede2-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ede2-111">要件</span><span class="sxs-lookup"><span data-stu-id="8ede2-111">Requirements</span></span>  
 <span data-ttu-id="8ede2-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8ede2-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ede2-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="8ede2-113">See Also</span></span>  
 [<span data-ttu-id="8ede2-114">ISymUnmanagedConstant インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8ede2-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 [<span data-ttu-id="8ede2-115">GetSignature メソッド</span><span class="sxs-lookup"><span data-stu-id="8ede2-115">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)  
 [<span data-ttu-id="8ede2-116">GetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="8ede2-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
