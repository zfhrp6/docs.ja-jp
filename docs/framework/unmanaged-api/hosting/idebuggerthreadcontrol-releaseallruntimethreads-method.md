---
title: "IDebuggerThreadControl::ReleaseAllRuntimeThreads メソッド"
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
- IDebuggerThreadControl.ReleaseAllRuntimeThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ReleaseAllRuntimeThreads
helpviewer_keywords:
- ReleaseAllRuntimeThreads method [.NET Framework hosting]
- IDebuggerThreadControl::ReleaseAllRuntimeThreads method [.NET Framework hosting]
ms.assetid: 1a2995ff-5f02-4b49-84dc-3a5f9cfd7d55
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8e6e2c4032a0765083177df9a6d7d5206448f566
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="74393-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="74393-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>
<span data-ttu-id="74393-103">デバッグ サービスがブロックされているすべてのスレッドを解放しようとしていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="74393-103">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74393-104">構文</span><span class="sxs-lookup"><span data-stu-id="74393-104">Syntax</span></span>  
  
```  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="74393-105">コメント</span><span class="sxs-lookup"><span data-stu-id="74393-105">Remarks</span></span>  
 <span data-ttu-id="74393-106">`ReleaseAllRuntimeThreads`メソッドは、ランタイム スレッドで呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="74393-106">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="74393-107">ホストに、ランタイム スレッドがブロックされている場合は、今すぐリリースに必要があります。</span><span class="sxs-lookup"><span data-stu-id="74393-107">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74393-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="74393-108">Requirements</span></span>  
 <span data-ttu-id="74393-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="74393-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74393-110">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="74393-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="74393-111">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="74393-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="74393-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74393-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74393-113">参照</span><span class="sxs-lookup"><span data-stu-id="74393-113">See Also</span></span>  
 [<span data-ttu-id="74393-114">IDebuggerThreadControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="74393-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
