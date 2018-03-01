---
title: "ISymUnmanagedMethod::GetToken メソッド"
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
- ISymUnmanagedMethod.GetToken
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetToken
helpviewer_keywords:
- ISymUnmanagedMethod::GetToken method [.NET Framework debugging]
- GetToken method, ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: 4effbe95-c36e-4a45-8b2a-ee21339415fb
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bfdc070c21c7929166bfa957c0e0dd63da80f761
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedmethodgettoken-method"></a><span data-ttu-id="0618a-102">ISymUnmanagedMethod::GetToken メソッド</span><span class="sxs-lookup"><span data-stu-id="0618a-102">ISymUnmanagedMethod::GetToken Method</span></span>
<span data-ttu-id="0618a-103">このメソッドのメタデータ トークンを返します。</span><span class="sxs-lookup"><span data-stu-id="0618a-103">Returns the metadata token for this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0618a-104">構文</span><span class="sxs-lookup"><span data-stu-id="0618a-104">Syntax</span></span>  
  
```  
HRESULT GetToken(  
   [out, retval]  mdMethodDef  *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0618a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0618a-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="0618a-106">[out]ポインター、`mdMethodDef`メタデータの格納に必要なバッファーの文字のサイズを受け取る。</span><span class="sxs-lookup"><span data-stu-id="0618a-106">[out] A pointer to a `mdMethodDef` that receives the size, in characters, of the buffer required to contain the metadata.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0618a-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="0618a-107">Return Value</span></span>  
 <span data-ttu-id="0618a-108">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="0618a-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0618a-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="0618a-109">Requirements</span></span>  
 <span data-ttu-id="0618a-110">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0618a-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0618a-111">参照</span><span class="sxs-lookup"><span data-stu-id="0618a-111">See Also</span></span>  
 [<span data-ttu-id="0618a-112">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0618a-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
