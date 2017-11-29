---
title: "IHostTaskManager::SwitchToTask メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.SwitchToTask
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::SwitchToTask
helpviewer_keywords:
- IHostTaskManager::SwitchToTask method [.NET Framework hosting]
- SwitchToTask method [.NET Framework hosting]
ms.assetid: 35d0c27e-4b14-49ce-810d-7ab2120177e8
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9b85c762bd2d10baddfa013a8310e3b542a94af6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagerswitchtotask-method"></a><span data-ttu-id="0b3fb-102">IHostTaskManager::SwitchToTask メソッド</span><span class="sxs-lookup"><span data-stu-id="0b3fb-102">IHostTaskManager::SwitchToTask Method</span></span>
<span data-ttu-id="0b3fb-103">現在のタスクを切り離すことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="0b3fb-103">Notifies the host that it should switch out the current task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b3fb-104">構文</span><span class="sxs-lookup"><span data-stu-id="0b3fb-104">Syntax</span></span>  
  
```  
HRESULT SwitchToTask (  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0b3fb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0b3fb-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="0b3fb-106">[in]1 つ、 [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)場合に、ホストが行うアクションを示す列挙値、要求された操作はブロックされます。</span><span class="sxs-lookup"><span data-stu-id="0b3fb-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating the action the host should take if the requested operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b3fb-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="0b3fb-107">Return Value</span></span>  
  
|<span data-ttu-id="0b3fb-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0b3fb-108">HRESULT</span></span>|<span data-ttu-id="0b3fb-109">説明</span><span class="sxs-lookup"><span data-stu-id="0b3fb-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0b3fb-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0b3fb-110">S_OK</span></span>|<span data-ttu-id="0b3fb-111">`SwitchToTask`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="0b3fb-111">`SwitchToTask` returned successfully.</span></span>|  
|<span data-ttu-id="0b3fb-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0b3fb-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0b3fb-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="0b3fb-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0b3fb-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0b3fb-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0b3fb-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="0b3fb-115">The call timed out.</span></span>|  
|<span data-ttu-id="0b3fb-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0b3fb-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0b3fb-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="0b3fb-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0b3fb-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0b3fb-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0b3fb-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="0b3fb-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0b3fb-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0b3fb-120">E_FAIL</span></span>|<span data-ttu-id="0b3fb-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="0b3fb-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0b3fb-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="0b3fb-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0b3fb-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="0b3fb-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b3fb-124">コメント</span><span class="sxs-lookup"><span data-stu-id="0b3fb-124">Remarks</span></span>  
 <span data-ttu-id="0b3fb-125">ホストは、必要に応じて、別のタスクに切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="0b3fb-125">The host can switch in another task as desired or needed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b3fb-126">`SwitchToTask`ホストが; に切り替える必要があるタスクが指定されていません切り離す必要があるタスクだけを指定します。</span><span class="sxs-lookup"><span data-stu-id="0b3fb-126">`SwitchToTask` does not specify which task the host should switch to; it specifies only the task that it should switch from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b3fb-127">要件</span><span class="sxs-lookup"><span data-stu-id="0b3fb-127">Requirements</span></span>  
 <span data-ttu-id="0b3fb-128">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0b3fb-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b3fb-129">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0b3fb-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0b3fb-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="0b3fb-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0b3fb-131">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b3fb-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b3fb-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="0b3fb-132">See Also</span></span>  
 [<span data-ttu-id="0b3fb-133">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0b3fb-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="0b3fb-134">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0b3fb-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="0b3fb-135">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0b3fb-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="0b3fb-136">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0b3fb-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
