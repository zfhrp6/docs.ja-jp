---
title: "ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: d5f88656-433d-447c-b21c-2a12bed2e72a
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 96040ee5f56ade3647367c4b879c8aa9e7f460fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodgetcatchhandleriloffset-method"></a><span data-ttu-id="a19e5-102">ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="a19e5-102">ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset Method</span></span>
<span data-ttu-id="a19e5-103">参照してください[DefineCatchHandlerILOffset メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="a19e5-103">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a19e5-104">構文</span><span class="sxs-lookup"><span data-stu-id="a19e5-104">Syntax</span></span>  
  
```idl  
HRESULT GetCatchHandlerILOffset(    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a19e5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a19e5-105">Parameters</span></span>  
  
|<span data-ttu-id="a19e5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a19e5-106">Parameter</span></span>|<span data-ttu-id="a19e5-107">説明</span><span class="sxs-lookup"><span data-stu-id="a19e5-107">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="a19e5-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="a19e5-108">Return Value</span></span>  
 <span data-ttu-id="a19e5-109">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="a19e5-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a19e5-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="a19e5-110">Requirements</span></span>  
 <span data-ttu-id="a19e5-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a19e5-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a19e5-112">参照</span><span class="sxs-lookup"><span data-stu-id="a19e5-112">See Also</span></span>  
 [<span data-ttu-id="a19e5-113">ISymUnmanagedAsyncMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a19e5-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
