---
title: "ISymUnmanagedVariable::GetSignature メソッド"
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
- ISymUnmanagedVariable.GetSignature
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetSignature method [.NET Framework debugging]
ms.assetid: 78c1ba28-a410-4360-805c-23a95408964a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ee403a5f92ba4eb88eca880d9bf2f858b52d4f05
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedvariablegetsignature-method"></a><span data-ttu-id="4d4d8-102">ISymUnmanagedVariable::GetSignature メソッド</span><span class="sxs-lookup"><span data-stu-id="4d4d8-102">ISymUnmanagedVariable::GetSignature Method</span></span>
<span data-ttu-id="4d4d8-103">この変数のシグネチャを取得します。</span><span class="sxs-lookup"><span data-stu-id="4d4d8-103">Gets the signature of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d4d8-104">構文</span><span class="sxs-lookup"><span data-stu-id="4d4d8-104">Syntax</span></span>  
  
```  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4d4d8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4d4d8-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="4d4d8-106">[in]バッファーの長さが指す、`sig`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="4d4d8-106">[in] The length of the buffer pointed to by the `sig` parameter.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="4d4d8-107">[out]ポインター、`ULONG32`シグネチャの格納に必要なバッファーの文字のサイズを受け取る。</span><span class="sxs-lookup"><span data-stu-id="4d4d8-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="4d4d8-108">[out]署名を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="4d4d8-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4d4d8-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="4d4d8-109">Return Value</span></span>  
 <span data-ttu-id="4d4d8-110">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="4d4d8-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d4d8-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="4d4d8-111">Requirements</span></span>  
 <span data-ttu-id="4d4d8-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4d4d8-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d4d8-113">参照</span><span class="sxs-lookup"><span data-stu-id="4d4d8-113">See Also</span></span>  
 [<span data-ttu-id="4d4d8-114">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4d4d8-114">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
