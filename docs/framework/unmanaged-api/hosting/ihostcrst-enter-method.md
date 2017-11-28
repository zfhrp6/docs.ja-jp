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
ms.openlocfilehash: 9d209e13360616295f166ad23c65b0c4e764af79
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ihostcrstenter-method"></a><span data-ttu-id="913aa-102">IHostCrst::Enter メソッド</span><span class="sxs-lookup"><span data-stu-id="913aa-102">IHostCrst::Enter Method</span></span>
<span data-ttu-id="913aa-103">現在で表される重要なセクションに入ります[IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="913aa-103">Enters the critical section that is represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="913aa-104">構文</span><span class="sxs-lookup"><span data-stu-id="913aa-104">Syntax</span></span>  
  
```  
HRESULT Enter (  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="913aa-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="913aa-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="913aa-106">[in]1 つ、 [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md)場合、ホストが実行するアクションを示す値、操作がブロックされます。</span><span class="sxs-lookup"><span data-stu-id="913aa-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="913aa-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="913aa-107">Return Value</span></span>  
  
|<span data-ttu-id="913aa-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="913aa-108">HRESULT</span></span>|<span data-ttu-id="913aa-109">説明</span><span class="sxs-lookup"><span data-stu-id="913aa-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="913aa-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="913aa-110">S_OK</span></span>|<span data-ttu-id="913aa-111">`Enter`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="913aa-111">`Enter` returned successfully.</span></span>|  
|<span data-ttu-id="913aa-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="913aa-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="913aa-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="913aa-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="913aa-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="913aa-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="913aa-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="913aa-115">The call timed out.</span></span>|  
|<span data-ttu-id="913aa-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="913aa-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="913aa-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="913aa-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="913aa-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="913aa-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="913aa-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="913aa-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="913aa-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="913aa-120">E_FAIL</span></span>|<span data-ttu-id="913aa-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="913aa-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="913aa-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="913aa-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="913aa-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="913aa-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="913aa-124">コメント</span><span class="sxs-lookup"><span data-stu-id="913aa-124">Remarks</span></span>  
 <span data-ttu-id="913aa-125">`Enter`Win32 をミラー化`EnterCriticalSection`関数。</span><span class="sxs-lookup"><span data-stu-id="913aa-125">`Enter` mirrors the Win32 `EnterCriticalSection` function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="913aa-126">このメソッドは、クリティカル セクションを入力するまでは返されません。</span><span class="sxs-lookup"><span data-stu-id="913aa-126">This method does not return until the critical section is entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="913aa-127">要件</span><span class="sxs-lookup"><span data-stu-id="913aa-127">Requirements</span></span>  
 <span data-ttu-id="913aa-128">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="913aa-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="913aa-129">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="913aa-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="913aa-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="913aa-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="913aa-131">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="913aa-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="913aa-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="913aa-132">See Also</span></span>  
 [<span data-ttu-id="913aa-133">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="913aa-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="913aa-134">IHostCrst インターフェイス</span><span class="sxs-lookup"><span data-stu-id="913aa-134">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="913aa-135">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="913aa-135">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
