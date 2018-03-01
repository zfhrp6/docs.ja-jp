---
title: "IHostTaskManager インターフェイス"
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
- IHostTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager
helpviewer_keywords:
- IHostTaskManager interface [.NET Framework hosting]
ms.assetid: 4a0b05b9-3ef1-4607-b7c8-bd4dd43647a0
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9573891a2c27a2a92eccd0522f84175effa8037a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanager-interface"></a><span data-ttu-id="5d672-102">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5d672-102">IHostTaskManager Interface</span></span>
<span data-ttu-id="5d672-103">共通言語ランタイム (CLR)、標準のオペレーティング システムのスレッドやファイバーの関数を使用する代わりに、ホストでタスクを処理できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="5d672-103">Provides methods that allow the common language runtime (CLR) to work with tasks through the host instead of using the standard operating system threading or fiber functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5d672-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="5d672-104">Methods</span></span>  
  
|<span data-ttu-id="5d672-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="5d672-105">Method</span></span>|<span data-ttu-id="5d672-106">説明</span><span class="sxs-lookup"><span data-stu-id="5d672-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5d672-107">BeginDelayAbort メソッド</span><span class="sxs-lookup"><span data-stu-id="5d672-107">BeginDelayAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md)|<span data-ttu-id="5d672-108">現在のタスクを中止できません期間が入るマネージ コードをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="5d672-108">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>|  
|[<span data-ttu-id="5d672-109">BeginThreadAffinity メソッド</span><span class="sxs-lookup"><span data-stu-id="5d672-109">BeginThreadAffinity Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md)|<span data-ttu-id="5d672-110">マネージ コードをホストが、現在のタスクを別のオペレーティング システム スレッドに移動できない期間を入力することを通知します。</span><span class="sxs-lookup"><span data-stu-id="5d672-110">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>|  
|[<span data-ttu-id="5d672-111">CallNeedsHostHook メソッド</span><span class="sxs-lookup"><span data-stu-id="5d672-111">CallNeedsHostHook Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)|<span data-ttu-id="5d672-112">共通言語ランタイムがアンマネージ関数に指定された呼び出しをインライン展開をできるかどうかを指定するホストを有効にします。</span><span class="sxs-lookup"><span data-stu-id="5d672-112">Enables the host to specify whether the common language runtime can inline the specified call to an unmanaged function.</span></span>|  
|[<span data-ttu-id="5d672-113">CreateTask メソッド</span><span class="sxs-lookup"><span data-stu-id="5d672-113">CreateTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md)|<span data-ttu-id="5d672-114">要求のホストが新しいタスクを作成することです。</span><span class="sxs-lookup"><span data-stu-id="5d672-114">Requests that the host create a new task.</span></span>|  
|[<span data-ttu-id="5d672-115">EndDelayAbort メソッド</span><span class="sxs-lookup"><span data-stu-id="5d672-115">EndDelayAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md)|<span data-ttu-id="5d672-116">マネージ コードをホストが終了するに通知を現在のタスクを中断できない、期間、事前に呼び出した`BeginDelayAbort`です。</span><span class="sxs-lookup"><span data-stu-id="5d672-116">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to `BeginDelayAbort`.</span></span>|  
|[<span data-ttu-id="5d672-117">EndThreadAffinity メソッド</span><span class="sxs-lookup"><span data-stu-id="5d672-117">EndThreadAffinity Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md)|<span data-ttu-id="5d672-118">マネージ コードをホストが終了する、現在のタスクを別のオペレーティング システム スレッドに移動できない期間を以前の呼び出しに通知`BeginThreadAffinity`です。</span><span class="sxs-lookup"><span data-stu-id="5d672-118">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to `BeginThreadAffinity`.</span></span>|  
|[<span data-ttu-id="5d672-119">EnterRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="5d672-119">EnterRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)|<span data-ttu-id="5d672-120">アンマネージ メソッドを呼び出し、プラットフォーム呼び出しメソッドなどに返すこと実行の制御、CLR をホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="5d672-120">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the CLR.</span></span>|  
|[<span data-ttu-id="5d672-121">GetCurrentTask メソッド</span><span class="sxs-lookup"><span data-stu-id="5d672-121">GetCurrentTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md)|<span data-ttu-id="5d672-122">この呼び出しが行われる元のオペレーティング システムのスレッドで現在実行中のタスクへのインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="5d672-122">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>|  
|[<span data-ttu-id="5d672-123">GetStackGuarantee メソッド</span><span class="sxs-lookup"><span data-stu-id="5d672-123">GetStackGuarantee Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getstackguarantee-method.md)|<span data-ttu-id="5d672-124">プロセスの終了前に、スタック操作の完了後に、使用することが保証されるスタック領域の量を取得します。</span><span class="sxs-lookup"><span data-stu-id="5d672-124">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>|  
|[<span data-ttu-id="5d672-125">LeaveRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="5d672-125">LeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)|<span data-ttu-id="5d672-126">アンマネージ関数呼び出しを行うには、マネージ コードをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="5d672-126">Notifies the host that managed code is about to make a call to an unmanaged function.</span></span>|  
|[<span data-ttu-id="5d672-127">ReverseEnterRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="5d672-127">ReverseEnterRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)|<span data-ttu-id="5d672-128">呼び出しがアンマネージ コードから共通言語ランタイム (CLR) に作成されていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="5d672-128">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>|  
|[<span data-ttu-id="5d672-129">ReverseLeaveRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="5d672-129">ReverseLeaveRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)|<span data-ttu-id="5d672-130">コントロールが、CLR のままであり、さらに、マネージ コードから呼び出されたアンマネージ関数を入力することをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="5d672-130">Notifies the host that control is leaving the CLR and entering an unmanaged function that was, in turn, called from managed code.</span></span>|  
|[<span data-ttu-id="5d672-131">SetCLRTaskManager メソッド</span><span class="sxs-lookup"><span data-stu-id="5d672-131">SetCLRTaskManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setclrtaskmanager-method.md)|<span data-ttu-id="5d672-132">により、ホストへのインターフェイス ポインターで、 [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)インスタンスの CLR によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="5d672-132">Provides the host with an interface pointer to an [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="5d672-133">SetLocale メソッド</span><span class="sxs-lookup"><span data-stu-id="5d672-133">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)|<span data-ttu-id="5d672-134">CLR の現在のタスクのロケールが変更されたことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="5d672-134">Notifies the host that the CLR has changed the locale on the current task.</span></span>|  
|[<span data-ttu-id="5d672-135">SetStackGuarantee メソッド</span><span class="sxs-lookup"><span data-stu-id="5d672-135">SetStackGuarantee Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setstackguarantee-method.md)|<span data-ttu-id="5d672-136">内部使用専用に予約されています。</span><span class="sxs-lookup"><span data-stu-id="5d672-136">Reserved for internal use only.</span></span>|  
|[<span data-ttu-id="5d672-137">SetUILocale メソッド</span><span class="sxs-lookup"><span data-stu-id="5d672-137">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)|<span data-ttu-id="5d672-138">現在のタスクのユーザー インターフェイスのロケールが変更されたことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="5d672-138">Notifies the host that the user interface locale has been changed on the current task.</span></span>|  
|[<span data-ttu-id="5d672-139">Sleep メソッド</span><span class="sxs-lookup"><span data-stu-id="5d672-139">Sleep Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md)|<span data-ttu-id="5d672-140">現在のタスクがスリープ状態にしようとしていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="5d672-140">Notifies the host that the current task is going to sleep.</span></span>|  
|[<span data-ttu-id="5d672-141">SwitchToTask メソッド</span><span class="sxs-lookup"><span data-stu-id="5d672-141">SwitchToTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md)|<span data-ttu-id="5d672-142">現在のタスクを切り離すことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="5d672-142">Notifies the host that it should switch out the current task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d672-143">コメント</span><span class="sxs-lookup"><span data-stu-id="5d672-143">Remarks</span></span>  
 <span data-ttu-id="5d672-144">`IHostTaskManager`CLR タスクを作成および管理には、マネージとアンマネージ コードは逆から制御が転送されるときにアクションを実行し、特定のアクションを指定するためのフックを提供するホストことができます、コードの実行中に取ることはできません。</span><span class="sxs-lookup"><span data-stu-id="5d672-144">`IHostTaskManager` allows the CLR to create and manage tasks, to provide hooks for the host to take action when control transfers from managed to unmanaged code and vice versa, and to specify certain actions the host can and cannot take during code execution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d672-145">必要条件</span><span class="sxs-lookup"><span data-stu-id="5d672-145">Requirements</span></span>  
 <span data-ttu-id="5d672-146">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5d672-146">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d672-147">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5d672-147">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5d672-148">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="5d672-148">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5d672-149">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d672-149">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d672-150">参照</span><span class="sxs-lookup"><span data-stu-id="5d672-150">See Also</span></span>  
 [<span data-ttu-id="5d672-151">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5d672-151">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="5d672-152">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5d672-152">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="5d672-153">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5d672-153">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="5d672-154">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5d672-154">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
