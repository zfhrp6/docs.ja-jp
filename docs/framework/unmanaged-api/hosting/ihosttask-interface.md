---
title: IHostTask インターフェイス
ms.date: 03/30/2017
api_name:
- IHostTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask
helpviewer_keywords:
- IHostTask interface [.NET Framework hosting]
ms.assetid: a71dbbd5-64b8-47eb-9f03-8e8c85fbe2bc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: df1fb24c4003f77523ef01a4029fd19cc55a3fef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442222"
---
# <a name="ihosttask-interface"></a><span data-ttu-id="ec70d-102">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ec70d-102">IHostTask Interface</span></span>
<span data-ttu-id="ec70d-103">共通言語ランタイム (CLR) のタスクを管理するホストと通信できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="ec70d-103">Provides methods that allow the common language runtime (CLR) to communicate with the host to manage tasks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ec70d-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="ec70d-104">Methods</span></span>  
  
|<span data-ttu-id="ec70d-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="ec70d-105">Method</span></span>|<span data-ttu-id="ec70d-106">説明</span><span class="sxs-lookup"><span data-stu-id="ec70d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ec70d-107">Alert メソッド</span><span class="sxs-lookup"><span data-stu-id="ec70d-107">Alert Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|<span data-ttu-id="ec70d-108">要求のホストが現在のタスクを wake`IHostTask`インスタンス、タスクを中止できるようにします。</span><span class="sxs-lookup"><span data-stu-id="ec70d-108">Requests that the host wake the task represented by the current `IHostTask` instance, so the task can be aborted.</span></span>|  
|[<span data-ttu-id="ec70d-109">GetPriority メソッド</span><span class="sxs-lookup"><span data-stu-id="ec70d-109">GetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|<span data-ttu-id="ec70d-110">現在で表されるタスクのスレッド優先度レベルを取得`IHostTask`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="ec70d-110">Gets the thread priority level of the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="ec70d-111">Join メソッド</span><span class="sxs-lookup"><span data-stu-id="ec70d-111">Join Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|<span data-ttu-id="ec70d-112">現在で表されるタスクまで呼び出し元のタスクをブロック`IHostTask`インスタンスが完了すると、指定した時間間隔が経過すると、または[ihosttask::alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)と呼びます。</span><span class="sxs-lookup"><span data-stu-id="ec70d-112">Blocks the calling task until the task represented by the current `IHostTask` instance completes, the specified time interval elapses, or [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) is called.</span></span>|  
|[<span data-ttu-id="ec70d-113">SetCLRTask メソッド</span><span class="sxs-lookup"><span data-stu-id="ec70d-113">SetCLRTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|<span data-ttu-id="ec70d-114">関連付けます、 [ICLRTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)、現在のインスタンス`IHostTask`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="ec70d-114">Associates an [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance with the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="ec70d-115">SetPriority メソッド</span><span class="sxs-lookup"><span data-stu-id="ec70d-115">SetPriority Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|<span data-ttu-id="ec70d-116">要求スレッドの優先度を変更するホスト レベルの現在のタスクの`IHostTask`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="ec70d-116">Requests that the host adjust the thread priority level for the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="ec70d-117">Start メソッド</span><span class="sxs-lookup"><span data-stu-id="ec70d-117">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|<span data-ttu-id="ec70d-118">ホストが現在のタスクを移動要求`IHostTask`インスタンスを中断状態からコードを実行できる状態にします。</span><span class="sxs-lookup"><span data-stu-id="ec70d-118">Requests that the host move the task represented by the current `IHostTask` instance from a suspended state to a live state, in which code can be executed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec70d-119">コメント</span><span class="sxs-lookup"><span data-stu-id="ec70d-119">Remarks</span></span>  
 <span data-ttu-id="ec70d-120">CLR によって定義されたメソッドを呼び出し、`IHostTask`セットを開始するタスク、そのスレッドの優先度レベルのようにします。</span><span class="sxs-lookup"><span data-stu-id="ec70d-120">The CLR calls methods defined by `IHostTask` to start a task, set its thread priority level, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec70d-121">要件</span><span class="sxs-lookup"><span data-stu-id="ec70d-121">Requirements</span></span>  
 <span data-ttu-id="ec70d-122">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ec70d-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec70d-123">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ec70d-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ec70d-124">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="ec70d-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ec70d-125">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec70d-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec70d-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="ec70d-126">See Also</span></span>  
 [<span data-ttu-id="ec70d-127">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ec70d-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="ec70d-128">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ec70d-128">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="ec70d-129">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ec70d-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="ec70d-130">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ec70d-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
