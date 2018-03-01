---
title: "IHostSyncManager インターフェイス"
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
- IHostSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager
helpviewer_keywords:
- IHostSyncManager interface [.NET Framework hosting]
ms.assetid: 2e081a37-6a28-4c93-b7ab-1c96a464637c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b51e1dd9219c30eb4918bf1e331c96585f7c03ac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsyncmanager-interface"></a><span data-ttu-id="98bb7-102">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="98bb7-102">IHostSyncManager Interface</span></span>
<span data-ttu-id="98bb7-103">共通言語ランタイム (CLR) に、Win32 の同期の関数を使用する代わりに、ホストを呼び出すことによって同期プリミティブを作成できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="98bb7-103">Provides methods that allow the common language runtime (CLR) to create synchronization primitives by calling the host instead of using the Win32 synchronization functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="98bb7-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="98bb7-104">Methods</span></span>  
  
|<span data-ttu-id="98bb7-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="98bb7-105">Method</span></span>|<span data-ttu-id="98bb7-106">説明</span><span class="sxs-lookup"><span data-stu-id="98bb7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="98bb7-107">CreateAutoEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="98bb7-107">CreateAutoEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createautoevent-method.md)|<span data-ttu-id="98bb7-108">自動リセット イベント オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="98bb7-108">Creates an auto-reset event object.</span></span>|  
|[<span data-ttu-id="98bb7-109">CreateCrst メソッド</span><span class="sxs-lookup"><span data-stu-id="98bb7-109">CreateCrst Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrst-method.md)|<span data-ttu-id="98bb7-110">同期のためのクリティカル セクション オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="98bb7-110">Creates a critical section object for synchronization.</span></span>|  
|[<span data-ttu-id="98bb7-111">CreateCrstWithSpinCount メソッド</span><span class="sxs-lookup"><span data-stu-id="98bb7-111">CreateCrstWithSpinCount Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrstwithspincount-method.md)|<span data-ttu-id="98bb7-112">同期用のスピン カウントをクリティカル セクション オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="98bb7-112">Creates a critical section object with spin count for synchronization.</span></span>|  
|[<span data-ttu-id="98bb7-113">CreateManualEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="98bb7-113">CreateManualEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmanualevent-method.md)|<span data-ttu-id="98bb7-114">手動リセット イベント オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="98bb7-114">Creates a manual-reset event object.</span></span>|  
|[<span data-ttu-id="98bb7-115">CreateMonitorEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="98bb7-115">CreateMonitorEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)|<span data-ttu-id="98bb7-116">監視対象の自動リセット イベント オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="98bb7-116">Creates a monitored auto-reset event object.</span></span>|  
|[<span data-ttu-id="98bb7-117">CreateRWLockReaderEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="98bb7-117">CreateRWLockReaderEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockreaderevent-method.md)|<span data-ttu-id="98bb7-118">リーダー ロックを実装するための手動リセット イベント オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="98bb7-118">Creates a manual-reset event object for the implementation of a reader lock.</span></span>|  
|[<span data-ttu-id="98bb7-119">CreateRWLockWriterEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="98bb7-119">CreateRWLockWriterEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockwriterevent-method.md)|<span data-ttu-id="98bb7-120">ライター ロックの実装の自動リセット イベント オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="98bb7-120">Creates an auto-reset event object for the implementation of a writer lock.</span></span>|  
|[<span data-ttu-id="98bb7-121">CreateSemaphore メソッド</span><span class="sxs-lookup"><span data-stu-id="98bb7-121">CreateSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|<span data-ttu-id="98bb7-122">作成、 [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)待機イベントのセマフォとして使用する CLR のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="98bb7-122">Creates an [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) object for the CLR to use as a semaphore for wait events.</span></span>|  
|[<span data-ttu-id="98bb7-123">SetCLRSyncManager メソッド</span><span class="sxs-lookup"><span data-stu-id="98bb7-123">SetCLRSyncManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|<span data-ttu-id="98bb7-124">セット、 [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)に現在関連付けインスタンス`IHostSyncManager`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="98bb7-124">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current `IHostSyncManager` instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98bb7-125">コメント</span><span class="sxs-lookup"><span data-stu-id="98bb7-125">Remarks</span></span>  
 <span data-ttu-id="98bb7-126">CLR のホストの実装を検出する`IHostSyncManager`を呼び出して、 [ihostcontrol::gethostmanager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)メソッドを`IID`IID_IHostSyncManager のです。</span><span class="sxs-lookup"><span data-stu-id="98bb7-126">The CLR discovers the host's implementation of `IHostSyncManager` by calling the [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) method with an `IID` of IID_IHostSyncManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98bb7-127">必要条件</span><span class="sxs-lookup"><span data-stu-id="98bb7-127">Requirements</span></span>  
 <span data-ttu-id="98bb7-128">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="98bb7-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98bb7-129">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="98bb7-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="98bb7-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="98bb7-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="98bb7-131">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98bb7-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98bb7-132">参照</span><span class="sxs-lookup"><span data-stu-id="98bb7-132">See Also</span></span>  
 [<span data-ttu-id="98bb7-133">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="98bb7-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="98bb7-134">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="98bb7-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
