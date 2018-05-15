---
title: IDebuggerThreadControl::ReleaseAllRuntimeThreads メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b3623c886a48cc938be017f955fbdac1df3f10f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="e5150-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="e5150-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>
<span data-ttu-id="e5150-103">デバッグ サービスがブロックされているすべてのスレッドを解放しようとしていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="e5150-103">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5150-104">構文</span><span class="sxs-lookup"><span data-stu-id="e5150-104">Syntax</span></span>  
  
```  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="e5150-105">コメント</span><span class="sxs-lookup"><span data-stu-id="e5150-105">Remarks</span></span>  
 <span data-ttu-id="e5150-106">`ReleaseAllRuntimeThreads`メソッドは、ランタイム スレッドで呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="e5150-106">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="e5150-107">ホストに、ランタイム スレッドがブロックされている場合は、今すぐリリースに必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5150-107">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5150-108">要件</span><span class="sxs-lookup"><span data-stu-id="e5150-108">Requirements</span></span>  
 <span data-ttu-id="e5150-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e5150-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5150-110">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e5150-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e5150-111">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="e5150-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e5150-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5150-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5150-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="e5150-113">See Also</span></span>  
 [<span data-ttu-id="e5150-114">IDebuggerThreadControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e5150-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
