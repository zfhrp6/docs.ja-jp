---
title: "ISymUnmanagedMethod::GetScopeFromOffset メソッド"
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
- ISymUnmanagedMethod.GetScopeFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetScopeFromOffset
helpviewer_keywords:
- GetScopeFromOffset method [.NET Framework debugging]
- ISymUnmanagedMethod::GetScopeFromOffset method [.NET Framework debugging]
ms.assetid: d14cf210-81f8-46e1-8b19-6ddec0ba8b11
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 890fd702bc2edb5714dc9c91a618c6420a11a27a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="ea4c3-102">ISymUnmanagedMethod::GetScopeFromOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="ea4c3-102">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>
<span data-ttu-id="ea4c3-103">このメソッドを指定したオフセットを囲む内で最も外側の構文のスコープを取得します。</span><span class="sxs-lookup"><span data-stu-id="ea4c3-103">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="ea4c3-104">ローカル変数の検索を開始するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="ea4c3-104">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea4c3-105">構文</span><span class="sxs-lookup"><span data-stu-id="ea4c3-105">Syntax</span></span>  
  
```  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ea4c3-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ea4c3-106">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="ea4c3-107">[in]A`ULONG`オフセットを格納しています。</span><span class="sxs-lookup"><span data-stu-id="ea4c3-107">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="ea4c3-108">[out]設定されているポインターに返された[ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="ea4c3-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ea4c3-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="ea4c3-109">Return Value</span></span>  
 <span data-ttu-id="ea4c3-110">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="ea4c3-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea4c3-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="ea4c3-111">Requirements</span></span>  
 <span data-ttu-id="ea4c3-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ea4c3-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea4c3-113">参照</span><span class="sxs-lookup"><span data-stu-id="ea4c3-113">See Also</span></span>  
 [<span data-ttu-id="ea4c3-114">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ea4c3-114">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
