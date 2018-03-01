---
title: "IDebuggerThreadControl インターフェイス"
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
- IDebuggerThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IDebuggerThreadControl
helpviewer_keywords:
- IDebuggerThreadControl interface [.NET Framework hosting]
ms.assetid: 0a270c42-a7d1-45f1-a64d-fa3e84d14532
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 297a66f9466b00dec4d32f7d8a6e2bd13b6e5655
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebuggerthreadcontrol-interface"></a><span data-ttu-id="6be3c-102">IDebuggerThreadControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6be3c-102">IDebuggerThreadControl Interface</span></span>
<span data-ttu-id="6be3c-103">デバッグ サービスによるスレッドのブロックおよびブロックについて、ホストを通知するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="6be3c-103">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6be3c-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="6be3c-104">Methods</span></span>  
  
|<span data-ttu-id="6be3c-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="6be3c-105">Method</span></span>|<span data-ttu-id="6be3c-106">説明</span><span class="sxs-lookup"><span data-stu-id="6be3c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6be3c-107">ThreadIsBlockingForDebugger メソッド</span><span class="sxs-lookup"><span data-stu-id="6be3c-107">ThreadIsBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|<span data-ttu-id="6be3c-108">このコールバックを送信しているスレッドは、ホストに通知デバッグ サービス内でブロックします。</span><span class="sxs-lookup"><span data-stu-id="6be3c-108">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>|  
|[<span data-ttu-id="6be3c-109">ReleaseAllRuntimeThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="6be3c-109">ReleaseAllRuntimeThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-releaseallruntimethreads-method.md)|<span data-ttu-id="6be3c-110">デバッグ サービスがブロックされているすべてのスレッドを解放しようとしていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="6be3c-110">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>|  
|[<span data-ttu-id="6be3c-111">StartBlockingForDebugger メソッド</span><span class="sxs-lookup"><span data-stu-id="6be3c-111">StartBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-startblockingfordebugger-method.md)|<span data-ttu-id="6be3c-112">デバッグ サービスがすべてのスレッドのブロックを開始しようとしていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="6be3c-112">Notifies the host that the debugging services are about to start blocking all threads.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6be3c-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="6be3c-113">Requirements</span></span>  
 <span data-ttu-id="6be3c-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6be3c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6be3c-115">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6be3c-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6be3c-116">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="6be3c-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6be3c-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6be3c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6be3c-118">参照</span><span class="sxs-lookup"><span data-stu-id="6be3c-118">See Also</span></span>  
 [<span data-ttu-id="6be3c-119">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6be3c-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
