---
title: "ISymUnmanagedScope::GetLocalCount メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope.GetLocalCount
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope::GetLocalCount
helpviewer_keywords:
- GetLocalCount method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocalCount method [.NET Framework debugging]
ms.assetid: 3ede8fb5-f655-4088-8e19-9c53812588a8
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: de8f0ee3e2a1cc13a9bdb0f59aaecd4592ea7fdc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedscopegetlocalcount-method"></a><span data-ttu-id="8aa91-102">ISymUnmanagedScope::GetLocalCount メソッド</span><span class="sxs-lookup"><span data-stu-id="8aa91-102">ISymUnmanagedScope::GetLocalCount Method</span></span>
<span data-ttu-id="8aa91-103">このスコープ内で定義されているローカル変数の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="8aa91-103">Gets a count of the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8aa91-104">構文</span><span class="sxs-lookup"><span data-stu-id="8aa91-104">Syntax</span></span>  
  
```  
HRESULT GetLocalCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8aa91-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8aa91-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="8aa91-106">[out]ポインター、`ULONG32`ローカル変数の数を受け取る。</span><span class="sxs-lookup"><span data-stu-id="8aa91-106">[out] A pointer to a `ULONG32` that receives the count of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8aa91-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="8aa91-107">Return Value</span></span>  
 <span data-ttu-id="8aa91-108">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="8aa91-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8aa91-109">要件</span><span class="sxs-lookup"><span data-stu-id="8aa91-109">Requirements</span></span>  
 <span data-ttu-id="8aa91-110">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8aa91-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aa91-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="8aa91-111">See Also</span></span>  
 [<span data-ttu-id="8aa91-112">ISymUnmanagedScope インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8aa91-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
