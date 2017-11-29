---
title: "IHostGCManager インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostGCManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostGCManager
helpviewer_keywords: IHostGCManager interface [.NET Framework hosting]
ms.assetid: 820330a4-244c-4f67-ab5e-f24b0b3c2080
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0927b236af094b964261a9b2a49a33d1ea2b9391
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ihostgcmanager-interface"></a><span data-ttu-id="e315d-102">IHostGCManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e315d-102">IHostGCManager Interface</span></span>
<span data-ttu-id="e315d-103">ガベージ コレクションのメカニズムが共通言語ランタイム (CLR) によって実装内のイベントのホストに通知するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="e315d-103">Provides methods that notify the host of events in the garbage collection mechanism implemented by the common language runtime (CLR).</span></span>  
  
## <a name="members"></a><span data-ttu-id="e315d-104">メンバー</span><span class="sxs-lookup"><span data-stu-id="e315d-104">Members</span></span>  
  
|<span data-ttu-id="e315d-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="e315d-105">Member</span></span>|<span data-ttu-id="e315d-106">説明</span><span class="sxs-lookup"><span data-stu-id="e315d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e315d-107">SuspensionEnding メソッド</span><span class="sxs-lookup"><span data-stu-id="e315d-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md)|<span data-ttu-id="e315d-108">CLR がガベージ コレクションの中断されていたスレッド上のタスクの実行を再開することをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="e315d-108">Notifies the host that the CLR is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>|  
|[<span data-ttu-id="e315d-109">SuspensionStarting メソッド</span><span class="sxs-lookup"><span data-stu-id="e315d-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md)|<span data-ttu-id="e315d-110">CLR がガベージ コレクションを実行する、タスクの実行を中断していることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="e315d-110">Notifies the host that the CLR is suspending execution of tasks, to perform a garbage collection.</span></span>|  
|[<span data-ttu-id="e315d-111">ThreadIsBlockingForSuspension メソッド</span><span class="sxs-lookup"><span data-stu-id="e315d-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md)|<span data-ttu-id="e315d-112">メソッドの呼び出し元のスレッドは、ホストに通知のガベージ コレクションをブロックします。</span><span class="sxs-lookup"><span data-stu-id="e315d-112">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e315d-113">要件</span><span class="sxs-lookup"><span data-stu-id="e315d-113">Requirements</span></span>  
 <span data-ttu-id="e315d-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e315d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e315d-115">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e315d-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e315d-116">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="e315d-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e315d-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e315d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e315d-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="e315d-118">See Also</span></span>  
 [<span data-ttu-id="e315d-119">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e315d-119">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="e315d-120">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e315d-120">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="e315d-121">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e315d-121">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="e315d-122">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e315d-122">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="e315d-123">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e315d-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
