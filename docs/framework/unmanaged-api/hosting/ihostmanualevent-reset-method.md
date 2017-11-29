---
title: "IHostManualEvent::Reset メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostManualEvent.Reset
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostManualEvent::Reset
helpviewer_keywords:
- Reset method, IHostManualEvent interface [.NET Framework hosting]
- IHostManualEvent::Reset method [.NET Framework hosting]
ms.assetid: 0d101168-b5e3-49ce-90c7-85cf2db83c4c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e41922cb1732fe4e6727408692bbc7b99288e6dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmanualeventreset-method"></a><span data-ttu-id="e0361-102">IHostManualEvent::Reset メソッド</span><span class="sxs-lookup"><span data-stu-id="e0361-102">IHostManualEvent::Reset Method</span></span>
<span data-ttu-id="e0361-103">現在のリセット[IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)インスタンスを非シグナル状態にします。</span><span class="sxs-lookup"><span data-stu-id="e0361-103">Resets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a non-signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0361-104">構文</span><span class="sxs-lookup"><span data-stu-id="e0361-104">Syntax</span></span>  
  
```  
HRESULT Reset ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e0361-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="e0361-105">Return Value</span></span>  
  
|<span data-ttu-id="e0361-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e0361-106">HRESULT</span></span>|<span data-ttu-id="e0361-107">説明</span><span class="sxs-lookup"><span data-stu-id="e0361-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e0361-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e0361-108">S_OK</span></span>|<span data-ttu-id="e0361-109">`Reset`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="e0361-109">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="e0361-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e0361-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e0361-111">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="e0361-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e0361-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e0361-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e0361-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="e0361-113">The call timed out.</span></span>|  
|<span data-ttu-id="e0361-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e0361-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e0361-115">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="e0361-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e0361-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e0361-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e0361-117">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="e0361-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e0361-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e0361-118">E_FAIL</span></span>|<span data-ttu-id="e0361-119">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="e0361-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e0361-120">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="e0361-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e0361-121">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="e0361-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e0361-122">要件</span><span class="sxs-lookup"><span data-stu-id="e0361-122">Requirements</span></span>  
 <span data-ttu-id="e0361-123">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e0361-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0361-124">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e0361-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e0361-125">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="e0361-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e0361-126">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0361-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0361-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="e0361-127">See Also</span></span>  
 [<span data-ttu-id="e0361-128">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e0361-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="e0361-129">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e0361-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="e0361-130">IHostManualEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e0361-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="e0361-131">IHostSemaphore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e0361-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="e0361-132">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e0361-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
