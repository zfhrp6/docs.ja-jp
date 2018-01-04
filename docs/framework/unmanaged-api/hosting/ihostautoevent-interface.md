---
title: "IHostAutoEvent インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAutoEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAutoEvent
helpviewer_keywords: IHostAutoEvent interface [.NET Framework hosting]
ms.assetid: 6c1d15c1-a80a-4ee9-b1e4-6e859db6575a
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 91e790cf7c97c0045535870c2d41d628f943a22d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostautoevent-interface"></a><span data-ttu-id="0787d-102">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0787d-102">IHostAutoEvent Interface</span></span>
<span data-ttu-id="0787d-103">ホストの自動リセット イベントの実装の表現を提供します。</span><span class="sxs-lookup"><span data-stu-id="0787d-103">Provides a representation of the host's implementation of an auto-reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0787d-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="0787d-104">Methods</span></span>  
  
|<span data-ttu-id="0787d-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="0787d-105">Method</span></span>|<span data-ttu-id="0787d-106">説明</span><span class="sxs-lookup"><span data-stu-id="0787d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0787d-107">Set メソッド</span><span class="sxs-lookup"><span data-stu-id="0787d-107">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-set-method.md)|<span data-ttu-id="0787d-108">現在の設定`IHostAutoEvent`インスタンスがシグナル状態にします。</span><span class="sxs-lookup"><span data-stu-id="0787d-108">Sets the current `IHostAutoEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="0787d-109">Wait メソッド</span><span class="sxs-lookup"><span data-stu-id="0787d-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-wait-method.md)|<span data-ttu-id="0787d-110">により、現在`IHostAutoEvent`イベントを所有するまで待機するインスタンスまたは指定された時間が経過時間。</span><span class="sxs-lookup"><span data-stu-id="0787d-110">Causes the current `IHostAutoEvent` instance to wait until the event is owned or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0787d-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="0787d-111">Requirements</span></span>  
 <span data-ttu-id="0787d-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0787d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0787d-113">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0787d-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0787d-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="0787d-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0787d-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0787d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0787d-116">参照</span><span class="sxs-lookup"><span data-stu-id="0787d-116">See Also</span></span>  
 [<span data-ttu-id="0787d-117">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0787d-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="0787d-118">IHostManualEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0787d-118">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="0787d-119">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0787d-119">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="0787d-120">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0787d-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
