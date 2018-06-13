---
title: IHostCrst::Leave メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae5561abb7cd0770fd5b7f290a4aa8dff85b6150
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441653"
---
# <a name="ihostcrstleave-method"></a><span data-ttu-id="5c79d-102">IHostCrst::Leave メソッド</span><span class="sxs-lookup"><span data-stu-id="5c79d-102">IHostCrst::Leave Method</span></span>
<span data-ttu-id="5c79d-103">現在のインスタンスで表されるクリティカル セクションのまま[IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="5c79d-103">Leaves the critical section that is represented by the current instance of [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c79d-104">構文</span><span class="sxs-lookup"><span data-stu-id="5c79d-104">Syntax</span></span>  
  
```  
HRESULT Leave ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="5c79d-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="5c79d-105">Return Value</span></span>  
  
|<span data-ttu-id="5c79d-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5c79d-106">HRESULT</span></span>|<span data-ttu-id="5c79d-107">説明</span><span class="sxs-lookup"><span data-stu-id="5c79d-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5c79d-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="5c79d-108">S_OK</span></span>|<span data-ttu-id="5c79d-109">`Leave` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="5c79d-109">`Leave` returned successfully.</span></span>|  
|<span data-ttu-id="5c79d-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5c79d-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5c79d-111">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="5c79d-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5c79d-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5c79d-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5c79d-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="5c79d-113">The call timed out.</span></span>|  
|<span data-ttu-id="5c79d-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5c79d-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5c79d-115">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="5c79d-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5c79d-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5c79d-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5c79d-117">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="5c79d-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5c79d-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5c79d-118">E_FAIL</span></span>|<span data-ttu-id="5c79d-119">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="5c79d-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5c79d-120">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="5c79d-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5c79d-121">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="5c79d-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c79d-122">コメント</span><span class="sxs-lookup"><span data-stu-id="5c79d-122">Remarks</span></span>  
 <span data-ttu-id="5c79d-123">`Leave` により、ホストの実装では、スレッド処理ではなく、対応する Win32 を使用して直接通信するために CLR`LeaveCriticalSection`関数。</span><span class="sxs-lookup"><span data-stu-id="5c79d-123">`Leave` allows the CLR to communicate directly with the host's threading implementation, rather than using the corresponding Win32 `LeaveCriticalSection` function.</span></span> <span data-ttu-id="5c79d-124">現在によって表される、クリティカル セクションの所有権を取得したスレッド`IHostCrst`インスタンスで呼び出す必要があります`Leave`時間ごとに、そのクリティカル セクションに入るとします。</span><span class="sxs-lookup"><span data-stu-id="5c79d-124">A thread that takes ownership of the critical section represented by the current `IHostCrst` instance must call `Leave` once for each time it enters that critical section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c79d-125">要件</span><span class="sxs-lookup"><span data-stu-id="5c79d-125">Requirements</span></span>  
 <span data-ttu-id="5c79d-126">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5c79d-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c79d-127">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5c79d-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5c79d-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="5c79d-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c79d-129">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c79d-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c79d-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="5c79d-130">See Also</span></span>  
 [<span data-ttu-id="5c79d-131">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5c79d-131">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="5c79d-132">IHostCrst インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5c79d-132">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="5c79d-133">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5c79d-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
