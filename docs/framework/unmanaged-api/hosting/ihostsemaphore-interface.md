---
title: "IHostSemaphore インターフェイス"
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
- IHostSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore
helpviewer_keywords:
- IHostSemaphore interface [.NET Framework hosting]
ms.assetid: c0765321-656c-441e-bab5-58176292be1e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bcc6a9a7847932e9e469cdbffc9792e1d5860570
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsemaphore-interface"></a><span data-ttu-id="43c6d-102">IHostSemaphore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="43c6d-102">IHostSemaphore Interface</span></span>
<span data-ttu-id="43c6d-103">ホストのスレッド処理のセマフォの実装を表します。</span><span class="sxs-lookup"><span data-stu-id="43c6d-103">Represents the host's implementation of a semaphore for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="43c6d-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="43c6d-104">Methods</span></span>  
  
|<span data-ttu-id="43c6d-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="43c6d-105">Method</span></span>|<span data-ttu-id="43c6d-106">説明</span><span class="sxs-lookup"><span data-stu-id="43c6d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="43c6d-107">ReleaseSemaphore メソッド</span><span class="sxs-lookup"><span data-stu-id="43c6d-107">ReleaseSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)|<span data-ttu-id="43c6d-108">現在のカウントを増やします`IHostSemaphore`インスタンスを指定の量。</span><span class="sxs-lookup"><span data-stu-id="43c6d-108">Increases the count of the current `IHostSemaphore` instance by the specified amount.</span></span>|  
|[<span data-ttu-id="43c6d-109">Wait メソッド</span><span class="sxs-lookup"><span data-stu-id="43c6d-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md)|<span data-ttu-id="43c6d-110">現在の原因`IHostSemaphore`が所有するまで待機するインスタンスまたは指定された時間が経過する量。</span><span class="sxs-lookup"><span data-stu-id="43c6d-110">Causes the current `IHostSemaphore` instance to wait until it is owned or the specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="43c6d-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="43c6d-111">Requirements</span></span>  
 <span data-ttu-id="43c6d-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="43c6d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43c6d-113">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="43c6d-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="43c6d-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="43c6d-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="43c6d-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43c6d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43c6d-116">参照</span><span class="sxs-lookup"><span data-stu-id="43c6d-116">See Also</span></span>  
 [<span data-ttu-id="43c6d-117">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="43c6d-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="43c6d-118">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="43c6d-118">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="43c6d-119">IHostManualEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="43c6d-119">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="43c6d-120">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="43c6d-120">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="43c6d-121">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="43c6d-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
