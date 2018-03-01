---
title: "IHostTask::SetCLRTask メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostTask.SetCLRTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::SetCLRTask
helpviewer_keywords:
- SetCLRTask method [.NET Framework hosting]
- IHostTask::SetCLRTask method [.NET Framework hosting]
ms.assetid: e9d39c80-41a1-49e7-bb5e-ea3433bfb5d7
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 680ad2c13d8d6fc24134c9399cffb236bd637057
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="3f23e-102">IHostTask::SetCLRTask メソッド</span><span class="sxs-lookup"><span data-stu-id="3f23e-102">IHostTask::SetCLRTask Method</span></span>
<span data-ttu-id="3f23e-103">関連付けます、 `ICLRTask` 、現在のインスタンス[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="3f23e-103">Associates an `ICLRTask` instance with the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f23e-104">構文</span><span class="sxs-lookup"><span data-stu-id="3f23e-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3f23e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3f23e-105">Parameters</span></span>  
 `pCLRTask`  
 <span data-ttu-id="3f23e-106">[in]インターフェイス ポインター、`ICLRTask`に現在関連付けられるインスタンス`IHostTask`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="3f23e-106">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f23e-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="3f23e-107">Return Value</span></span>  
  
|<span data-ttu-id="3f23e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3f23e-108">HRESULT</span></span>|<span data-ttu-id="3f23e-109">説明</span><span class="sxs-lookup"><span data-stu-id="3f23e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3f23e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3f23e-110">S_OK</span></span>|<span data-ttu-id="3f23e-111">`SetCLRTask`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="3f23e-111">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="3f23e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3f23e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3f23e-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="3f23e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3f23e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3f23e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3f23e-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="3f23e-115">The call timed out.</span></span>|  
|<span data-ttu-id="3f23e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3f23e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3f23e-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="3f23e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3f23e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3f23e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3f23e-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="3f23e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3f23e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3f23e-120">E_FAIL</span></span>|<span data-ttu-id="3f23e-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="3f23e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3f23e-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="3f23e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3f23e-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="3f23e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f23e-124">コメント</span><span class="sxs-lookup"><span data-stu-id="3f23e-124">Remarks</span></span>  
 <span data-ttu-id="3f23e-125">CLR 呼び出し`SetCLRTask`に関連付けるには、 `ICLRTask` 、現在のインスタンス`IHostTask`への呼び出しによって作成されたインスタンス[ihosttaskmanager::createtask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="3f23e-125">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f23e-126">必要条件</span><span class="sxs-lookup"><span data-stu-id="3f23e-126">Requirements</span></span>  
 <span data-ttu-id="3f23e-127">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3f23e-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f23e-128">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3f23e-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3f23e-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="3f23e-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3f23e-130">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f23e-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f23e-131">参照</span><span class="sxs-lookup"><span data-stu-id="3f23e-131">See Also</span></span>  
 [<span data-ttu-id="3f23e-132">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3f23e-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="3f23e-133">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3f23e-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="3f23e-134">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3f23e-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="3f23e-135">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3f23e-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
