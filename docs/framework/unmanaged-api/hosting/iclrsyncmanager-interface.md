---
title: ICLRSyncManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager
helpviewer_keywords:
- ICLRSyncManager interface [.NET Framework hosting]
ms.assetid: a49f9d80-1c76-4ddd-8c49-34f913a5c596
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b87ccc3d6c3e957d0384499048032e35247093a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436482"
---
# <a name="iclrsyncmanager-interface"></a><span data-ttu-id="54393-102">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="54393-102">ICLRSyncManager Interface</span></span>
<span data-ttu-id="54393-103">要求されたタスクに関する情報を取得し、同期実装でデッドロックを検出するためにホストできるようにするメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="54393-103">Defines methods that allow the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="54393-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="54393-104">Methods</span></span>  
  
|<span data-ttu-id="54393-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="54393-105">Method</span></span>|<span data-ttu-id="54393-106">説明</span><span class="sxs-lookup"><span data-stu-id="54393-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="54393-107">CreateRWLockOwnerIterator メソッド</span><span class="sxs-lookup"><span data-stu-id="54393-107">CreateRWLockOwnerIterator Method</span></span>](iclrsyncmanager-createrwlockowneriterator-method.md)|<span data-ttu-id="54393-108">共通言語ランタイム (CLR) を使用して、一連のリーダー ライター ロックを待機してタスクを決定するホストの反復子を作成するように要求します。</span><span class="sxs-lookup"><span data-stu-id="54393-108">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>|  
|[<span data-ttu-id="54393-109">DeleteRWLockOwnerIterator メソッド</span><span class="sxs-lookup"><span data-stu-id="54393-109">DeleteRWLockOwnerIterator Method</span></span>](iclrsyncmanager-deleterwlockowneriterator-method.md)|<span data-ttu-id="54393-110">CLR がへの呼び出しによって作成された反復子を破棄することを要求`CreateRWLockOwnerIterator`です。</span><span class="sxs-lookup"><span data-stu-id="54393-110">Requests that the CLR destroy an iterator that was created by a call to `CreateRWLockOwnerIterator`.</span></span>|  
|[<span data-ttu-id="54393-111">GetMonitorOwner メソッド</span><span class="sxs-lookup"><span data-stu-id="54393-111">GetMonitorOwner Method</span></span>](iclrsyncmanager-getmonitorowner-method.md)|<span data-ttu-id="54393-112">指定したモニターを所有するタスクを取得します。</span><span class="sxs-lookup"><span data-stu-id="54393-112">Gets the task that owns the specified monitor.</span></span>|  
|[<span data-ttu-id="54393-113">GetRWLockOwnerNext メソッド</span><span class="sxs-lookup"><span data-stu-id="54393-113">GetRWLockOwnerNext Method</span></span>](iclrsyncmanager-getrwlockownernext-method.md)|<span data-ttu-id="54393-114">現在のリーダー ライター ロックを待機している次のタスクを取得します。</span><span class="sxs-lookup"><span data-stu-id="54393-114">Gets the next task that is waiting on the current reader-writer lock.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="54393-115">要件</span><span class="sxs-lookup"><span data-stu-id="54393-115">Requirements</span></span>  
 <span data-ttu-id="54393-116">**プラットフォーム:** を参照してください[システム要件](../../get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="54393-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54393-117">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="54393-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="54393-118">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="54393-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="54393-119">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54393-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54393-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="54393-120">See Also</span></span>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="54393-121">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="54393-121">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)  
 <span data-ttu-id="54393-122">[マネージ コードとアンマネージ スレッド処理](https://msdn.microsoft.com/library/db425c20-4b2f-4433-bf96-76071c7881e5(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="54393-122">[Managed and Unmanaged Threading](https://msdn.microsoft.com/library/db425c20-4b2f-4433-bf96-76071c7881e5(v=vs.100))</span></span>  
 [<span data-ttu-id="54393-123">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="54393-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
