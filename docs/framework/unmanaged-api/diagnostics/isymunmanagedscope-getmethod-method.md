---
title: "ISymUnmanagedScope::GetMethod メソッド"
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
- ISymUnmanagedScope.GetMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetMethod method [.NET Framework debugging]
ms.assetid: a61866ee-221a-45b9-a1b7-395825b77872
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e4756ff1f373f09a96daa64c1fb01875274a6d0e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedscopegetmethod-method"></a><span data-ttu-id="d88d7-102">ISymUnmanagedScope::GetMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="d88d7-102">ISymUnmanagedScope::GetMethod Method</span></span>
<span data-ttu-id="d88d7-103">このスコープに含まれているメソッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="d88d7-103">Gets the method that contains this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d88d7-104">構文</span><span class="sxs-lookup"><span data-stu-id="d88d7-104">Syntax</span></span>  
  
```  
HRESULT GetMethod(  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d88d7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d88d7-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="d88d7-106">[out]返されたへのポインター [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="d88d7-106">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d88d7-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="d88d7-107">Return Value</span></span>  
 <span data-ttu-id="d88d7-108">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="d88d7-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d88d7-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="d88d7-109">Requirements</span></span>  
 <span data-ttu-id="d88d7-110">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d88d7-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d88d7-111">参照</span><span class="sxs-lookup"><span data-stu-id="d88d7-111">See Also</span></span>  
 [<span data-ttu-id="d88d7-112">ISymUnmanagedScope インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d88d7-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
