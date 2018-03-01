---
title: "IHostManualEvent::Wait メソッド"
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
- IHostManualEvent.Wait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Wait
helpviewer_keywords:
- IHostManualEvent::Wait method [.NET Framework hosting]
- Wait method, IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 1fbb7d8b-8a23-4c2b-8376-1a70cd2d6030
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2dd456a3901f91fc8598a707a5699637ec450dbd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmanualeventwait-method"></a><span data-ttu-id="1b0c5-102">IHostManualEvent::Wait メソッド</span><span class="sxs-lookup"><span data-stu-id="1b0c5-102">IHostManualEvent::Wait Method</span></span>
<span data-ttu-id="1b0c5-103">により、現在[IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)所有されているまで待機するインスタンスまたは指定された時間が経過時間。</span><span class="sxs-lookup"><span data-stu-id="1b0c5-103">Causes the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to wait until it is owned, or a specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b0c5-104">構文</span><span class="sxs-lookup"><span data-stu-id="1b0c5-104">Syntax</span></span>  
  
```  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1b0c5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1b0c5-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="1b0c5-106">[in]場合は、戻る前に待機するミリ秒数、現在`IHostManualEvent`インスタンスは所有されていません。</span><span class="sxs-lookup"><span data-stu-id="1b0c5-106">[in] The number of milliseconds to wait before returning, if the current `IHostManualEvent` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="1b0c5-107">[in]いずれか、 [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)値、ホストが実行する場合は、この操作を示す操作がブロックされます。</span><span class="sxs-lookup"><span data-stu-id="1b0c5-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating the action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1b0c5-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="1b0c5-108">Return Value</span></span>  
  
|<span data-ttu-id="1b0c5-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1b0c5-109">HRESULT</span></span>|<span data-ttu-id="1b0c5-110">説明</span><span class="sxs-lookup"><span data-stu-id="1b0c5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1b0c5-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="1b0c5-111">S_OK</span></span>|<span data-ttu-id="1b0c5-112">`Wait`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="1b0c5-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="1b0c5-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1b0c5-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1b0c5-114">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="1b0c5-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1b0c5-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1b0c5-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1b0c5-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="1b0c5-116">The call timed out.</span></span>|  
|<span data-ttu-id="1b0c5-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1b0c5-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1b0c5-118">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="1b0c5-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1b0c5-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1b0c5-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1b0c5-120">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="1b0c5-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1b0c5-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1b0c5-121">E_FAIL</span></span>|<span data-ttu-id="1b0c5-122">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="1b0c5-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1b0c5-123">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="1b0c5-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1b0c5-124">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="1b0c5-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1b0c5-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="1b0c5-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="1b0c5-126">ホストが、待機中にデッドロックを検出し、現在`IHostManualEvent`デッドロックの対象としてインスタンス。</span><span class="sxs-lookup"><span data-stu-id="1b0c5-126">The host detected a deadlock during the wait interval, and chose the current `IHostManualEvent` instance as the deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1b0c5-127">必要条件</span><span class="sxs-lookup"><span data-stu-id="1b0c5-127">Requirements</span></span>  
 <span data-ttu-id="1b0c5-128">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1b0c5-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b0c5-129">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1b0c5-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1b0c5-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="1b0c5-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1b0c5-131">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b0c5-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b0c5-132">参照</span><span class="sxs-lookup"><span data-stu-id="1b0c5-132">See Also</span></span>  
 [<span data-ttu-id="1b0c5-133">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1b0c5-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="1b0c5-134">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1b0c5-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="1b0c5-135">IHostManualEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1b0c5-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="1b0c5-136">IHostSemaphore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1b0c5-136">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="1b0c5-137">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1b0c5-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
