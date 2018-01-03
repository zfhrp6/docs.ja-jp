---
title: "ISymUnmanagedAsyncMethod::GetKickoffMethod メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ba084444-9e68-4cde-9388-54b950670987
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 866632b3916cd2e35e7832c4d58b5988fa350c52
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodgetkickoffmethod-method"></a><span data-ttu-id="e48be-102">ISymUnmanagedAsyncMethod::GetKickoffMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="e48be-102">ISymUnmanagedAsyncMethod::GetKickoffMethod Method</span></span>
<span data-ttu-id="e48be-103">参照してください[DefineKickoffMethod メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="e48be-103">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e48be-104">構文</span><span class="sxs-lookup"><span data-stu-id="e48be-104">Syntax</span></span>  
  
```idl  
HRESULT GetKickoffMethod(    [out, retval] mdToken* kickoffMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e48be-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e48be-105">Parameters</span></span>  
  
|<span data-ttu-id="e48be-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e48be-106">Parameter</span></span>|<span data-ttu-id="e48be-107">説明</span><span class="sxs-lookup"><span data-stu-id="e48be-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="e48be-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="e48be-108">Return Value</span></span>  
 <span data-ttu-id="e48be-109">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="e48be-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e48be-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="e48be-110">Requirements</span></span>  
 <span data-ttu-id="e48be-111">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e48be-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e48be-112">参照</span><span class="sxs-lookup"><span data-stu-id="e48be-112">See Also</span></span>  
 [<span data-ttu-id="e48be-113">ISymUnmanagedAsyncMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e48be-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
