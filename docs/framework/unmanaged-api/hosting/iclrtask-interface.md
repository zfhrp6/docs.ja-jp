---
title: "ICLRTask インターフェイス"
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
- ICLRTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask
helpviewer_keywords:
- ICLRTask interface [.NET Framework hosting]
ms.assetid: b3a44df3-578a-4451-b55e-70c8e7695f5e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6fcce85e56abae561b05364a925fdb6b55825669
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtask-interface"></a><span data-ttu-id="4a7d0-102">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4a7d0-102">ICLRTask Interface</span></span>
<span data-ttu-id="4a7d0-103">ホストまたは関連付けられているタスクは、CLR に通知を提供する共通言語ランタイム (CLR) の要求を行うことができるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="4a7d0-103">Provides methods that allow the host to make requests of the common language runtime (CLR), or to provide notification to the CLR about the associated task.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4a7d0-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="4a7d0-104">Methods</span></span>  
  
|<span data-ttu-id="4a7d0-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="4a7d0-105">Method</span></span>|<span data-ttu-id="4a7d0-106">説明</span><span class="sxs-lookup"><span data-stu-id="4a7d0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4a7d0-107">Abort メソッド</span><span class="sxs-lookup"><span data-stu-id="4a7d0-107">Abort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-abort-method.md)|<span data-ttu-id="4a7d0-108">CLR がタスクを中止する要求を現在`ICLRTask`インスタンスが表すです。</span><span class="sxs-lookup"><span data-stu-id="4a7d0-108">Requests that the CLR abort the task that the current `ICLRTask` instance represents.</span></span>|  
|[<span data-ttu-id="4a7d0-109">ExitTask メソッド</span><span class="sxs-lookup"><span data-stu-id="4a7d0-109">ExitTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md)|<span data-ttu-id="4a7d0-110">タスクに現在関連付けられている、CLR に通知`ICLRTask`インスタンスが終了し、タスクを正常にシャット ダウンしようとしています。</span><span class="sxs-lookup"><span data-stu-id="4a7d0-110">Notifies the CLR that the task associated with the current `ICLRTask` instance is ending, and attempts to shut the task down gracefully.</span></span>|  
|[<span data-ttu-id="4a7d0-111">GetMemStats メソッド</span><span class="sxs-lookup"><span data-stu-id="4a7d0-111">GetMemStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md)|<span data-ttu-id="4a7d0-112">現在のタスクでメモリ リソースの使用に関する統計情報を取得`ICLRTask`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="4a7d0-112">Gets statistical information on the use of memory resources by the task represented by the current `ICLRTask` instance.</span></span>|  
|[<span data-ttu-id="4a7d0-113">LocksHeld メソッド</span><span class="sxs-lookup"><span data-stu-id="4a7d0-113">LocksHeld Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-locksheld-method.md)|<span data-ttu-id="4a7d0-114">タスクで現在保持されているロックの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="4a7d0-114">Gets the number of locks currently held on the task.</span></span>|  
|[<span data-ttu-id="4a7d0-115">NeedsPriorityScheduling メソッド</span><span class="sxs-lookup"><span data-stu-id="4a7d0-115">NeedsPriorityScheduling Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-needspriorityscheduling-method.md)|<span data-ttu-id="4a7d0-116">ホストが現在によって表されるタスクの再スケジュールする高優先順位を割り当てる必要があるかどうかを示す値を取得`ICLRTask`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="4a7d0-116">Gets a value indicating whether the host should assign a high priority to rescheduling the task represented by the current `ICLRTask` instance.</span></span>|  
|[<span data-ttu-id="4a7d0-117">Reset メソッド</span><span class="sxs-lookup"><span data-stu-id="4a7d0-117">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-reset-method.md)|<span data-ttu-id="4a7d0-118">ホストが、タスクが完了し、現在を再利用する CLR を有効にことを CLR に通知`ICLRTask`を別のタスクを表すインスタンス。</span><span class="sxs-lookup"><span data-stu-id="4a7d0-118">Informs the CLR that the host has completed a task, and enables the CLR to reuse the current `ICLRTask` instance to represent another task.</span></span>|  
|[<span data-ttu-id="4a7d0-119">RudeAbort メソッド</span><span class="sxs-lookup"><span data-stu-id="4a7d0-119">RudeAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-rudeabort-method.md)|<span data-ttu-id="4a7d0-120">Clr は現在のタスクを中止する`ICLRTask`ファイナライザーが実行されるを待機せず、すぐにインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="4a7d0-120">Causes the CLR to abort the task represented by the current `ICLRTask` instance immediately, without a guarantee that finalizers will be executed.</span></span>|  
|[<span data-ttu-id="4a7d0-121">SetTaskIdentifier メソッド</span><span class="sxs-lookup"><span data-stu-id="4a7d0-121">SetTaskIdentifier Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md)|<span data-ttu-id="4a7d0-122">現在のタスクの一意の識別子を設定`ICLRTask`デバッグで使用するためのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="4a7d0-122">Sets a unique identifier for the task represented by the current `ICLRTask` instance, for use in debugging.</span></span>|  
|[<span data-ttu-id="4a7d0-123">SwitchIn メソッド</span><span class="sxs-lookup"><span data-stu-id="4a7d0-123">SwitchIn Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchin-method.md)|<span data-ttu-id="4a7d0-124">現在のタスクが表す CLR に通知`ICLRTask`インスタンスが操作可能な状態にします。</span><span class="sxs-lookup"><span data-stu-id="4a7d0-124">Notifies the CLR that the task represented by the current `ICLRTask` instance is in an operable state.</span></span>|  
|[<span data-ttu-id="4a7d0-125">SwitchOut メソッド</span><span class="sxs-lookup"><span data-stu-id="4a7d0-125">SwitchOut Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md)|<span data-ttu-id="4a7d0-126">現在のタスクが表す CLR に通知`ICLRTask`インスタンスは操作可能な状態ではありません。</span><span class="sxs-lookup"><span data-stu-id="4a7d0-126">Notifies the CLR that the task represented by the current `ICLRTask` instance is no longer in an operable state.</span></span>|  
|[<span data-ttu-id="4a7d0-127">YieldTask メソッド</span><span class="sxs-lookup"><span data-stu-id="4a7d0-127">YieldTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-yieldtask-method.md)|<span data-ttu-id="4a7d0-128">CLR make の他のタスクで使用できるプロセッサ時間を要求します。</span><span class="sxs-lookup"><span data-stu-id="4a7d0-128">Requests that the CLR make processor time available to other tasks.</span></span> <span data-ttu-id="4a7d0-129">CLR は、タスクが処理時間を得ることのできる状態になるという保証を行いません。</span><span class="sxs-lookup"><span data-stu-id="4a7d0-129">The CLR makes no guarantee that the task will be put in a state where it can yield processing time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a7d0-130">コメント</span><span class="sxs-lookup"><span data-stu-id="4a7d0-130">Remarks</span></span>  
 <span data-ttu-id="4a7d0-131">`ICLRTask` CLR のタスクの表現です。</span><span class="sxs-lookup"><span data-stu-id="4a7d0-131">An `ICLRTask` is the representation of a task for the CLR.</span></span> <span data-ttu-id="4a7d0-132">、任意の時点でコードが実行中には、タスクを実行するいると、実行を待機しているどちらかに記述できます。</span><span class="sxs-lookup"><span data-stu-id="4a7d0-132">At any point during code execution, a task can be described either as running or waiting to run.</span></span> <span data-ttu-id="4a7d0-133">ホストの呼び出し、 `ICLRTask::SwitchIn` CLR に通知するメソッドをタスクを現在`ICLRTask`インスタンスを表すは操作可能な状態にします。</span><span class="sxs-lookup"><span data-stu-id="4a7d0-133">The host calls the `ICLRTask::SwitchIn` method to notify the CLR that the task that the current `ICLRTask` instance represents is now in an operable state.</span></span> <span data-ttu-id="4a7d0-134">呼び出しの後に`ICLRTask::SwitchIn`、ホストは、ランタイムへの呼び出しで指定されたスレッド アフィニティが必要な場合を除く任意のオペレーティング システム スレッドでタスクをスケジュールすることができます、 [ihosttaskmanager::beginthreadaffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md)と[Ihosttaskmanager::endthreadaffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="4a7d0-134">After a call to `ICLRTask::SwitchIn`, the host can schedule the task on any operating system thread, except in cases where the runtime requires thread-affinity, as specified by calls to the [IHostTaskManager::BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md) and [IHostTaskManager::EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md) methods.</span></span> <span data-ttu-id="4a7d0-135">しばらくしてから、オペレーティング システムは、スレッドからタスクを削除し、実行されていない状態に配置することができます。</span><span class="sxs-lookup"><span data-stu-id="4a7d0-135">Some time later, the operating system might decide to remove the task from the thread and place it in a non-running state.</span></span> <span data-ttu-id="4a7d0-136">たとえば、タスクの同期プリミティブをブロックまたは I/O 操作の完了を待機するたびに発生するこのです。</span><span class="sxs-lookup"><span data-stu-id="4a7d0-136">For example, this might happen whenever the task blocks on synchronization primitives, or waits for I/O operations to complete.</span></span> <span data-ttu-id="4a7d0-137">ホスト呼び出し[SwitchOut](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md)が現在のタスクが表す CLR に通知`ICLRTask`インスタンスは操作可能な状態ではありません。</span><span class="sxs-lookup"><span data-stu-id="4a7d0-137">The host calls [SwitchOut](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md) to notify the CLR that the task represented by the current `ICLRTask` instance is no longer in an operable state.</span></span>  
  
 <span data-ttu-id="4a7d0-138">タスクは、通常、コードの実行の最後に終了します。</span><span class="sxs-lookup"><span data-stu-id="4a7d0-138">A task typically terminates at the end of code execution.</span></span> <span data-ttu-id="4a7d0-139">ホストを呼び出して、その時点で`ICLRTask::ExitTask`、関連付けられているを破棄する`ICLRTask`です。</span><span class="sxs-lookup"><span data-stu-id="4a7d0-139">At that time, the host calls `ICLRTask::ExitTask` to destroy the associated `ICLRTask`.</span></span> <span data-ttu-id="4a7d0-140">ただし、タスクできますもリサイクルへの呼び出しを使用して、 `ICLRTask::Reset`、これにより、`ICLRTask`再使用するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="4a7d0-140">However, tasks can also be recycled by using a call to `ICLRTask::Reset`, which allows the `ICLRTask` instance to be used again.</span></span> <span data-ttu-id="4a7d0-141">このアプローチには、繰り返しの作成とインスタンスを破棄のオーバーヘッドができないようにします。</span><span class="sxs-lookup"><span data-stu-id="4a7d0-141">This approach prevents the overhead of repeatedly creating and destroying instances.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a7d0-142">必要条件</span><span class="sxs-lookup"><span data-stu-id="4a7d0-142">Requirements</span></span>  
 <span data-ttu-id="4a7d0-143">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4a7d0-143">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a7d0-144">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4a7d0-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4a7d0-145">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="4a7d0-145">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4a7d0-146">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a7d0-146">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a7d0-147">参照</span><span class="sxs-lookup"><span data-stu-id="4a7d0-147">See Also</span></span>  
 [<span data-ttu-id="4a7d0-148">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4a7d0-148">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="4a7d0-149">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4a7d0-149">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="4a7d0-150">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4a7d0-150">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="4a7d0-151">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4a7d0-151">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="4a7d0-152">ICLRTask2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4a7d0-152">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
