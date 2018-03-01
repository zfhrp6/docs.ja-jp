---
title: "IGCThreadControl インターフェイス"
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
- IGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCThreadControl
helpviewer_keywords:
- IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 3ff04d75-85ac-4df9-886d-dbaa037c0552
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: def6ae3c8bf8eea9cb135529e2b6e672b180e68c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="igcthreadcontrol-interface"></a><span data-ttu-id="dded0-102">IGCThreadControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dded0-102">IGCThreadControl Interface</span></span>
<span data-ttu-id="dded0-103">それ以外の場合のみがブロックされるガベージ コレクションのスレッドのスケジューリングに参加するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="dded0-103">Provides methods for participating in the scheduling of threads that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dded0-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="dded0-104">Methods</span></span>  
  
|<span data-ttu-id="dded0-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="dded0-105">Method</span></span>|<span data-ttu-id="dded0-106">説明</span><span class="sxs-lookup"><span data-stu-id="dded0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dded0-107">SuspensionEnding メソッド</span><span class="sxs-lookup"><span data-stu-id="dded0-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionending-method.md)|<span data-ttu-id="dded0-108">ランタイムがガベージ コレクションまたはその他の中断の後のスレッドを再開することをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="dded0-108">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="dded0-109">SuspensionStarting メソッド</span><span class="sxs-lookup"><span data-stu-id="dded0-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionstarting-method.md)|<span data-ttu-id="dded0-110">ランタイムがガベージ コレクションのスレッドの中断またはその他の中断を開始していることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="dded0-110">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="dded0-111">ThreadIsBlockingForSuspension メソッド</span><span class="sxs-lookup"><span data-stu-id="dded0-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)|<span data-ttu-id="dded0-112">呼び出しを行っているスレッドがガベージ コレクションまたはその他の中断のためにブロックすることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="dded0-112">Notifies the host that the thread making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dded0-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="dded0-113">Requirements</span></span>  
 <span data-ttu-id="dded0-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="dded0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dded0-115">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dded0-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dded0-116">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="dded0-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dded0-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dded0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dded0-118">参照</span><span class="sxs-lookup"><span data-stu-id="dded0-118">See Also</span></span>  
 [<span data-ttu-id="dded0-119">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dded0-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
