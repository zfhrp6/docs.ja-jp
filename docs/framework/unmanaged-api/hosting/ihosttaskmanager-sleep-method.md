---
title: IHostTaskManager::Sleep メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.Sleep
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::Sleep
helpviewer_keywords:
- IHostTaskManager::Sleep method [.NET Framework hosting]
- Sleep method, IHostTaskManager interface [.NET Framework hosting]
ms.assetid: f67d25f3-9199-4c5f-b1e8-1c819243cfd5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 648d705f21b23feb740e1791c8f32a707b985df2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442664"
---
# <a name="ihosttaskmanagersleep-method"></a><span data-ttu-id="fe9a9-102">IHostTaskManager::Sleep メソッド</span><span class="sxs-lookup"><span data-stu-id="fe9a9-102">IHostTaskManager::Sleep Method</span></span>
<span data-ttu-id="fe9a9-103">現在のタスクがスリープ状態にしようとしていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="fe9a9-103">Notifies the host that the current task is going to sleep.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe9a9-104">構文</span><span class="sxs-lookup"><span data-stu-id="fe9a9-104">Syntax</span></span>  
  
```  
HRESULT Sleep (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fe9a9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fe9a9-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="fe9a9-106">[in]スレッドがスリープ状態をミリ秒単位の時間間隔。</span><span class="sxs-lookup"><span data-stu-id="fe9a9-106">[in] The time interval, in milliseconds, that the thread will sleep.</span></span>  
  
 `option`  
 <span data-ttu-id="fe9a9-107">[in]1 つ、 [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)ホストが実行する場合は、このアクションを示す列挙値は、アクション ブロックします。</span><span class="sxs-lookup"><span data-stu-id="fe9a9-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) enumeration values, indicating what action the host should take if this action blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe9a9-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="fe9a9-108">Return Value</span></span>  
  
|<span data-ttu-id="fe9a9-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fe9a9-109">HRESULT</span></span>|<span data-ttu-id="fe9a9-110">説明</span><span class="sxs-lookup"><span data-stu-id="fe9a9-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fe9a9-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="fe9a9-111">S_OK</span></span>|<span data-ttu-id="fe9a9-112">`Sleep` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="fe9a9-112">`Sleep` returned successfully.</span></span>|  
|<span data-ttu-id="fe9a9-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fe9a9-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fe9a9-114">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="fe9a9-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fe9a9-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fe9a9-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fe9a9-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="fe9a9-116">The call timed out.</span></span>|  
|<span data-ttu-id="fe9a9-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fe9a9-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fe9a9-118">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="fe9a9-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fe9a9-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fe9a9-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fe9a9-120">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="fe9a9-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fe9a9-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fe9a9-121">E_FAIL</span></span>|<span data-ttu-id="fe9a9-122">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="fe9a9-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fe9a9-123">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="fe9a9-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fe9a9-124">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="fe9a9-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe9a9-125">コメント</span><span class="sxs-lookup"><span data-stu-id="fe9a9-125">Remarks</span></span>  
 <span data-ttu-id="fe9a9-126">CLR は呼び出し、通常`IHostTaskManager::Sleep`とき<xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>ユーザー コードから呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="fe9a9-126">The CLR typically calls `IHostTaskManager::Sleep` when <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is called from user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe9a9-127">要件</span><span class="sxs-lookup"><span data-stu-id="fe9a9-127">Requirements</span></span>  
 <span data-ttu-id="fe9a9-128">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="fe9a9-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe9a9-129">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fe9a9-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fe9a9-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="fe9a9-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fe9a9-131">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe9a9-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe9a9-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="fe9a9-132">See Also</span></span>  
 [<span data-ttu-id="fe9a9-133">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fe9a9-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="fe9a9-134">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fe9a9-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="fe9a9-135">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fe9a9-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="fe9a9-136">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fe9a9-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
