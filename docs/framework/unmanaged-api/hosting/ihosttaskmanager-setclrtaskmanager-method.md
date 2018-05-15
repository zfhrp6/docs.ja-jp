---
title: IHostTaskManager::SetCLRTaskManager メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetCLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetCLRTaskManager
helpviewer_keywords:
- IHostTaskManager::SetCLRTaskManager method [.NET Framework hosting]
- SetCLRTaskManager method [.NET Framework hosting]
ms.assetid: ec90ee83-bd4b-408b-9274-62a923ab86a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84501ae5e96a2eab4c5da4d4cb211fc60822e339
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="4ab71-102">IHostTaskManager::SetCLRTaskManager メソッド</span><span class="sxs-lookup"><span data-stu-id="4ab71-102">IHostTaskManager::SetCLRTaskManager Method</span></span>
<span data-ttu-id="4ab71-103">により、ホストへのインターフェイス ポインターで、 [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)共通言語ランタイム (CLR) によって実装されているインスタンス。</span><span class="sxs-lookup"><span data-stu-id="4ab71-103">Provides the host with an interface pointer to an [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ab71-104">構文</span><span class="sxs-lookup"><span data-stu-id="4ab71-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4ab71-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4ab71-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="4ab71-106">[in]ポインター、`ICLRTaskManager`共通言語ランタイムによって実装されるインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="4ab71-106">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ab71-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="4ab71-107">Return Value</span></span>  
  
|<span data-ttu-id="4ab71-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4ab71-108">HRESULT</span></span>|<span data-ttu-id="4ab71-109">説明</span><span class="sxs-lookup"><span data-stu-id="4ab71-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4ab71-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4ab71-110">S_OK</span></span>|<span data-ttu-id="4ab71-111">`SetCLRTaskManager` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="4ab71-111">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="4ab71-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4ab71-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4ab71-113">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="4ab71-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4ab71-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4ab71-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4ab71-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="4ab71-115">The call timed out.</span></span>|  
|<span data-ttu-id="4ab71-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4ab71-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4ab71-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="4ab71-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4ab71-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4ab71-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4ab71-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="4ab71-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4ab71-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4ab71-120">E_FAIL</span></span>|<span data-ttu-id="4ab71-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="4ab71-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4ab71-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="4ab71-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4ab71-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="4ab71-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ab71-124">コメント</span><span class="sxs-lookup"><span data-stu-id="4ab71-124">Remarks</span></span>  
 <span data-ttu-id="4ab71-125">ランタイム呼び出し`SetCLRTaskManager`にインターフェイス ポインターを使用して、ホストを提供する、`ICLRTaskManager`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="4ab71-125">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ab71-126">要件</span><span class="sxs-lookup"><span data-stu-id="4ab71-126">Requirements</span></span>  
 <span data-ttu-id="4ab71-127">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4ab71-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ab71-128">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4ab71-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4ab71-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="4ab71-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4ab71-130">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ab71-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ab71-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ab71-131">See Also</span></span>  
 [<span data-ttu-id="4ab71-132">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4ab71-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="4ab71-133">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4ab71-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="4ab71-134">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4ab71-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="4ab71-135">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4ab71-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
