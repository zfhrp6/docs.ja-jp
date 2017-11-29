---
title: "ICLRSyncManager インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRSyncManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRSyncManager
helpviewer_keywords: ICLRSyncManager interface [.NET Framework hosting]
ms.assetid: a49f9d80-1c76-4ddd-8c49-34f913a5c596
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1e47f02a5a84b909b03c6be4e0a43c7166a1ddc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrsyncmanager-interface"></a><span data-ttu-id="0cea1-102">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0cea1-102">ICLRSyncManager Interface</span></span>
<span data-ttu-id="0cea1-103">要求されたタスクに関する情報を取得し、同期実装でデッドロックを検出するためにホストできるようにするメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="0cea1-103">Defines methods that allow the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0cea1-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="0cea1-104">Methods</span></span>  
  
|<span data-ttu-id="0cea1-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="0cea1-105">Method</span></span>|<span data-ttu-id="0cea1-106">説明</span><span class="sxs-lookup"><span data-stu-id="0cea1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0cea1-107">CreateRWLockOwnerIterator メソッド</span><span class="sxs-lookup"><span data-stu-id="0cea1-107">CreateRWLockOwnerIterator Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md)|<span data-ttu-id="0cea1-108">共通言語ランタイム (CLR) を使用して、一連のリーダー ライター ロックを待機してタスクを決定するホストの反復子を作成するように要求します。</span><span class="sxs-lookup"><span data-stu-id="0cea1-108">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>|  
|[<span data-ttu-id="0cea1-109">DeleteRWLockOwnerIterator メソッド</span><span class="sxs-lookup"><span data-stu-id="0cea1-109">DeleteRWLockOwnerIterator Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md)|<span data-ttu-id="0cea1-110">CLR がへの呼び出しによって作成された反復子を破棄することを要求`CreateRWLockOwnerIterator`です。</span><span class="sxs-lookup"><span data-stu-id="0cea1-110">Requests that the CLR destroy an iterator that was created by a call to `CreateRWLockOwnerIterator`.</span></span>|  
|[<span data-ttu-id="0cea1-111">GetMonitorOwner メソッド</span><span class="sxs-lookup"><span data-stu-id="0cea1-111">GetMonitorOwner Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md)|<span data-ttu-id="0cea1-112">指定したモニターを所有するタスクを取得します。</span><span class="sxs-lookup"><span data-stu-id="0cea1-112">Gets the task that owns the specified monitor.</span></span>|  
|[<span data-ttu-id="0cea1-113">GetRWLockOwnerNext メソッド</span><span class="sxs-lookup"><span data-stu-id="0cea1-113">GetRWLockOwnerNext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md)|<span data-ttu-id="0cea1-114">現在のリーダー ライター ロックを待機している次のタスクを取得します。</span><span class="sxs-lookup"><span data-stu-id="0cea1-114">Gets the next task that is waiting on the current reader-writer lock.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0cea1-115">要件</span><span class="sxs-lookup"><span data-stu-id="0cea1-115">Requirements</span></span>  
 <span data-ttu-id="0cea1-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0cea1-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cea1-117">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0cea1-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0cea1-118">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="0cea1-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0cea1-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cea1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cea1-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="0cea1-120">See Also</span></span>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="0cea1-121">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0cea1-121">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="0cea1-122">マネージ コードとアンマネージ スレッド処理</span><span class="sxs-lookup"><span data-stu-id="0cea1-122">Managed and Unmanaged Threading</span></span>](http://msdn.microsoft.com/en-us/db425c20-4b2f-4433-bf96-76071c7881e5)  
 [<span data-ttu-id="0cea1-123">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0cea1-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
