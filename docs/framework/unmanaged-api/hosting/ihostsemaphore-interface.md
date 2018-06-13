---
title: IHostSemaphore インターフェイス
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 103deb5ec46ba8c1d385c5339bc52a0c220c4c93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439769"
---
# <a name="ihostsemaphore-interface"></a><span data-ttu-id="9a26c-102">IHostSemaphore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a26c-102">IHostSemaphore Interface</span></span>
<span data-ttu-id="9a26c-103">ホストのスレッド処理のセマフォの実装を表します。</span><span class="sxs-lookup"><span data-stu-id="9a26c-103">Represents the host's implementation of a semaphore for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9a26c-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="9a26c-104">Methods</span></span>  
  
|<span data-ttu-id="9a26c-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="9a26c-105">Method</span></span>|<span data-ttu-id="9a26c-106">説明</span><span class="sxs-lookup"><span data-stu-id="9a26c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9a26c-107">ReleaseSemaphore メソッド</span><span class="sxs-lookup"><span data-stu-id="9a26c-107">ReleaseSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)|<span data-ttu-id="9a26c-108">現在のカウントを増やします`IHostSemaphore`インスタンスを指定の量。</span><span class="sxs-lookup"><span data-stu-id="9a26c-108">Increases the count of the current `IHostSemaphore` instance by the specified amount.</span></span>|  
|[<span data-ttu-id="9a26c-109">Wait メソッド</span><span class="sxs-lookup"><span data-stu-id="9a26c-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md)|<span data-ttu-id="9a26c-110">現在の原因`IHostSemaphore`が所有するまで待機するインスタンスまたは指定された時間が経過する量。</span><span class="sxs-lookup"><span data-stu-id="9a26c-110">Causes the current `IHostSemaphore` instance to wait until it is owned or the specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9a26c-111">要件</span><span class="sxs-lookup"><span data-stu-id="9a26c-111">Requirements</span></span>  
 <span data-ttu-id="9a26c-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9a26c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a26c-113">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9a26c-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9a26c-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="9a26c-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a26c-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a26c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a26c-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a26c-116">See Also</span></span>  
 [<span data-ttu-id="9a26c-117">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a26c-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="9a26c-118">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a26c-118">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="9a26c-119">IHostManualEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a26c-119">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="9a26c-120">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a26c-120">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="9a26c-121">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a26c-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
