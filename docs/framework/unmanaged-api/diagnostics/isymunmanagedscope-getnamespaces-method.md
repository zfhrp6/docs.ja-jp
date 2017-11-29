---
title: "ISymUnmanagedScope::GetNamespaces メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope.GetNamespaces
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope::GetNamespaces
helpviewer_keywords:
- GetNamespaces method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetNamespaces method [.NET Framework debugging]
ms.assetid: c44b0440-04bd-460a-84fb-41afecf44503
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 641ce6c4587f9f23743a3c1b5a1aeb6fb77edde7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedscopegetnamespaces-method"></a><span data-ttu-id="87e18-102">ISymUnmanagedScope::GetNamespaces メソッド</span><span class="sxs-lookup"><span data-stu-id="87e18-102">ISymUnmanagedScope::GetNamespaces Method</span></span>
<span data-ttu-id="87e18-103">このスコープ内で使用されている名前空間を取得します。</span><span class="sxs-lookup"><span data-stu-id="87e18-103">Gets the namespaces that are being used within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87e18-104">構文</span><span class="sxs-lookup"><span data-stu-id="87e18-104">Syntax</span></span>  
  
```  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces),  
        length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="87e18-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="87e18-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="87e18-106">[in] `namespaces` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="87e18-106">[in] The size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="87e18-107">[out]ポインター、`ULONG32`名前空間の格納に必要なバッファーのサイズを受け取る。</span><span class="sxs-lookup"><span data-stu-id="87e18-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="87e18-108">[out]名前空間を受け取る配列。</span><span class="sxs-lookup"><span data-stu-id="87e18-108">[out] The array that receives the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87e18-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="87e18-109">Return Value</span></span>  
 <span data-ttu-id="87e18-110">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="87e18-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87e18-111">要件</span><span class="sxs-lookup"><span data-stu-id="87e18-111">Requirements</span></span>  
 <span data-ttu-id="87e18-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="87e18-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87e18-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="87e18-113">See Also</span></span>  
 [<span data-ttu-id="87e18-114">ISymUnmanagedScope インターフェイス</span><span class="sxs-lookup"><span data-stu-id="87e18-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
