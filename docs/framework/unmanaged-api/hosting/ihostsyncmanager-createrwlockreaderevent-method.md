---
title: IHostSyncManager::CreateRWLockReaderEvent メソッド
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateRWLockReaderEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateRWLockReaderEvent
helpviewer_keywords:
- CreateRWLockReaderEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockReaderEvent method [.NET Framework hosting]
ms.assetid: 68c4ea19-c47c-45c6-b420-d3a2ba1c2d50
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb2a7a6650da03796628b647bc0b06174c576538
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447357"
---
# <a name="ihostsyncmanagercreaterwlockreaderevent-method"></a><span data-ttu-id="413b3-102">IHostSyncManager::CreateRWLockReaderEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="413b3-102">IHostSyncManager::CreateRWLockReaderEvent Method</span></span>
<span data-ttu-id="413b3-103">リーダー ロックを実装するための手動リセット イベント オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="413b3-103">Creates a manual-reset event object for the implementation of a reader lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="413b3-104">構文</span><span class="sxs-lookup"><span data-stu-id="413b3-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockReaderEvent (  
    [in]  BOOL bInitialState,  
    [in]  SIZE_T cookie,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="413b3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="413b3-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="413b3-106">[in]`true`場合は、 `ppEvent` 、それ以外のシグナル状態にする必要があります`false`です。</span><span class="sxs-lookup"><span data-stu-id="413b3-106">[in] `true`, if `ppEvent` should be signaled; otherwise, `false`.</span></span>  
  
 `cookie`  
 <span data-ttu-id="413b3-107">[in]リーダー ロックと関連付けるクッキー。</span><span class="sxs-lookup"><span data-stu-id="413b3-107">[in] A cookie to associate with the reader lock.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="413b3-108">[out]アドレスへのポインター、 [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)インスタンス、または null の場合、イベント オブジェクトを作成できませんでした。</span><span class="sxs-lookup"><span data-stu-id="413b3-108">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="413b3-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="413b3-109">Return Value</span></span>  
  
|<span data-ttu-id="413b3-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="413b3-110">HRESULT</span></span>|<span data-ttu-id="413b3-111">説明</span><span class="sxs-lookup"><span data-stu-id="413b3-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="413b3-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="413b3-112">S_OK</span></span>|<span data-ttu-id="413b3-113">`CreateRWLockReaderEvent` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="413b3-113">`CreateRWLockReaderEvent` returned successfully.</span></span>|  
|<span data-ttu-id="413b3-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="413b3-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="413b3-115">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="413b3-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="413b3-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="413b3-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="413b3-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="413b3-117">The call timed out.</span></span>|  
|<span data-ttu-id="413b3-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="413b3-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="413b3-119">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="413b3-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="413b3-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="413b3-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="413b3-121">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="413b3-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="413b3-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="413b3-122">E_FAIL</span></span>|<span data-ttu-id="413b3-123">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="413b3-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="413b3-124">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="413b3-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="413b3-125">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="413b3-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="413b3-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="413b3-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="413b3-127">十分なメモリは、要求されたイベント オブジェクトを作成できませんでした。</span><span class="sxs-lookup"><span data-stu-id="413b3-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="413b3-128">コメント</span><span class="sxs-lookup"><span data-stu-id="413b3-128">Remarks</span></span>  
 <span data-ttu-id="413b3-129">CLR 呼び出し`CreateRWLockReaderEvent`への参照を取得する、`IHostManualEvent`リーダー ロックの実装で使用するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="413b3-129">The CLR calls `CreateRWLockReaderEvent` to get a reference to an `IHostManualEvent` instance to use in its implementation of a reader lock.</span></span> <span data-ttu-id="413b3-130">ホストは、cookie を使用してクエリを実行して、リーダー ロックを待機しているタスクを決定する、 [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="413b3-130">The host can use the cookie to determine which tasks are waiting on the reader lock by querying the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="413b3-131">要件</span><span class="sxs-lookup"><span data-stu-id="413b3-131">Requirements</span></span>  
 <span data-ttu-id="413b3-132">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="413b3-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="413b3-133">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="413b3-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="413b3-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="413b3-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="413b3-135">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="413b3-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="413b3-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="413b3-136">See Also</span></span>  
 [<span data-ttu-id="413b3-137">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="413b3-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="413b3-138">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="413b3-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="413b3-139">IHostManualEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="413b3-139">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="413b3-140">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="413b3-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
