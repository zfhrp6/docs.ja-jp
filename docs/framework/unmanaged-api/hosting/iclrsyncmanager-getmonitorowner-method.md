---
title: "ICLRSyncManager::GetMonitorOwner メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRSyncManager.GetMonitorOwner
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRSyncManager::GetMonitorOwner
helpviewer_keywords:
- ICLRSyncManager::GetMonitorOwner method [.NET Framework hosting]
- GetMonitorOwner method [.NET Framework hosting]
ms.assetid: 840983a4-396d-47b4-86a0-d35f9b437cdb
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 90fbba9a5aead27d79c5355d69bc12481e826b65
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a><span data-ttu-id="88592-102">ICLRSyncManager::GetMonitorOwner メソッド</span><span class="sxs-lookup"><span data-stu-id="88592-102">ICLRSyncManager::GetMonitorOwner Method</span></span>
<span data-ttu-id="88592-103">取得、 [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)指定された cookie で識別されるモニターを所有するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="88592-103">Gets the [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that owns the monitor identified by the specified cookie.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88592-104">構文</span><span class="sxs-lookup"><span data-stu-id="88592-104">Syntax</span></span>  
  
```  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="88592-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="88592-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="88592-106">[in]モニターに関連付けられているクッキー。</span><span class="sxs-lookup"><span data-stu-id="88592-106">[in] The cookie associated with the monitor.</span></span>  
  
 `ppOwnerHostTask`  
 <span data-ttu-id="88592-107">[out]ポインター、`IHostTask`を現在所有しているモニター、または null タスクが所有権を持たない場合。</span><span class="sxs-lookup"><span data-stu-id="88592-107">[out] A pointer to the `IHostTask` that currently owns the monitor, or null if no task has ownership.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88592-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="88592-108">Return Value</span></span>  
  
|<span data-ttu-id="88592-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="88592-109">HRESULT</span></span>|<span data-ttu-id="88592-110">説明</span><span class="sxs-lookup"><span data-stu-id="88592-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="88592-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="88592-111">S_OK</span></span>|<span data-ttu-id="88592-112">`GetMonitorOwner`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="88592-112">`GetMonitorOwner` returned successfully.</span></span>|  
|<span data-ttu-id="88592-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="88592-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="88592-114">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="88592-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="88592-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="88592-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="88592-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="88592-116">The call timed out.</span></span>|  
|<span data-ttu-id="88592-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="88592-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="88592-118">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="88592-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="88592-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="88592-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="88592-120">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="88592-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="88592-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="88592-121">E_FAIL</span></span>|<span data-ttu-id="88592-122">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="88592-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="88592-123">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="88592-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="88592-124">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="88592-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88592-125">コメント</span><span class="sxs-lookup"><span data-stu-id="88592-125">Remarks</span></span>  
 <span data-ttu-id="88592-126">ホストは`GetMonitorOwner`デッドロック検出メカニズムの一部として。</span><span class="sxs-lookup"><span data-stu-id="88592-126">The host typically calls `GetMonitorOwner` as part of a deadlock-detection mechanism.</span></span> <span data-ttu-id="88592-127">呼び出しを使用して、作成時、cookie がモニターに関連付けられて[ihostsyncmanager::createmonitorevent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="88592-127">The cookie is associated with a monitor when it is created by using a call to [IHostSyncManager::CreateMonitorEvent](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88592-128">モニターを基になるイベントを解放する呼び出しをブロックする可能性があります: デッドロックは発生しませんが、— このメソッドに呼び出しがそのモニターに関連付けられた cookie で現在有効である場合。</span><span class="sxs-lookup"><span data-stu-id="88592-128">A call to release the event underlying the monitor might block—but will not deadlock—if a call to this method is currently in effect on the cookie associated with that monitor.</span></span> <span data-ttu-id="88592-129">このモニターの取得を試みた場合、その他のタスクがブロックも可能性があります。</span><span class="sxs-lookup"><span data-stu-id="88592-129">Other tasks might also block if they attempt to acquire this monitor.</span></span>  
  
 <span data-ttu-id="88592-130">`GetMonitorOwner`常にすぐに返され、呼び出しの後にいつでも呼び出すことができます`CreateMonitorEvent`です。</span><span class="sxs-lookup"><span data-stu-id="88592-130">`GetMonitorOwner` always returns immediately and can be called any time after a call to `CreateMonitorEvent`.</span></span> <span data-ttu-id="88592-131">ホストは、タスクが、イベントで待機するまで待機する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="88592-131">The host does not need to wait until a task is waiting on the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88592-132">要件</span><span class="sxs-lookup"><span data-stu-id="88592-132">Requirements</span></span>  
 <span data-ttu-id="88592-133">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="88592-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88592-134">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="88592-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="88592-135">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="88592-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="88592-136">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88592-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88592-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="88592-137">See Also</span></span>  
 [<span data-ttu-id="88592-138">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="88592-138">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="88592-139">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="88592-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
