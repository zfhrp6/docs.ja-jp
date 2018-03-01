---
title: "IHostCrst::Leave メソッド"
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
- IHostCrst.Leave
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::Leave
helpviewer_keywords:
- IHostCrst::Leave method [.NET Framework hosting]
- Leave method [.NET Framework hosting]
ms.assetid: dfc51d9e-b36d-4dba-9ea1-4f63fa0601ae
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 391aff3920e7ea2ef010ce7d97bdedb4e636dc86
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostcrstleave-method"></a><span data-ttu-id="3e038-102">IHostCrst::Leave メソッド</span><span class="sxs-lookup"><span data-stu-id="3e038-102">IHostCrst::Leave Method</span></span>
<span data-ttu-id="3e038-103">現在のインスタンスで表されるクリティカル セクションのまま[IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="3e038-103">Leaves the critical section that is represented by the current instance of [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e038-104">構文</span><span class="sxs-lookup"><span data-stu-id="3e038-104">Syntax</span></span>  
  
```  
HRESULT Leave ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="3e038-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="3e038-105">Return Value</span></span>  
  
|<span data-ttu-id="3e038-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3e038-106">HRESULT</span></span>|<span data-ttu-id="3e038-107">説明</span><span class="sxs-lookup"><span data-stu-id="3e038-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3e038-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="3e038-108">S_OK</span></span>|<span data-ttu-id="3e038-109">`Leave`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="3e038-109">`Leave` returned successfully.</span></span>|  
|<span data-ttu-id="3e038-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3e038-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3e038-111">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="3e038-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3e038-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3e038-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3e038-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="3e038-113">The call timed out.</span></span>|  
|<span data-ttu-id="3e038-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3e038-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3e038-115">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="3e038-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3e038-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3e038-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3e038-117">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="3e038-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3e038-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3e038-118">E_FAIL</span></span>|<span data-ttu-id="3e038-119">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="3e038-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3e038-120">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="3e038-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3e038-121">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="3e038-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e038-122">コメント</span><span class="sxs-lookup"><span data-stu-id="3e038-122">Remarks</span></span>  
 <span data-ttu-id="3e038-123">`Leave`により、ホストの実装では、スレッド処理ではなく、対応する Win32 を使用して直接通信するために CLR`LeaveCriticalSection`関数。</span><span class="sxs-lookup"><span data-stu-id="3e038-123">`Leave` allows the CLR to communicate directly with the host's threading implementation, rather than using the corresponding Win32 `LeaveCriticalSection` function.</span></span> <span data-ttu-id="3e038-124">現在によって表される、クリティカル セクションの所有権を取得したスレッド`IHostCrst`インスタンスで呼び出す必要があります`Leave`時間ごとに、そのクリティカル セクションに入るとします。</span><span class="sxs-lookup"><span data-stu-id="3e038-124">A thread that takes ownership of the critical section represented by the current `IHostCrst` instance must call `Leave` once for each time it enters that critical section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e038-125">必要条件</span><span class="sxs-lookup"><span data-stu-id="3e038-125">Requirements</span></span>  
 <span data-ttu-id="3e038-126">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3e038-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e038-127">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3e038-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3e038-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="3e038-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3e038-129">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e038-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e038-130">参照</span><span class="sxs-lookup"><span data-stu-id="3e038-130">See Also</span></span>  
 [<span data-ttu-id="3e038-131">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3e038-131">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="3e038-132">IHostCrst インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3e038-132">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="3e038-133">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3e038-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
