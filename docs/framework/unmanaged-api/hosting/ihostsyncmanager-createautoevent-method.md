---
title: "IHostSyncManager::CreateAutoEvent メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateAutoEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateAutoEvent
helpviewer_keywords:
- IHostSyncManager::CreateAutoEvent method [.NET Framework hosting]
- CreateAutoEvent method [.NET Framework hosting]
ms.assetid: 3153643e-cf5c-4b44-8e0e-c2b22cb08208
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b7874839d04af89f2fa512f82213862f34408001
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsyncmanagercreateautoevent-method"></a><span data-ttu-id="ad1bc-102">IHostSyncManager::CreateAutoEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="ad1bc-102">IHostSyncManager::CreateAutoEvent Method</span></span>
<span data-ttu-id="ad1bc-103">自動リセット イベント オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="ad1bc-103">Creates an auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad1bc-104">構文</span><span class="sxs-lookup"><span data-stu-id="ad1bc-104">Syntax</span></span>  
  
```  
HRESULT CreateAutoEvent (  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ad1bc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ad1bc-105">Parameters</span></span>  
 `ppEvent`  
 <span data-ttu-id="ad1bc-106">[out]アドレスへのポインター、 [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)インスタンス、ホストによって実装された、または null の場合は、イベント オブジェクトを作成できませんでした。</span><span class="sxs-lookup"><span data-stu-id="ad1bc-106">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance implemented by the host, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad1bc-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="ad1bc-107">Return Value</span></span>  
  
|<span data-ttu-id="ad1bc-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ad1bc-108">HRESULT</span></span>|<span data-ttu-id="ad1bc-109">説明</span><span class="sxs-lookup"><span data-stu-id="ad1bc-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ad1bc-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ad1bc-110">S_OK</span></span>|<span data-ttu-id="ad1bc-111">`CreateAutoEvent`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="ad1bc-111">`CreateAutoEvent` returned successfully.</span></span>|  
|<span data-ttu-id="ad1bc-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ad1bc-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ad1bc-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="ad1bc-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ad1bc-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ad1bc-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ad1bc-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="ad1bc-115">The call timed out.</span></span>|  
|<span data-ttu-id="ad1bc-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ad1bc-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ad1bc-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="ad1bc-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ad1bc-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ad1bc-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ad1bc-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="ad1bc-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ad1bc-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ad1bc-120">E_FAIL</span></span>|<span data-ttu-id="ad1bc-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="ad1bc-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ad1bc-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="ad1bc-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ad1bc-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="ad1bc-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ad1bc-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="ad1bc-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="ad1bc-125">十分なメモリは、要求されたイベント オブジェクトを作成できませんでした。</span><span class="sxs-lookup"><span data-stu-id="ad1bc-125">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad1bc-126">コメント</span><span class="sxs-lookup"><span data-stu-id="ad1bc-126">Remarks</span></span>  
 <span data-ttu-id="ad1bc-127">`CreateAutoEvent`状態が自動的に変更を非シグナル待機中のスレッドが解放された後に自動イベント オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="ad1bc-127">`CreateAutoEvent` creates an auto-event object whose state is automatically changed to non-signaled after the waiting thread has been released.</span></span> <span data-ttu-id="ad1bc-128">このメソッドは、Win32 をミラー化`CreateEvent`の値を持つ関数`false`向けに指定された、`bManualReset`パラメーター</span><span class="sxs-lookup"><span data-stu-id="ad1bc-128">This method mirrors the Win32 `CreateEvent` function with a value of `false` specified for the `bManualReset` parameter</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad1bc-129">必要条件</span><span class="sxs-lookup"><span data-stu-id="ad1bc-129">Requirements</span></span>  
 <span data-ttu-id="ad1bc-130">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ad1bc-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad1bc-131">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ad1bc-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ad1bc-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="ad1bc-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ad1bc-133">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad1bc-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad1bc-134">参照</span><span class="sxs-lookup"><span data-stu-id="ad1bc-134">See Also</span></span>  
 [<span data-ttu-id="ad1bc-135">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ad1bc-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="ad1bc-136">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ad1bc-136">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="ad1bc-137">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ad1bc-137">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [<span data-ttu-id="ad1bc-138">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ad1bc-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
