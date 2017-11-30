---
title: "ICLROnEventManager::RegisterActionOnEvent メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLROnEventManager.RegisterActionOnEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLROnEventManager::RegisterActionOnEvent
helpviewer_keywords:
- ICLROnEventManager::RegisterActionOnEvent method [.NET Framework hosting]
- RegisterActionOnEvent method [.NET Framework hosting]
ms.assetid: b944cf49-918d-4c4e-993b-77d097a52550
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0ef99527abc7ca33e1176958a590483f34556a1b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclroneventmanagerregisteractiononevent-method"></a><span data-ttu-id="60771-102">ICLROnEventManager::RegisterActionOnEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="60771-102">ICLROnEventManager::RegisterActionOnEvent Method</span></span>
<span data-ttu-id="60771-103">指定したイベントのコールバック ポインターを登録します。</span><span class="sxs-lookup"><span data-stu-id="60771-103">Registers a callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60771-104">構文</span><span class="sxs-lookup"><span data-stu-id="60771-104">Syntax</span></span>  
  
```  
HRESULT RegisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="60771-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="60771-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="60771-106">[in]1 つ、 [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)で説明されているコールバック ポインターを登録するためのイベントを示す値`pAction`です。</span><span class="sxs-lookup"><span data-stu-id="60771-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, indicating the event for which to register the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="60771-107">[in]ポインター、 [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)登録済みのイベントが発生したときに呼び出されるオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="60771-107">[in] A pointer to an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) object that is called when the registered event fires.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="60771-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="60771-108">Return Value</span></span>  
  
|<span data-ttu-id="60771-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="60771-109">HRESULT</span></span>|<span data-ttu-id="60771-110">説明</span><span class="sxs-lookup"><span data-stu-id="60771-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="60771-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="60771-111">S_OK</span></span>|<span data-ttu-id="60771-112">`RegisterActionOnEvent`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="60771-112">`RegisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="60771-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="60771-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="60771-114">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="60771-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="60771-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="60771-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="60771-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="60771-116">The call timed out.</span></span>|  
|<span data-ttu-id="60771-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="60771-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="60771-118">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="60771-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="60771-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="60771-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="60771-120">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="60771-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="60771-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="60771-121">E_FAIL</span></span>|<span data-ttu-id="60771-122">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="60771-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="60771-123">メソッドには、E_FAIL が返された、後に、CLR はプロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="60771-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="60771-124">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="60771-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60771-125">コメント</span><span class="sxs-lookup"><span data-stu-id="60771-125">Remarks</span></span>  
 <span data-ttu-id="60771-126">ホストは、どちらか一方または両方で説明されている 2 つのイベントの種類のコールバックを登録できる`EClrEvent`です。</span><span class="sxs-lookup"><span data-stu-id="60771-126">The host can register callbacks for either or both of the two event types described by `EClrEvent`.</span></span> <span data-ttu-id="60771-127">ホストを取得、`ICLROnEventManager`インターフェイスを呼び出して、 [iclrcontrol::getclrmanager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="60771-127">The host gets the `ICLROnEventManager` interface by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="60771-128">イベントを`RegisterActionOnEvent`レジスタは、2 回以上とアンロードまたは CLR を無効にすることを通知するさまざまなスレッドから起動されることです。</span><span class="sxs-lookup"><span data-stu-id="60771-128">The events that `RegisterActionOnEvent` registers can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60771-129">要件</span><span class="sxs-lookup"><span data-stu-id="60771-129">Requirements</span></span>  
 <span data-ttu-id="60771-130">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="60771-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60771-131">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="60771-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="60771-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="60771-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="60771-133">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60771-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60771-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="60771-134">See Also</span></span>  
 [<span data-ttu-id="60771-135">EClrEvent 列挙型</span><span class="sxs-lookup"><span data-stu-id="60771-135">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="60771-136">IActionOnCLREvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="60771-136">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [<span data-ttu-id="60771-137">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="60771-137">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="60771-138">ICLROnEventManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="60771-138">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
