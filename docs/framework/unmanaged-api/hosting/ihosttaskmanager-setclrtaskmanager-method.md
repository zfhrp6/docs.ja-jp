---
title: "IHostTaskManager::SetCLRTaskManager メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.SetCLRTaskManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::SetCLRTaskManager
helpviewer_keywords:
- IHostTaskManager::SetCLRTaskManager method [.NET Framework hosting]
- SetCLRTaskManager method [.NET Framework hosting]
ms.assetid: ec90ee83-bd4b-408b-9274-62a923ab86a1
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9f009fee3f9bc439ce61d859759870f9cbb54f09
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="aae30-102">IHostTaskManager::SetCLRTaskManager メソッド</span><span class="sxs-lookup"><span data-stu-id="aae30-102">IHostTaskManager::SetCLRTaskManager Method</span></span>
<span data-ttu-id="aae30-103">により、ホストへのインターフェイス ポインターで、 [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)共通言語ランタイム (CLR) によって実装されているインスタンス。</span><span class="sxs-lookup"><span data-stu-id="aae30-103">Provides the host with an interface pointer to an [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aae30-104">構文</span><span class="sxs-lookup"><span data-stu-id="aae30-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aae30-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aae30-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="aae30-106">[in]ポインター、`ICLRTaskManager`共通言語ランタイムによって実装されるインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="aae30-106">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aae30-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="aae30-107">Return Value</span></span>  
  
|<span data-ttu-id="aae30-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aae30-108">HRESULT</span></span>|<span data-ttu-id="aae30-109">説明</span><span class="sxs-lookup"><span data-stu-id="aae30-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aae30-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="aae30-110">S_OK</span></span>|<span data-ttu-id="aae30-111">`SetCLRTaskManager`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="aae30-111">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="aae30-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aae30-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aae30-113">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="aae30-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aae30-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aae30-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="aae30-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="aae30-115">The call timed out.</span></span>|  
|<span data-ttu-id="aae30-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="aae30-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="aae30-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="aae30-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="aae30-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="aae30-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="aae30-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="aae30-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="aae30-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aae30-120">E_FAIL</span></span>|<span data-ttu-id="aae30-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="aae30-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aae30-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="aae30-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aae30-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="aae30-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aae30-124">コメント</span><span class="sxs-lookup"><span data-stu-id="aae30-124">Remarks</span></span>  
 <span data-ttu-id="aae30-125">ランタイム呼び出し`SetCLRTaskManager`にインターフェイス ポインターを使用して、ホストを提供する、`ICLRTaskManager`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="aae30-125">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aae30-126">必要条件</span><span class="sxs-lookup"><span data-stu-id="aae30-126">Requirements</span></span>  
 <span data-ttu-id="aae30-127">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="aae30-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aae30-128">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="aae30-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aae30-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="aae30-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aae30-130">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aae30-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aae30-131">参照</span><span class="sxs-lookup"><span data-stu-id="aae30-131">See Also</span></span>  
 [<span data-ttu-id="aae30-132">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aae30-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="aae30-133">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aae30-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="aae30-134">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aae30-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="aae30-135">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aae30-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
