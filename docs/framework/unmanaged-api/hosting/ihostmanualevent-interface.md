---
title: IHostManualEvent インターフェイス
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53aaf4c23861666962e5567a6cf9eb9fffc6292f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438757"
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="e6f08-102">IHostManualEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e6f08-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="e6f08-103">手動リセット イベントの形式のホストの実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="e6f08-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e6f08-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="e6f08-104">Methods</span></span>  
  
|<span data-ttu-id="e6f08-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="e6f08-105">Method</span></span>|<span data-ttu-id="e6f08-106">説明</span><span class="sxs-lookup"><span data-stu-id="e6f08-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e6f08-107">Reset メソッド</span><span class="sxs-lookup"><span data-stu-id="e6f08-107">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|<span data-ttu-id="e6f08-108">現在のリセット`IHostManualEvent`インスタンスを非シグナル状態にします。</span><span class="sxs-lookup"><span data-stu-id="e6f08-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="e6f08-109">Set メソッド</span><span class="sxs-lookup"><span data-stu-id="e6f08-109">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|<span data-ttu-id="e6f08-110">現在の設定`IHostManualEvent`インスタンスがシグナル状態にします。</span><span class="sxs-lookup"><span data-stu-id="e6f08-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="e6f08-111">Wait メソッド</span><span class="sxs-lookup"><span data-stu-id="e6f08-111">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|<span data-ttu-id="e6f08-112">により、現在`IHostManualEvent`所有されているまで待機するインスタンスまたは指定された時間が経過時間。</span><span class="sxs-lookup"><span data-stu-id="e6f08-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e6f08-113">要件</span><span class="sxs-lookup"><span data-stu-id="e6f08-113">Requirements</span></span>  
 <span data-ttu-id="e6f08-114">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e6f08-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6f08-115">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e6f08-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e6f08-116">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="e6f08-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e6f08-117">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6f08-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6f08-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="e6f08-118">See Also</span></span>  
 [<span data-ttu-id="e6f08-119">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e6f08-119">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="e6f08-120">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e6f08-120">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="e6f08-121">IHostSemaphore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e6f08-121">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="e6f08-122">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e6f08-122">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="e6f08-123">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e6f08-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
