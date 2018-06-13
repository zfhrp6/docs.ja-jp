---
title: IHostSyncManager::CreateManualEvent メソッド
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateManualEvent
helpviewer_keywords:
- CreateManualEvent method [.NET Framework hosting]
- IHostSyncManager::CreateManualEvent method [.NET Framework hosting]
ms.assetid: 68661fbd-09cf-46dc-890b-e694f8a3880a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ecf53606dd12b517d9ec31ab25f98452d35bdf98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443447"
---
# <a name="ihostsyncmanagercreatemanualevent-method"></a><span data-ttu-id="785cf-102">IHostSyncManager::CreateManualEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="785cf-102">IHostSyncManager::CreateManualEvent Method</span></span>
<span data-ttu-id="785cf-103">手動リセット イベント オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="785cf-103">Creates a manual-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="785cf-104">構文</span><span class="sxs-lookup"><span data-stu-id="785cf-104">Syntax</span></span>  
  
```  
HRESULT CreateManualEvent (  
    [in]  BOOL bInitialState,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="785cf-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="785cf-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="785cf-106">[in]`true`オブジェクトがシグナル状態、それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="785cf-106">[in] `true`, if the object is signaled; otherwise, `false`.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="785cf-107">[out]アドレスへのポインター、 [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)インスタンス、または null の場合、イベントを作成できませんでした。</span><span class="sxs-lookup"><span data-stu-id="785cf-107">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="785cf-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="785cf-108">Return Value</span></span>  
  
|<span data-ttu-id="785cf-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="785cf-109">HRESULT</span></span>|<span data-ttu-id="785cf-110">説明</span><span class="sxs-lookup"><span data-stu-id="785cf-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="785cf-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="785cf-111">S_OK</span></span>|<span data-ttu-id="785cf-112">`CreateManualEvent` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="785cf-112">`CreateManualEvent` returned successfully.</span></span>|  
|<span data-ttu-id="785cf-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="785cf-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="785cf-114">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="785cf-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="785cf-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="785cf-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="785cf-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="785cf-116">The call timed out.</span></span>|  
|<span data-ttu-id="785cf-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="785cf-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="785cf-118">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="785cf-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="785cf-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="785cf-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="785cf-120">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="785cf-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="785cf-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="785cf-121">E_FAIL</span></span>|<span data-ttu-id="785cf-122">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="785cf-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="785cf-123">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="785cf-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="785cf-124">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="785cf-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="785cf-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="785cf-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="785cf-126">十分なメモリは、要求されたイベント オブジェクトを作成できませんでした。</span><span class="sxs-lookup"><span data-stu-id="785cf-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="785cf-127">コメント</span><span class="sxs-lookup"><span data-stu-id="785cf-127">Remarks</span></span>  
 <span data-ttu-id="785cf-128">`CreateManualEvent` 作成、 `IHostManualEvent`、手動リセット イベント オブジェクトへの呼び出しを必要とする、 [ihostmanualevent::reset](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)を非シグナル状態に設定します。</span><span class="sxs-lookup"><span data-stu-id="785cf-128">`CreateManualEvent` creates an `IHostManualEvent`, a manual-reset event object that requires a call to the [IHostManualEvent::Reset](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md) method to set it to a non-signaled state.</span></span> <span data-ttu-id="785cf-129">`CreateManualEvent` Win32 をミラー化`CreateEvent`の値を持つ関数`true`向けに指定された、`bManualReset`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="785cf-129">`CreateManualEvent` mirrors the Win32 `CreateEvent` function with a value of `true` specified for the `bManualReset` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="785cf-130">要件</span><span class="sxs-lookup"><span data-stu-id="785cf-130">Requirements</span></span>  
 <span data-ttu-id="785cf-131">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="785cf-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="785cf-132">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="785cf-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="785cf-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="785cf-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="785cf-134">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="785cf-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="785cf-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="785cf-135">See Also</span></span>  
 [<span data-ttu-id="785cf-136">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="785cf-136">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="785cf-137">IHostManualEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="785cf-137">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="785cf-138">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="785cf-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
