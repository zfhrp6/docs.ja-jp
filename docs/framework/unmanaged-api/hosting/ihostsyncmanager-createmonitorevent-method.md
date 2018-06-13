---
title: IHostSyncManager::CreateMonitorEvent メソッド
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateMonitorEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateMonitorEvent
helpviewer_keywords:
- CreateMonitorEvent method [.NET Framework hosting]
- IHostSyncManager::CreateMonitorEvent method [.NET Framework hosting]
ms.assetid: 524c7fd3-9b5c-46e7-99ba-555fd2fe33f0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d7cff23fc0b58d316ce19950a982249e84b79ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441953"
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a><span data-ttu-id="e572d-102">IHostSyncManager::CreateMonitorEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="e572d-102">IHostSyncManager::CreateMonitorEvent Method</span></span>
<span data-ttu-id="e572d-103">監視対象の自動リセット イベント オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="e572d-103">Creates a monitored auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e572d-104">構文</span><span class="sxs-lookup"><span data-stu-id="e572d-104">Syntax</span></span>  
  
```  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e572d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e572d-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="e572d-106">[in]イベント オブジェクトに関連付けるクッキー。</span><span class="sxs-lookup"><span data-stu-id="e572d-106">[in] A cookie to associate with the event object.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="e572d-107">[out]アドレスへのポインター、 [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)インスタンス、または null の場合、イベント オブジェクトを作成できませんでした。</span><span class="sxs-lookup"><span data-stu-id="e572d-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e572d-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="e572d-108">Return Value</span></span>  
  
|<span data-ttu-id="e572d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e572d-109">HRESULT</span></span>|<span data-ttu-id="e572d-110">説明</span><span class="sxs-lookup"><span data-stu-id="e572d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e572d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e572d-111">S_OK</span></span>|<span data-ttu-id="e572d-112">`CreateMonitorEvent` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="e572d-112">`CreateMonitorEvent` returned successfully.</span></span>|  
|<span data-ttu-id="e572d-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e572d-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e572d-114">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="e572d-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e572d-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e572d-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e572d-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="e572d-116">The call timed out.</span></span>|  
|<span data-ttu-id="e572d-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e572d-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e572d-118">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="e572d-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e572d-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e572d-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e572d-120">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="e572d-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e572d-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e572d-121">E_FAIL</span></span>|<span data-ttu-id="e572d-122">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="e572d-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e572d-123">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="e572d-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e572d-124">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="e572d-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e572d-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="e572d-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="e572d-126">十分なメモリは、要求されたイベント オブジェクトを作成できませんでした。</span><span class="sxs-lookup"><span data-stu-id="e572d-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e572d-127">コメント</span><span class="sxs-lookup"><span data-stu-id="e572d-127">Remarks</span></span>  
 <span data-ttu-id="e572d-128">`CreateMonitorEvent` 返します、 `IHostAutoEvent` CLR がマネージの実装で使用する<xref:System.Threading.Monitor?displayProperty=nameWithType>型です。</span><span class="sxs-lookup"><span data-stu-id="e572d-128">`CreateMonitorEvent` returns an `IHostAutoEvent` that the CLR uses in its implementation of the managed <xref:System.Threading.Monitor?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="e572d-129">このメソッドは、Win32 をミラー化`CreateEvent`関数の値を持つ`false`向けに指定された、`bManualReset`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="e572d-129">This method mirrors the Win32 `CreateEvent` function, with a value of `false` specified for the `bManualReset` parameter.</span></span>  
  
 <span data-ttu-id="e572d-130">ホストは、cookie を使用して呼び出すことで、モニターにどのタスクが待機しているかを判断、 [iclrsyncmanager::getmonitorowner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="e572d-130">The host can use the cookie to determine which task is waiting on the monitor by calling the [ICLRSyncManager::GetMonitorOwner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e572d-131">要件</span><span class="sxs-lookup"><span data-stu-id="e572d-131">Requirements</span></span>  
 <span data-ttu-id="e572d-132">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e572d-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e572d-133">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e572d-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e572d-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="e572d-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e572d-135">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e572d-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e572d-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="e572d-136">See Also</span></span>  
 [<span data-ttu-id="e572d-137">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e572d-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="e572d-138">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e572d-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="e572d-139">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e572d-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="e572d-140">モニター</span><span class="sxs-lookup"><span data-stu-id="e572d-140">Monitors</span></span>](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)
