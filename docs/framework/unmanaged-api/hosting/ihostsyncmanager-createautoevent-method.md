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
ms.openlocfilehash: e6a792ca9075e48a8092d92e1adf870174dd1af6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsyncmanagercreateautoevent-method"></a><span data-ttu-id="54506-102">IHostSyncManager::CreateAutoEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="54506-102">IHostSyncManager::CreateAutoEvent Method</span></span>
<span data-ttu-id="54506-103">自動リセット イベント オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="54506-103">Creates an auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54506-104">構文</span><span class="sxs-lookup"><span data-stu-id="54506-104">Syntax</span></span>  
  
```  
HRESULT CreateAutoEvent (  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="54506-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="54506-105">Parameters</span></span>  
 `ppEvent`  
 <span data-ttu-id="54506-106">[out]アドレスへのポインター、 [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)インスタンス、ホストによって実装された、または null の場合は、イベント オブジェクトを作成できませんでした。</span><span class="sxs-lookup"><span data-stu-id="54506-106">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance implemented by the host, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="54506-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="54506-107">Return Value</span></span>  
  
|<span data-ttu-id="54506-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="54506-108">HRESULT</span></span>|<span data-ttu-id="54506-109">説明</span><span class="sxs-lookup"><span data-stu-id="54506-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="54506-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="54506-110">S_OK</span></span>|<span data-ttu-id="54506-111">`CreateAutoEvent`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="54506-111">`CreateAutoEvent` returned successfully.</span></span>|  
|<span data-ttu-id="54506-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="54506-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="54506-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="54506-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="54506-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="54506-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="54506-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="54506-115">The call timed out.</span></span>|  
|<span data-ttu-id="54506-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="54506-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="54506-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="54506-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="54506-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="54506-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="54506-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="54506-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="54506-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="54506-120">E_FAIL</span></span>|<span data-ttu-id="54506-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="54506-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="54506-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="54506-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="54506-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="54506-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="54506-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="54506-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="54506-125">十分なメモリは、要求されたイベント オブジェクトを作成できませんでした。</span><span class="sxs-lookup"><span data-stu-id="54506-125">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54506-126">コメント</span><span class="sxs-lookup"><span data-stu-id="54506-126">Remarks</span></span>  
 <span data-ttu-id="54506-127">`CreateAutoEvent`状態が自動的に変更を非シグナル待機中のスレッドが解放された後に自動イベント オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="54506-127">`CreateAutoEvent` creates an auto-event object whose state is automatically changed to non-signaled after the waiting thread has been released.</span></span> <span data-ttu-id="54506-128">このメソッドは、Win32 をミラー化`CreateEvent`の値を持つ関数`false`向けに指定された、`bManualReset`パラメーター</span><span class="sxs-lookup"><span data-stu-id="54506-128">This method mirrors the Win32 `CreateEvent` function with a value of `false` specified for the `bManualReset` parameter</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54506-129">要件</span><span class="sxs-lookup"><span data-stu-id="54506-129">Requirements</span></span>  
 <span data-ttu-id="54506-130">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="54506-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54506-131">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="54506-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="54506-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="54506-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="54506-133">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54506-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54506-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="54506-134">See Also</span></span>  
 [<span data-ttu-id="54506-135">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="54506-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="54506-136">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="54506-136">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="54506-137">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="54506-137">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [<span data-ttu-id="54506-138">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="54506-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
