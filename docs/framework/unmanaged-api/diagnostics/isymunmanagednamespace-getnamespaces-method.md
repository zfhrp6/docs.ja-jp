---
title: "ISymUnmanagedNamespace::GetNamespaces メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedNamespace.GetNamespaces
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedNamespace::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedNamespace::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 0ea9d9af-8709-4a46-872b-f54d9e840088
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ef84358443520aa0548ef2244c2537b7a593f9e3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagednamespacegetnamespaces-method"></a><span data-ttu-id="8c25e-102">ISymUnmanagedNamespace::GetNamespaces メソッド</span><span class="sxs-lookup"><span data-stu-id="8c25e-102">ISymUnmanagedNamespace::GetNamespaces Method</span></span>
<span data-ttu-id="8c25e-103">この名前空間の子を取得します。</span><span class="sxs-lookup"><span data-stu-id="8c25e-103">Gets the children of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c25e-104">構文</span><span class="sxs-lookup"><span data-stu-id="8c25e-104">Syntax</span></span>  
  
```  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces), length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8c25e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c25e-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="8c25e-106">[in]A`ULONG32`のサイズを示す、`namespaces`配列。</span><span class="sxs-lookup"><span data-stu-id="8c25e-106">[in] A `ULONG32` that indicates the size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="8c25e-107">[out]ポインター、`ULONG32`名前空間の格納に必要なバッファーの文字のサイズを受け取る。</span><span class="sxs-lookup"><span data-stu-id="8c25e-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="8c25e-108">[out]名前空間を格納しているバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8c25e-108">[out] A pointer to the buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c25e-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="8c25e-109">Return Value</span></span>  
 <span data-ttu-id="8c25e-110">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="8c25e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c25e-111">要件</span><span class="sxs-lookup"><span data-stu-id="8c25e-111">Requirements</span></span>  
 <span data-ttu-id="8c25e-112">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8c25e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c25e-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="8c25e-113">See Also</span></span>  
 [<span data-ttu-id="8c25e-114">ISymUnmanagedNamespace インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c25e-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
