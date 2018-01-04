---
title: "ISymUnmanagedMethod::GetRootScope メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetRootScope
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetRootScope
helpviewer_keywords:
- ISymUnmanagedMethod::GetRootScope method [.NET Framework debugging]
- GetRootScope method [.NET Framework debugging]
ms.assetid: 7d58caac-2e75-4dfa-9249-32d8a624b247
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e7fe3d2934345fbc89b4a2c7747abb867a20df20
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedmethodgetrootscope-method"></a><span data-ttu-id="f9c57-102">ISymUnmanagedMethod::GetRootScope メソッド</span><span class="sxs-lookup"><span data-stu-id="f9c57-102">ISymUnmanagedMethod::GetRootScope Method</span></span>
<span data-ttu-id="f9c57-103">このメソッド内でルート構文スコープを取得します。</span><span class="sxs-lookup"><span data-stu-id="f9c57-103">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="f9c57-104">このスコープはメソッド全体を囲みます。</span><span class="sxs-lookup"><span data-stu-id="f9c57-104">This scope encloses the entire method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9c57-105">構文</span><span class="sxs-lookup"><span data-stu-id="f9c57-105">Syntax</span></span>  
  
```  
HRESULT GetRootScope(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f9c57-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f9c57-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="f9c57-107">[out]設定されているポインターに返された[ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="f9c57-107">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9c57-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="f9c57-108">Return Value</span></span>  
 <span data-ttu-id="f9c57-109">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="f9c57-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9c57-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="f9c57-110">Requirements</span></span>  
 <span data-ttu-id="f9c57-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f9c57-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9c57-112">参照</span><span class="sxs-lookup"><span data-stu-id="f9c57-112">See Also</span></span>  
 [<span data-ttu-id="f9c57-113">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f9c57-113">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
