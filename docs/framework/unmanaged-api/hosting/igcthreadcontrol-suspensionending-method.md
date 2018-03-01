---
title: "IGCThreadControl::SuspensionEnding メソッド"
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
- IGCThreadControl.SuspensionEnding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SuspensionEnding
helpviewer_keywords:
- IGCThreadControl::SuspensionEnding method [.NET Framework hosting]
- SuspensionEnding method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 70814265-c734-4ddc-9502-fe8b28d2b414
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3d17d9d2d676b83c21bea46e47914fecbec9ccf4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="igcthreadcontrolsuspensionending-method"></a><span data-ttu-id="90981-102">IGCThreadControl::SuspensionEnding メソッド</span><span class="sxs-lookup"><span data-stu-id="90981-102">IGCThreadControl::SuspensionEnding Method</span></span>
<span data-ttu-id="90981-103">ランタイムがガベージ コレクションまたはその他の中断の後のスレッドを再開することをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="90981-103">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90981-104">構文</span><span class="sxs-lookup"><span data-stu-id="90981-104">Syntax</span></span>  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="90981-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="90981-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="90981-106">[in]ガベージ コレクションが実行されて生成されます。</span><span class="sxs-lookup"><span data-stu-id="90981-106">[in] The generation on which a garbage collection has been performed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90981-107">コメント</span><span class="sxs-lookup"><span data-stu-id="90981-107">Remarks</span></span>  
 <span data-ttu-id="90981-108">中にすべてのスレッドは再スケジュールしないで、`SuspensionEnding`コールバック。</span><span class="sxs-lookup"><span data-stu-id="90981-108">Do not reschedule any threads during the `SuspensionEnding` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90981-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="90981-109">Requirements</span></span>  
 <span data-ttu-id="90981-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="90981-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90981-111">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="90981-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="90981-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="90981-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="90981-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90981-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90981-114">参照</span><span class="sxs-lookup"><span data-stu-id="90981-114">See Also</span></span>  
 [<span data-ttu-id="90981-115">IGCThreadControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="90981-115">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
