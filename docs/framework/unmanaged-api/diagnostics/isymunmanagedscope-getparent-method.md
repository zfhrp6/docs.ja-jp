---
title: "ISymUnmanagedScope::GetParent メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope.GetParent
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope::GetParent
helpviewer_keywords:
- GetParent method [.NET Framework debugging]
- ISymUnmanagedScope::GetParent method [.NET Framework debugging]
ms.assetid: c7963c87-6ec5-49b3-a5cd-e0fe0c43f9b4
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 68215224467170962e897964483a4ce13d7b6366
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedscopegetparent-method"></a><span data-ttu-id="8252c-102">ISymUnmanagedScope::GetParent メソッド</span><span class="sxs-lookup"><span data-stu-id="8252c-102">ISymUnmanagedScope::GetParent Method</span></span>
<span data-ttu-id="8252c-103">このスコープの親スコープを取得します。</span><span class="sxs-lookup"><span data-stu-id="8252c-103">Gets the parent scope of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8252c-104">構文</span><span class="sxs-lookup"><span data-stu-id="8252c-104">Syntax</span></span>  
  
```  
HRESULT GetParent(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8252c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8252c-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="8252c-106">[out]返されたへのポインター [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="8252c-106">[out] A pointer to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8252c-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="8252c-107">Return Value</span></span>  
 <span data-ttu-id="8252c-108">メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。</span><span class="sxs-lookup"><span data-stu-id="8252c-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8252c-109">要件</span><span class="sxs-lookup"><span data-stu-id="8252c-109">Requirements</span></span>  
 <span data-ttu-id="8252c-110">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8252c-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8252c-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="8252c-111">See Also</span></span>  
 [<span data-ttu-id="8252c-112">ISymUnmanagedScope インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8252c-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 [<span data-ttu-id="8252c-113">GetChildren メソッド</span><span class="sxs-lookup"><span data-stu-id="8252c-113">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)
