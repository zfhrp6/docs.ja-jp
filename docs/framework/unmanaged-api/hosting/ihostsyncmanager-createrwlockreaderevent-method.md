---
title: "IHostSyncManager::CreateRWLockReaderEvent メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateRWLockReaderEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateRWLockReaderEvent
helpviewer_keywords:
- CreateRWLockReaderEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockReaderEvent method [.NET Framework hosting]
ms.assetid: 68c4ea19-c47c-45c6-b420-d3a2ba1c2d50
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b583e7b5dd1a83ecb891591c25802ae257ad7c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsyncmanagercreaterwlockreaderevent-method"></a><span data-ttu-id="69753-102">IHostSyncManager::CreateRWLockReaderEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="69753-102">IHostSyncManager::CreateRWLockReaderEvent Method</span></span>
<span data-ttu-id="69753-103">リーダー ロックを実装するための手動リセット イベント オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="69753-103">Creates a manual-reset event object for the implementation of a reader lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69753-104">構文</span><span class="sxs-lookup"><span data-stu-id="69753-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockReaderEvent (  
    [in]  BOOL bInitialState,  
    [in]  SIZE_T cookie,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="69753-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="69753-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="69753-106">[in]`true`場合は、 `ppEvent` 、それ以外のシグナル状態にする必要があります`false`です。</span><span class="sxs-lookup"><span data-stu-id="69753-106">[in] `true`, if `ppEvent` should be signaled; otherwise, `false`.</span></span>  
  
 `cookie`  
 <span data-ttu-id="69753-107">[in]リーダー ロックと関連付けるクッキー。</span><span class="sxs-lookup"><span data-stu-id="69753-107">[in] A cookie to associate with the reader lock.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="69753-108">[out]アドレスへのポインター、 [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)インスタンス、または null の場合、イベント オブジェクトを作成できませんでした。</span><span class="sxs-lookup"><span data-stu-id="69753-108">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69753-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="69753-109">Return Value</span></span>  
  
|<span data-ttu-id="69753-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="69753-110">HRESULT</span></span>|<span data-ttu-id="69753-111">説明</span><span class="sxs-lookup"><span data-stu-id="69753-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="69753-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="69753-112">S_OK</span></span>|<span data-ttu-id="69753-113">`CreateRWLockReaderEvent`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="69753-113">`CreateRWLockReaderEvent` returned successfully.</span></span>|  
|<span data-ttu-id="69753-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="69753-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="69753-115">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="69753-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="69753-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="69753-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="69753-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="69753-117">The call timed out.</span></span>|  
|<span data-ttu-id="69753-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="69753-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="69753-119">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="69753-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="69753-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="69753-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="69753-121">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="69753-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="69753-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="69753-122">E_FAIL</span></span>|<span data-ttu-id="69753-123">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="69753-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="69753-124">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="69753-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="69753-125">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="69753-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="69753-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="69753-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="69753-127">十分なメモリは、要求されたイベント オブジェクトを作成できませんでした。</span><span class="sxs-lookup"><span data-stu-id="69753-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69753-128">コメント</span><span class="sxs-lookup"><span data-stu-id="69753-128">Remarks</span></span>  
 <span data-ttu-id="69753-129">CLR 呼び出し`CreateRWLockReaderEvent`への参照を取得する、`IHostManualEvent`リーダー ロックの実装で使用するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="69753-129">The CLR calls `CreateRWLockReaderEvent` to get a reference to an `IHostManualEvent` instance to use in its implementation of a reader lock.</span></span> <span data-ttu-id="69753-130">ホストは、cookie を使用してクエリを実行して、リーダー ロックを待機しているタスクを決定する、 [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="69753-130">The host can use the cookie to determine which tasks are waiting on the reader lock by querying the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69753-131">必要条件</span><span class="sxs-lookup"><span data-stu-id="69753-131">Requirements</span></span>  
 <span data-ttu-id="69753-132">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="69753-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69753-133">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="69753-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="69753-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="69753-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="69753-135">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69753-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69753-136">参照</span><span class="sxs-lookup"><span data-stu-id="69753-136">See Also</span></span>  
 [<span data-ttu-id="69753-137">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="69753-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="69753-138">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="69753-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="69753-139">IHostManualEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="69753-139">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="69753-140">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="69753-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
