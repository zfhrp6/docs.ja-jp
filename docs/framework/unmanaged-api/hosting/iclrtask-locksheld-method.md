---
title: "ICLRTask::LocksHeld メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.LocksHeld
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::LocksHeld
helpviewer_keywords:
- LocksHeld method [.NET Framework hosting]
- ICLRTask::LocksHeld method [.NET Framework hosting]
ms.assetid: e88a4dc3-02cc-4703-a474-292b71c40657
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f985295dcc54816fc0ee31b40115360602f1afd9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtasklocksheld-method"></a><span data-ttu-id="fb366-102">ICLRTask::LocksHeld メソッド</span><span class="sxs-lookup"><span data-stu-id="fb366-102">ICLRTask::LocksHeld Method</span></span>
<span data-ttu-id="fb366-103">タスクで現在保持されているロックの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="fb366-103">Gets the number of locks currently held on the task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb366-104">構文</span><span class="sxs-lookup"><span data-stu-id="fb366-104">Syntax</span></span>  
  
```  
HRESULT LocksHeld (  
    [out] SIZE_T *pLockCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb366-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fb366-105">Parameters</span></span>  
 `pLockCount`  
 <span data-ttu-id="fb366-106">[out]メソッドの呼び出し時にタスクで保持されているロックの数。</span><span class="sxs-lookup"><span data-stu-id="fb366-106">[out] The number of locks held on the task at the time of the method call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fb366-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="fb366-107">Return Value</span></span>  
  
|<span data-ttu-id="fb366-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fb366-108">HRESULT</span></span>|<span data-ttu-id="fb366-109">説明</span><span class="sxs-lookup"><span data-stu-id="fb366-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fb366-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fb366-110">S_OK</span></span>|<span data-ttu-id="fb366-111">`LocksHeld`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="fb366-111">`LocksHeld` returned successfully.</span></span>|  
|<span data-ttu-id="fb366-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fb366-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fb366-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="fb366-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fb366-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fb366-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fb366-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="fb366-115">The call timed out.</span></span>|  
|<span data-ttu-id="fb366-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fb366-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fb366-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="fb366-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fb366-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fb366-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fb366-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="fb366-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fb366-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fb366-120">E_FAIL</span></span>|<span data-ttu-id="fb366-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="fb366-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fb366-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="fb366-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fb366-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="fb366-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fb366-124">必要条件</span><span class="sxs-lookup"><span data-stu-id="fb366-124">Requirements</span></span>  
 <span data-ttu-id="fb366-125">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="fb366-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb366-126">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fb366-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fb366-127">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="fb366-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fb366-128">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb366-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb366-129">参照</span><span class="sxs-lookup"><span data-stu-id="fb366-129">See Also</span></span>  
 [<span data-ttu-id="fb366-130">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fb366-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="fb366-131">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fb366-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="fb366-132">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fb366-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="fb366-133">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fb366-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
