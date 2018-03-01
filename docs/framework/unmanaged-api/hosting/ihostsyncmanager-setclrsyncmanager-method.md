---
title: "IHostSyncManager::SetCLRSyncManager メソッド"
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
- IHostSyncManager.SetCLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::SetCLRSyncManager
helpviewer_keywords:
- IHostSyncManager::SetCLRSyncManager method [.NET Framework hosting]
- SetCLRSyncManager method [.NET Framework hosting]
ms.assetid: 2b8bbe76-a45d-4989-bacb-11df42f8798c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fca59f0d2617c6fb244b2b1ed7b5cf46a7d5869f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsyncmanagersetclrsyncmanager-method"></a><span data-ttu-id="4964f-102">IHostSyncManager::SetCLRSyncManager メソッド</span><span class="sxs-lookup"><span data-stu-id="4964f-102">IHostSyncManager::SetCLRSyncManager Method</span></span>
<span data-ttu-id="4964f-103">セット、 [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)に現在関連付けインスタンス[IHostSyncManager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="4964f-103">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current [IHostSyncManager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4964f-104">構文</span><span class="sxs-lookup"><span data-stu-id="4964f-104">Syntax</span></span>  
  
```  
HRESULT SetCLRSyncManager (  
    [in] ICLRSyncManager *pManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4964f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4964f-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="4964f-106">[in]ポインター、`ICLRSyncManager`共通言語ランタイム (CLR) で指定されたインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="4964f-106">[in] A pointer to an `ICLRSyncManager` instance supplied by the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4964f-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="4964f-107">Return Value</span></span>  
  
|<span data-ttu-id="4964f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4964f-108">HRESULT</span></span>|<span data-ttu-id="4964f-109">説明</span><span class="sxs-lookup"><span data-stu-id="4964f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4964f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4964f-110">S_OK</span></span>|<span data-ttu-id="4964f-111">`SetCLRSyncManager`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="4964f-111">`SetCLRSyncManager` returned successfully.</span></span>|  
|<span data-ttu-id="4964f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4964f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4964f-113">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="4964f-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4964f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4964f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4964f-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="4964f-115">The call timed out.</span></span>|  
|<span data-ttu-id="4964f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4964f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4964f-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="4964f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4964f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4964f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4964f-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="4964f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4964f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4964f-120">E_FAIL</span></span>|<span data-ttu-id="4964f-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="4964f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4964f-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="4964f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4964f-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="4964f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4964f-124">コメント</span><span class="sxs-lookup"><span data-stu-id="4964f-124">Remarks</span></span>  
 <span data-ttu-id="4964f-125">ホストと CLR の間の通信を容易にホスト インターフェイスは、通常のペアになっています。</span><span class="sxs-lookup"><span data-stu-id="4964f-125">To facilitate communication between the host and the CLR, hosting interfaces generally come in pairs.</span></span> <span data-ttu-id="4964f-126">ペアの 1 つのメンバーは、ホストによって実装し、他のメンバーは、CLR で実装します。</span><span class="sxs-lookup"><span data-stu-id="4964f-126">One member of the pair is implemented by the host, and the other member is implemented by the CLR.</span></span> <span data-ttu-id="4964f-127">ホスト側の実装として、`IHostSyncManager`に対応するインターフェイス、 `ICLRSyncManager` CLR によって実装されるインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="4964f-127">As a host-side implementation, the `IHostSyncManager` interface corresponds to the `ICLRSyncManager` interface implemented by the CLR.</span></span> <span data-ttu-id="4964f-128">CLR 呼び出し`SetCLRSyncManager`を指定する、`ICLRSyncManager`現在に関連付けるホストをインスタンス`IHostSyncManager`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="4964f-128">The CLR calls `SetCLRSyncManager` to supply an `ICLRSyncManager` instance for the host to associate with the current `IHostSyncManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4964f-129">必要条件</span><span class="sxs-lookup"><span data-stu-id="4964f-129">Requirements</span></span>  
 <span data-ttu-id="4964f-130">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4964f-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4964f-131">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4964f-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4964f-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="4964f-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4964f-133">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4964f-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4964f-134">参照</span><span class="sxs-lookup"><span data-stu-id="4964f-134">See Also</span></span>  
 [<span data-ttu-id="4964f-135">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4964f-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="4964f-136">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4964f-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
