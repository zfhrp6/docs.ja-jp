---
title: "ICLRIoCompletionManager インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRIoCompletionManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRIoCompletionManager
helpviewer_keywords: ICLRIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c6c3ace6-e5e7-4450-8cc5-a9a48208c493
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dbff3c39da2a18ab45f0ea03d1e1588aa61c7c3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="9864d-102">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9864d-102">ICLRIoCompletionManager Interface</span></span>
<span data-ttu-id="9864d-103">実装により、指定した I/O の状態のホストが共通言語ランタイム (CLR) に通知されるコールバック メソッドを要求します。</span><span class="sxs-lookup"><span data-stu-id="9864d-103">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9864d-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="9864d-104">Methods</span></span>  
  
|<span data-ttu-id="9864d-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="9864d-105">Method</span></span>|<span data-ttu-id="9864d-106">説明</span><span class="sxs-lookup"><span data-stu-id="9864d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9864d-107">OnComplete メソッド</span><span class="sxs-lookup"><span data-stu-id="9864d-107">OnComplete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="9864d-108">呼び出しを使用して行われた I/O 要求の状態の CLR に通知、 [ihostiocompletionmanager::bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="9864d-108">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9864d-109">コメント</span><span class="sxs-lookup"><span data-stu-id="9864d-109">Remarks</span></span>  
 <span data-ttu-id="9864d-110">ホストを使用して、I/O 完了の抽象化を実装して、 [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="9864d-110">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="9864d-111">CLR は、このインターフェイスでは、I/O 要求を行うし、ホストを使用してこのような要求の結果をランタイムに通知、`ICLRIoCompletionManager`インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="9864d-111">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9864d-112">要件</span><span class="sxs-lookup"><span data-stu-id="9864d-112">Requirements</span></span>  
 <span data-ttu-id="9864d-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9864d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9864d-114">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9864d-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9864d-115">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="9864d-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9864d-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9864d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9864d-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="9864d-117">See Also</span></span>  
 [<span data-ttu-id="9864d-118">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9864d-118">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 [<span data-ttu-id="9864d-119">IHostThreadPoolManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9864d-119">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 [<span data-ttu-id="9864d-120">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9864d-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
