---
title: ISymUnmanagedMethod::GetRootScope メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetRootScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetRootScope
helpviewer_keywords:
- ISymUnmanagedMethod::GetRootScope method [.NET Framework debugging]
- GetRootScope method [.NET Framework debugging]
ms.assetid: 7d58caac-2e75-4dfa-9249-32d8a624b247
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 417ce67d807fddd3b99ceff4b05f1524db3044e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430529"
---
# <a name="isymunmanagedmethodgetrootscope-method"></a><span data-ttu-id="13c20-102">ISymUnmanagedMethod::GetRootScope メソッド</span><span class="sxs-lookup"><span data-stu-id="13c20-102">ISymUnmanagedMethod::GetRootScope Method</span></span>
<span data-ttu-id="13c20-103">このメソッド内でルート構文スコープを取得します。</span><span class="sxs-lookup"><span data-stu-id="13c20-103">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="13c20-104">このスコープはメソッド全体を囲みます。</span><span class="sxs-lookup"><span data-stu-id="13c20-104">This scope encloses the entire method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13c20-105">構文</span><span class="sxs-lookup"><span data-stu-id="13c20-105">Syntax</span></span>  
  
```  
HRESULT GetRootScope(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="13c20-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="13c20-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="13c20-107">[out]設定されているポインターに返された[ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="13c20-107">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13c20-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="13c20-108">Return Value</span></span>  
 <span data-ttu-id="13c20-109">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="13c20-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13c20-110">要件</span><span class="sxs-lookup"><span data-stu-id="13c20-110">Requirements</span></span>  
 <span data-ttu-id="13c20-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="13c20-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13c20-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="13c20-112">See Also</span></span>  
 [<span data-ttu-id="13c20-113">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="13c20-113">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
