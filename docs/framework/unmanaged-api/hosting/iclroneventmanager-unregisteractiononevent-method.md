---
title: "ICLROnEventManager::UnregisterActionOnEvent メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLROnEventManager.UnregisterActionOnEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLROnEventManager::UnregisterActionOnEvent
helpviewer_keywords:
- UnRegisterActionOnEvent method [.NET Framework hosting]
- ICLROnEventManager::UnRegisterActionOnEvent method [.NET Framework hosting]
ms.assetid: 4c02ec37-cdf0-46b2-890e-235092741236
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8d295817a7c6f8a177de3ff251904beeaf8ca828
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclroneventmanagerunregisteractiononevent-method"></a><span data-ttu-id="073ca-102">ICLROnEventManager::UnregisterActionOnEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="073ca-102">ICLROnEventManager::UnregisterActionOnEvent Method</span></span>
<span data-ttu-id="073ca-103">指定されたイベントに対して以前に登録されたコールバック ポインターを登録解除します。</span><span class="sxs-lookup"><span data-stu-id="073ca-103">Unregisters a previously registered callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="073ca-104">構文</span><span class="sxs-lookup"><span data-stu-id="073ca-104">Syntax</span></span>  
  
```  
HRESULT UnregisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="073ca-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="073ca-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="073ca-106">[in]1 つ、 [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)で説明されているコールバック ポインターの登録を解除する対象のイベントを示す値`pAction`です。</span><span class="sxs-lookup"><span data-stu-id="073ca-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, indicating the event for which to unregister the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="073ca-107">[in]ポインター、 [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)へのパラメーターとして渡されたオブジェクト、 [RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="073ca-107">[in] A pointer to an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) object that was passed as a parameter to the [RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="073ca-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="073ca-108">Return Value</span></span>  
  
|<span data-ttu-id="073ca-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="073ca-109">HRESULT</span></span>|<span data-ttu-id="073ca-110">説明</span><span class="sxs-lookup"><span data-stu-id="073ca-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="073ca-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="073ca-111">S_OK</span></span>|<span data-ttu-id="073ca-112">`UnregisterActionOnEvent`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="073ca-112">`UnregisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="073ca-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="073ca-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="073ca-114">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="073ca-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="073ca-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="073ca-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="073ca-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="073ca-116">The call timed out.</span></span>|  
|<span data-ttu-id="073ca-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="073ca-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="073ca-118">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="073ca-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="073ca-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="073ca-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="073ca-120">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="073ca-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="073ca-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="073ca-121">E_FAIL</span></span>|<span data-ttu-id="073ca-122">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="073ca-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="073ca-123">メソッドには、E_FAIL が返された、後に、CLR はプロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="073ca-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="073ca-124">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="073ca-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="073ca-125">必要条件</span><span class="sxs-lookup"><span data-stu-id="073ca-125">Requirements</span></span>  
 <span data-ttu-id="073ca-126">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="073ca-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="073ca-127">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="073ca-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="073ca-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="073ca-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="073ca-129">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="073ca-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="073ca-130">参照</span><span class="sxs-lookup"><span data-stu-id="073ca-130">See Also</span></span>  
 [<span data-ttu-id="073ca-131">EClrEvent 列挙型</span><span class="sxs-lookup"><span data-stu-id="073ca-131">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="073ca-132">IActionOnCLREvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="073ca-132">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [<span data-ttu-id="073ca-133">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="073ca-133">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="073ca-134">ICLROnEventManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="073ca-134">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
