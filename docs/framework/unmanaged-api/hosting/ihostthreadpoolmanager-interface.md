---
title: IHostThreadPoolManager インターフェイス
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager
helpviewer_keywords:
- IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: c3a2cd90-7c4e-4374-bb87-b41befb8344f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 92097cdf735630f3537296f188bd83ea8162add2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441139"
---
# <a name="ihostthreadpoolmanager-interface"></a><span data-ttu-id="d68d2-102">IHostThreadPoolManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d68d2-102">IHostThreadPoolManager Interface</span></span>
<span data-ttu-id="d68d2-103">共通言語ランタイム (CLR) をスレッド プールを構成し、スレッド プールに作業項目をキューに登録できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="d68d2-103">Provides methods that enable the common language runtime (CLR) to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d68d2-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="d68d2-104">Methods</span></span>  
  
|<span data-ttu-id="d68d2-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="d68d2-105">Method</span></span>|<span data-ttu-id="d68d2-106">説明</span><span class="sxs-lookup"><span data-stu-id="d68d2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d68d2-107">GetAvailableThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="d68d2-107">GetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)|<span data-ttu-id="d68d2-108">現在の作業項目を処理していないスレッド プール内のスレッドの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="d68d2-108">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>|  
|[<span data-ttu-id="d68d2-109">GetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="d68d2-109">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)|<span data-ttu-id="d68d2-110">スレッド プールに同時にホストで管理されるスレッドの最大数を取得します。</span><span class="sxs-lookup"><span data-stu-id="d68d2-110">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>|  
|[<span data-ttu-id="d68d2-111">GetMinThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="d68d2-111">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)|<span data-ttu-id="d68d2-112">要求に応じるためには、ホストで管理されるアイドル状態スレッド数の最小数を取得します。</span><span class="sxs-lookup"><span data-stu-id="d68d2-112">Gets the minimum number of idle threads that the host maintains in anticipation of requests.</span></span>|  
|[<span data-ttu-id="d68d2-113">QueueUserWorkItem メソッド</span><span class="sxs-lookup"><span data-stu-id="d68d2-113">QueueUserWorkItem Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)|<span data-ttu-id="d68d2-114">関数の実行をキューに配置し、関数によって使用されるデータを格納しているオブジェクトを提供します。</span><span class="sxs-lookup"><span data-stu-id="d68d2-114">Queues a function for execution, and provides an object containing data to be used by the function.</span></span>|  
|[<span data-ttu-id="d68d2-115">SetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="d68d2-115">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)|<span data-ttu-id="d68d2-116">ホストは、スレッド プールで保持できるスレッドの最大数を設定します。</span><span class="sxs-lookup"><span data-stu-id="d68d2-116">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>|  
|[<span data-ttu-id="d68d2-117">SetMinThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="d68d2-117">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)|<span data-ttu-id="d68d2-118">要求に応じるため、ホストを維持する必要がありますアイドルのスレッドの最小数を設定します。</span><span class="sxs-lookup"><span data-stu-id="d68d2-118">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d68d2-119">コメント</span><span class="sxs-lookup"><span data-stu-id="d68d2-119">Remarks</span></span>  
 <span data-ttu-id="d68d2-120">ホストがへの呼び出しで指定された値を使用して、スレッド プールを構成する必要はありません、`SetMaxThreads`と`SetMinThreads`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="d68d2-120">The host is not required to configure the thread pool by using the values specified in calls to the `SetMaxThreads` and `SetMinThreads` methods.</span></span> <span data-ttu-id="d68d2-121">この場合、ホストは、これらのメソッドから E_NOTIMPL の HRESULT 値を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="d68d2-121">In this case, the host should return an HRESULT value of E_NOTIMPL from these methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d68d2-122">要件</span><span class="sxs-lookup"><span data-stu-id="d68d2-122">Requirements</span></span>  
 <span data-ttu-id="d68d2-123">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d68d2-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d68d2-124">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d68d2-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d68d2-125">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="d68d2-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d68d2-126">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d68d2-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d68d2-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="d68d2-127">See Also</span></span>  
 <xref:System.Threading>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="d68d2-128">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d68d2-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
