---
title: ISymUnmanagedScope::GetLocalCount メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetLocalCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetLocalCount
helpviewer_keywords:
- GetLocalCount method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocalCount method [.NET Framework debugging]
ms.assetid: 3ede8fb5-f655-4088-8e19-9c53812588a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2f8dde609f83a0bbf040ce0e8a4f164259e8584a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427928"
---
# <a name="isymunmanagedscopegetlocalcount-method"></a><span data-ttu-id="a2f00-102">ISymUnmanagedScope::GetLocalCount メソッド</span><span class="sxs-lookup"><span data-stu-id="a2f00-102">ISymUnmanagedScope::GetLocalCount Method</span></span>
<span data-ttu-id="a2f00-103">このスコープ内で定義されているローカル変数の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="a2f00-103">Gets a count of the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2f00-104">構文</span><span class="sxs-lookup"><span data-stu-id="a2f00-104">Syntax</span></span>  
  
```  
HRESULT GetLocalCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a2f00-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a2f00-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="a2f00-106">[out]ポインター、`ULONG32`ローカル変数の数を受け取る。</span><span class="sxs-lookup"><span data-stu-id="a2f00-106">[out] A pointer to a `ULONG32` that receives the count of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2f00-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="a2f00-107">Return Value</span></span>  
 <span data-ttu-id="a2f00-108">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="a2f00-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2f00-109">要件</span><span class="sxs-lookup"><span data-stu-id="a2f00-109">Requirements</span></span>  
 <span data-ttu-id="a2f00-110">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a2f00-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2f00-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="a2f00-111">See Also</span></span>  
 [<span data-ttu-id="a2f00-112">ISymUnmanagedScope インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a2f00-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
