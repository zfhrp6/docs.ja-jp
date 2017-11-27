---
title: "IGCThreadControl インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCThreadControl
api_location: mscoree.dll
api_type: COM
f1_keywords: IGCThreadControl
helpviewer_keywords: IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 3ff04d75-85ac-4df9-886d-dbaa037c0552
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 66afef7dec0637e98249838ae06ae6f1161df3f3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="igcthreadcontrol-interface"></a><span data-ttu-id="75db1-102">IGCThreadControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="75db1-102">IGCThreadControl Interface</span></span>
<span data-ttu-id="75db1-103">それ以外の場合のみがブロックされるガベージ コレクションのスレッドのスケジューリングに参加するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="75db1-103">Provides methods for participating in the scheduling of threads that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="75db1-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="75db1-104">Methods</span></span>  
  
|<span data-ttu-id="75db1-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="75db1-105">Method</span></span>|<span data-ttu-id="75db1-106">説明</span><span class="sxs-lookup"><span data-stu-id="75db1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="75db1-107">SuspensionEnding メソッド</span><span class="sxs-lookup"><span data-stu-id="75db1-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionending-method.md)|<span data-ttu-id="75db1-108">ランタイムがガベージ コレクションまたはその他の中断の後のスレッドを再開することをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="75db1-108">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="75db1-109">SuspensionStarting メソッド</span><span class="sxs-lookup"><span data-stu-id="75db1-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionstarting-method.md)|<span data-ttu-id="75db1-110">ランタイムがガベージ コレクションのスレッドの中断またはその他の中断を開始していることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="75db1-110">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="75db1-111">ThreadIsBlockingForSuspension メソッド</span><span class="sxs-lookup"><span data-stu-id="75db1-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)|<span data-ttu-id="75db1-112">呼び出しを行っているスレッドがガベージ コレクションまたはその他の中断のためにブロックすることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="75db1-112">Notifies the host that the thread making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="75db1-113">要件</span><span class="sxs-lookup"><span data-stu-id="75db1-113">Requirements</span></span>  
 <span data-ttu-id="75db1-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="75db1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75db1-115">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="75db1-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="75db1-116">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="75db1-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="75db1-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75db1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75db1-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="75db1-118">See Also</span></span>  
 [<span data-ttu-id="75db1-119">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="75db1-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
