---
title: ISymUnmanagedScope::GetMethod メソッド
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ebef54baf4e560b364845a521e4b4444ed359395
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426121"
---
# <a name="isymunmanagedscopegetmethod-method"></a><span data-ttu-id="68737-102">ISymUnmanagedScope::GetMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="68737-102">ISymUnmanagedScope::GetMethod Method</span></span>
<span data-ttu-id="68737-103">このスコープに含まれているメソッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="68737-103">Gets the method that contains this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68737-104">構文</span><span class="sxs-lookup"><span data-stu-id="68737-104">Syntax</span></span>  
  
```  
HRESULT GetMethod(  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="68737-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="68737-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="68737-106">[out]返されたへのポインター [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="68737-106">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="68737-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="68737-107">Return Value</span></span>  
 <span data-ttu-id="68737-108">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="68737-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68737-109">要件</span><span class="sxs-lookup"><span data-stu-id="68737-109">Requirements</span></span>  
 <span data-ttu-id="68737-110">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="68737-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68737-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="68737-111">See Also</span></span>  
 [<span data-ttu-id="68737-112">ISymUnmanagedScope インターフェイス</span><span class="sxs-lookup"><span data-stu-id="68737-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
