---
title: "ICLRTask2 インターフェイス"
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
- ICLRTask2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2
helpviewer_keywords:
- ICLRTask2 interface [.NET Framework hosting]
ms.assetid: b5a22ebc-0582-49de-91f9-97a3d9789290
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8701cff3400e46660fac90486cf5648d29aa9972
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtask2-interface"></a><span data-ttu-id="169fa-102">ICLRTask2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="169fa-102">ICLRTask2 Interface</span></span>
<span data-ttu-id="169fa-103">すべての機能を提供、 [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)インターフェイスです。 さらに、現在のスレッドで遅延するスレッドの中止できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="169fa-103">Provides all the functionality of the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface; in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="169fa-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="169fa-104">Methods</span></span>  
  
|<span data-ttu-id="169fa-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="169fa-105">Method</span></span>|<span data-ttu-id="169fa-106">説明</span><span class="sxs-lookup"><span data-stu-id="169fa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="169fa-107">BeginPreventAsyncAbort メソッド</span><span class="sxs-lookup"><span data-stu-id="169fa-107">BeginPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|<span data-ttu-id="169fa-108">新しいスレッドの遅延は、現在のスレッドで要求を中止します。</span><span class="sxs-lookup"><span data-stu-id="169fa-108">Delays new thread abort requests on the current thread.</span></span>|  
|[<span data-ttu-id="169fa-109">EndPreventAsyncAbort メソッド</span><span class="sxs-lookup"><span data-stu-id="169fa-109">EndPreventAsyncAbort Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|<span data-ttu-id="169fa-110">新しい許可または保留中のスレッドで発生するスレッドの中止の要求を現在のスレッドの中止します。</span><span class="sxs-lookup"><span data-stu-id="169fa-110">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="169fa-111">コメント</span><span class="sxs-lookup"><span data-stu-id="169fa-111">Remarks</span></span>  
 <span data-ttu-id="169fa-112">`ICLRTask2`インターフェイスが継承、`ICLRTask`インターフェイスおよびホストが失敗する必要がありますしないコードの領域を保護する、スレッドの中止を延期できるようにするメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="169fa-112">The `ICLRTask2` interface inherits the `ICLRTask` interface and adds methods that allow the host to delay thread aborts, to protect a region of code that must not fail.</span></span> <span data-ttu-id="169fa-113">呼び出す`BeginPreventAsyncAbort`した現在のスレッドと呼び出し元の遅延スレッドの中止のカウンターをインクリメント`EndPreventAsyncAbort`デクリメントことです。</span><span class="sxs-lookup"><span data-stu-id="169fa-113">Calling `BeginPreventAsyncAbort` increments the delay-thread-abort counter for the current thread, and calling `EndPreventAsyncAbort` decrements it.</span></span> <span data-ttu-id="169fa-114">呼び出す`BeginPreventAsyncAbort`と`EndPreventAsyncAbort`入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="169fa-114">Calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="169fa-115">カウンターは、0 より大きい値が、限り、現在のスレッドのスレッドの中止が遅延されます。</span><span class="sxs-lookup"><span data-stu-id="169fa-115">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="169fa-116">場合を呼び出す`BeginPreventAsyncAbort`と`EndPreventAsyncAbort`が対になっていない、可能であればどのスレッドで中止を現在のスレッドに配信できない状態になります。</span><span class="sxs-lookup"><span data-stu-id="169fa-116">If calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` are not paired, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="169fa-117">遅延時間はそれ自体を中止するスレッドの受け入れられません。</span><span class="sxs-lookup"><span data-stu-id="169fa-117">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="169fa-118">この機能によって公開される機能は、仮想マシン (VM) で内部使用されます。</span><span class="sxs-lookup"><span data-stu-id="169fa-118">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="169fa-119">これらのメソッドの誤用によっては、VM で未定義の動作があります。</span><span class="sxs-lookup"><span data-stu-id="169fa-119">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="169fa-120">たとえば、呼び出し`EndPreventAsyncAbort`最初呼び出さず`BeginPreventAsyncAbort`VM がインクリメントしていたときに、カウンターをゼロに設定でした。</span><span class="sxs-lookup"><span data-stu-id="169fa-120">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="169fa-121">同様に、内部カウンターは、オーバーフローはチェックされません。</span><span class="sxs-lookup"><span data-stu-id="169fa-121">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="169fa-122">場合は、整数の上限を超えているため、ホストと VM の両方がインクリメントされますが、結果の動作は指定されません。</span><span class="sxs-lookup"><span data-stu-id="169fa-122">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
 <span data-ttu-id="169fa-123">継承されたメンバーに関する情報の`ICLRTask`し、このインターフェイスの他の使用について、次を参照してください。、 [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="169fa-123">For information about members inherited from `ICLRTask` and about the other uses of this interface, see the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="169fa-124">必要条件</span><span class="sxs-lookup"><span data-stu-id="169fa-124">Requirements</span></span>  
 <span data-ttu-id="169fa-125">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="169fa-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="169fa-126">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="169fa-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="169fa-127">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="169fa-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="169fa-128">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="169fa-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="169fa-129">参照</span><span class="sxs-lookup"><span data-stu-id="169fa-129">See Also</span></span>  
 [<span data-ttu-id="169fa-130">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="169fa-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="169fa-131">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="169fa-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="169fa-132">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="169fa-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="169fa-133">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="169fa-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="169fa-134">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="169fa-134">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
