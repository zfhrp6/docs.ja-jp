---
title: "ICLRIoCompletionManager インターフェイス"
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
- ICLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager
helpviewer_keywords:
- ICLRIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c6c3ace6-e5e7-4450-8cc5-a9a48208c493
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 99dc183674abaff33047f070c14794150a8615f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="a68dc-102">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a68dc-102">ICLRIoCompletionManager Interface</span></span>
<span data-ttu-id="a68dc-103">実装により、指定した I/O の状態のホストが共通言語ランタイム (CLR) に通知されるコールバック メソッドを要求します。</span><span class="sxs-lookup"><span data-stu-id="a68dc-103">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a68dc-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="a68dc-104">Methods</span></span>  
  
|<span data-ttu-id="a68dc-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a68dc-105">Method</span></span>|<span data-ttu-id="a68dc-106">説明</span><span class="sxs-lookup"><span data-stu-id="a68dc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a68dc-107">OnComplete メソッド</span><span class="sxs-lookup"><span data-stu-id="a68dc-107">OnComplete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="a68dc-108">呼び出しを使用して行われた I/O 要求の状態の CLR に通知、 [ihostiocompletionmanager::bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="a68dc-108">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a68dc-109">コメント</span><span class="sxs-lookup"><span data-stu-id="a68dc-109">Remarks</span></span>  
 <span data-ttu-id="a68dc-110">ホストを使用して、I/O 完了の抽象化を実装して、 [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="a68dc-110">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="a68dc-111">CLR は、このインターフェイスでは、I/O 要求を行うし、ホストを使用してこのような要求の結果をランタイムに通知、`ICLRIoCompletionManager`インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="a68dc-111">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a68dc-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="a68dc-112">Requirements</span></span>  
 <span data-ttu-id="a68dc-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a68dc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a68dc-114">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a68dc-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a68dc-115">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="a68dc-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a68dc-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a68dc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a68dc-117">参照</span><span class="sxs-lookup"><span data-stu-id="a68dc-117">See Also</span></span>  
 [<span data-ttu-id="a68dc-118">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a68dc-118">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 [<span data-ttu-id="a68dc-119">IHostThreadPoolManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a68dc-119">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 [<span data-ttu-id="a68dc-120">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a68dc-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
