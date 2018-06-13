---
title: IHostGCManager インターフェイス
ms.date: 03/30/2017
api_name:
- IHostGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager
helpviewer_keywords:
- IHostGCManager interface [.NET Framework hosting]
ms.assetid: 820330a4-244c-4f67-ab5e-f24b0b3c2080
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4eac8abede82915386abc19c4c8389932451df4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440377"
---
# <a name="ihostgcmanager-interface"></a><span data-ttu-id="69eba-102">IHostGCManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="69eba-102">IHostGCManager Interface</span></span>
<span data-ttu-id="69eba-103">ガベージ コレクションのメカニズムが共通言語ランタイム (CLR) によって実装内のイベントのホストに通知するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="69eba-103">Provides methods that notify the host of events in the garbage collection mechanism implemented by the common language runtime (CLR).</span></span>  
  
## <a name="members"></a><span data-ttu-id="69eba-104">メンバー</span><span class="sxs-lookup"><span data-stu-id="69eba-104">Members</span></span>  
  
|<span data-ttu-id="69eba-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="69eba-105">Member</span></span>|<span data-ttu-id="69eba-106">説明</span><span class="sxs-lookup"><span data-stu-id="69eba-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="69eba-107">SuspensionEnding メソッド</span><span class="sxs-lookup"><span data-stu-id="69eba-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md)|<span data-ttu-id="69eba-108">CLR がガベージ コレクションの中断されていたスレッド上のタスクの実行を再開することをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="69eba-108">Notifies the host that the CLR is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>|  
|[<span data-ttu-id="69eba-109">SuspensionStarting メソッド</span><span class="sxs-lookup"><span data-stu-id="69eba-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md)|<span data-ttu-id="69eba-110">CLR がガベージ コレクションを実行する、タスクの実行を中断していることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="69eba-110">Notifies the host that the CLR is suspending execution of tasks, to perform a garbage collection.</span></span>|  
|[<span data-ttu-id="69eba-111">ThreadIsBlockingForSuspension メソッド</span><span class="sxs-lookup"><span data-stu-id="69eba-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md)|<span data-ttu-id="69eba-112">メソッドの呼び出し元のスレッドは、ホストに通知のガベージ コレクションをブロックします。</span><span class="sxs-lookup"><span data-stu-id="69eba-112">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="69eba-113">要件</span><span class="sxs-lookup"><span data-stu-id="69eba-113">Requirements</span></span>  
 <span data-ttu-id="69eba-114">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="69eba-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69eba-115">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="69eba-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="69eba-116">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="69eba-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="69eba-117">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69eba-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69eba-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="69eba-118">See Also</span></span>  
 [<span data-ttu-id="69eba-119">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="69eba-119">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="69eba-120">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="69eba-120">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="69eba-121">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="69eba-121">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="69eba-122">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="69eba-122">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="69eba-123">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="69eba-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
