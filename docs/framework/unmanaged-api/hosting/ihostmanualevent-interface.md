---
title: "IHostManualEvent インターフェイス"
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
- IHostManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent
helpviewer_keywords:
- IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 300c2661-b7d1-4c39-b080-9ebdef0fd523
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0d55500efbe808b2fce16e869422e727b8ed0b93
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="7d274-102">IHostManualEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7d274-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="7d274-103">手動リセット イベントの形式のホストの実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="7d274-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7d274-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="7d274-104">Methods</span></span>  
  
|<span data-ttu-id="7d274-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="7d274-105">Method</span></span>|<span data-ttu-id="7d274-106">説明</span><span class="sxs-lookup"><span data-stu-id="7d274-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7d274-107">Reset メソッド</span><span class="sxs-lookup"><span data-stu-id="7d274-107">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|<span data-ttu-id="7d274-108">現在のリセット`IHostManualEvent`インスタンスを非シグナル状態にします。</span><span class="sxs-lookup"><span data-stu-id="7d274-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="7d274-109">Set メソッド</span><span class="sxs-lookup"><span data-stu-id="7d274-109">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|<span data-ttu-id="7d274-110">現在の設定`IHostManualEvent`インスタンスがシグナル状態にします。</span><span class="sxs-lookup"><span data-stu-id="7d274-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="7d274-111">Wait メソッド</span><span class="sxs-lookup"><span data-stu-id="7d274-111">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|<span data-ttu-id="7d274-112">により、現在`IHostManualEvent`所有されているまで待機するインスタンスまたは指定された時間が経過時間。</span><span class="sxs-lookup"><span data-stu-id="7d274-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7d274-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="7d274-113">Requirements</span></span>  
 <span data-ttu-id="7d274-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7d274-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d274-115">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7d274-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7d274-116">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="7d274-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d274-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d274-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d274-118">参照</span><span class="sxs-lookup"><span data-stu-id="7d274-118">See Also</span></span>  
 [<span data-ttu-id="7d274-119">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7d274-119">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="7d274-120">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7d274-120">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="7d274-121">IHostSemaphore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7d274-121">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="7d274-122">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7d274-122">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="7d274-123">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7d274-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
