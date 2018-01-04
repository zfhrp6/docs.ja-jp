---
title: "IHostCrst::Enter メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostCrst.Enter
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostCrst::Enter
helpviewer_keywords:
- Enter method [.NET Framework hosting]
- IHostCrst::Enter method [.NET Framework hosting]
ms.assetid: 100dd7eb-7053-4295-9bb3-32ba47f6ec79
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 390f30c85dac494451af1ff82328c913dd9438ab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostcrstenter-method"></a><span data-ttu-id="1510e-102">IHostCrst::Enter メソッド</span><span class="sxs-lookup"><span data-stu-id="1510e-102">IHostCrst::Enter Method</span></span>
<span data-ttu-id="1510e-103">現在で表される重要なセクションに入ります[IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="1510e-103">Enters the critical section that is represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1510e-104">構文</span><span class="sxs-lookup"><span data-stu-id="1510e-104">Syntax</span></span>  
  
```  
HRESULT Enter (  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1510e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1510e-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="1510e-106">[in]1 つ、 [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)場合、ホストが実行するアクションを示す値、操作がブロックされます。</span><span class="sxs-lookup"><span data-stu-id="1510e-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1510e-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="1510e-107">Return Value</span></span>  
  
|<span data-ttu-id="1510e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1510e-108">HRESULT</span></span>|<span data-ttu-id="1510e-109">説明</span><span class="sxs-lookup"><span data-stu-id="1510e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1510e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1510e-110">S_OK</span></span>|<span data-ttu-id="1510e-111">`Enter`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="1510e-111">`Enter` returned successfully.</span></span>|  
|<span data-ttu-id="1510e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1510e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1510e-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="1510e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1510e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1510e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1510e-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="1510e-115">The call timed out.</span></span>|  
|<span data-ttu-id="1510e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1510e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1510e-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="1510e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1510e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1510e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1510e-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="1510e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1510e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1510e-120">E_FAIL</span></span>|<span data-ttu-id="1510e-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="1510e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1510e-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="1510e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1510e-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="1510e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1510e-124">コメント</span><span class="sxs-lookup"><span data-stu-id="1510e-124">Remarks</span></span>  
 <span data-ttu-id="1510e-125">`Enter`Win32 をミラー化`EnterCriticalSection`関数。</span><span class="sxs-lookup"><span data-stu-id="1510e-125">`Enter` mirrors the Win32 `EnterCriticalSection` function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1510e-126">このメソッドは、クリティカル セクションを入力するまでは返されません。</span><span class="sxs-lookup"><span data-stu-id="1510e-126">This method does not return until the critical section is entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1510e-127">必要条件</span><span class="sxs-lookup"><span data-stu-id="1510e-127">Requirements</span></span>  
 <span data-ttu-id="1510e-128">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1510e-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1510e-129">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1510e-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1510e-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="1510e-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1510e-131">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1510e-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1510e-132">参照</span><span class="sxs-lookup"><span data-stu-id="1510e-132">See Also</span></span>  
 [<span data-ttu-id="1510e-133">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1510e-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="1510e-134">IHostCrst インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1510e-134">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="1510e-135">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1510e-135">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
