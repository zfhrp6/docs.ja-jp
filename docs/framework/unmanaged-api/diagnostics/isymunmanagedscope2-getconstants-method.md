---
title: "ISymUnmanagedScope2::GetConstants メソッド"
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
- ISymUnmanagedScope2.GetConstants
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstants
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstants method [.NET Framework debugging]
- GetConstants method [.NET Framework debugging]
ms.assetid: f241b620-9ec5-42fd-92ef-3b22329db72a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: da0d2d39fcc1de8435c7af49a912764c79eb6583
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedscope2getconstants-method"></a><span data-ttu-id="39a09-102">ISymUnmanagedScope2::GetConstants メソッド</span><span class="sxs-lookup"><span data-stu-id="39a09-102">ISymUnmanagedScope2::GetConstants Method</span></span>
<span data-ttu-id="39a09-103">このスコープ内で定義されているローカル定数を取得します。</span><span class="sxs-lookup"><span data-stu-id="39a09-103">Gets the local constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39a09-104">構文</span><span class="sxs-lookup"><span data-stu-id="39a09-104">Syntax</span></span>  
  
```  
HRESULT GetConstants(  
     [in]  ULONG32  cConstants,  
     [out] ULONG32  *pcConstants,  
     [out, size_is(cConstants),  
         length_is(*pcConstants)] ISymUnmanagedConstant*   
             constants[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="39a09-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="39a09-105">Parameters</span></span>  
 `cConstants`  
 <span data-ttu-id="39a09-106">[in]バッファーの長さを`pcConstants`パラメーターをポイントします。</span><span class="sxs-lookup"><span data-stu-id="39a09-106">[in] The length of the buffer that the `pcConstants` parameter points to.</span></span>  
  
 `pcConstants`  
 <span data-ttu-id="39a09-107">[out]ポインター、`ULONG32`定数の格納に必要なバッファーの文字のサイズを受け取る。</span><span class="sxs-lookup"><span data-stu-id="39a09-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
 `constants`  
 <span data-ttu-id="39a09-108">[out]定数を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="39a09-108">[out] The buffer that stores the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39a09-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="39a09-109">Return Value</span></span>  
 <span data-ttu-id="39a09-110">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="39a09-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39a09-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="39a09-111">Requirements</span></span>  
 <span data-ttu-id="39a09-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="39a09-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39a09-113">参照</span><span class="sxs-lookup"><span data-stu-id="39a09-113">See Also</span></span>  
 [<span data-ttu-id="39a09-114">ISymUnmanagedScope2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="39a09-114">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
