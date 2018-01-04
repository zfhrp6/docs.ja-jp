---
title: "ICLRGCManager::SetGCStartupLimits メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRGCManager.SetGCStartupLimits
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRGCManager::SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: 1c8d9959-95b5-4131-be4a-556d97774014
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4fd5a1135866b75ea1d11fc5a14289104edfeac4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrgcmanagersetgcstartuplimits-method"></a><span data-ttu-id="5f062-102">ICLRGCManager::SetGCStartupLimits メソッド</span><span class="sxs-lookup"><span data-stu-id="5f062-102">ICLRGCManager::SetGCStartupLimits Method</span></span>
<span data-ttu-id="5f062-103">ガベージ コレクション セグメントのサイズと、ガベージ コレクション システムのジェネレーション 0 の最大サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="5f062-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5f062-104">以降で、[!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]セグメントのサイズを設定することができます、およびサイズの最大のジェネレーション 0 の値より大きい`DWORD`を使用して、 [iclrgcmanager 2::setgcstartuplimitsex](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="5f062-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f062-105">構文</span><span class="sxs-lookup"><span data-stu-id="5f062-105">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,   
    [in] DWORD MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5f062-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5f062-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="5f062-107">[in]ガベージ コレクション セグメントの指定したサイズ。</span><span class="sxs-lookup"><span data-stu-id="5f062-107">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="5f062-108">セグメントの最小サイズは、4 MB です。</span><span class="sxs-lookup"><span data-stu-id="5f062-108">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="5f062-109">セグメントには、1 mb 単位で増やす以上を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5f062-109">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="5f062-110">[in]ジェネレーション 0 の指定した最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="5f062-110">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="5f062-111">ジェネレーション 0 の最小サイズは、64 KB です。</span><span class="sxs-lookup"><span data-stu-id="5f062-111">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5f062-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="5f062-112">Return Value</span></span>  
  
|<span data-ttu-id="5f062-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5f062-113">HRESULT</span></span>|<span data-ttu-id="5f062-114">説明</span><span class="sxs-lookup"><span data-stu-id="5f062-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5f062-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="5f062-115">S_OK</span></span>|<span data-ttu-id="5f062-116">`SetGCStartupLimits`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="5f062-116">`SetGCStartupLimits` returned successfully.</span></span>|  
|<span data-ttu-id="5f062-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5f062-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5f062-118">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="5f062-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5f062-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5f062-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5f062-120">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="5f062-120">The call timed out.</span></span>|  
|<span data-ttu-id="5f062-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5f062-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5f062-122">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="5f062-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5f062-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5f062-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5f062-124">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="5f062-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5f062-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5f062-125">E_FAIL</span></span>|<span data-ttu-id="5f062-126">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="5f062-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5f062-127">メソッドには、E_FAIL が返された、後に、CLR はプロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="5f062-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5f062-128">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="5f062-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f062-129">コメント</span><span class="sxs-lookup"><span data-stu-id="5f062-129">Remarks</span></span>  
 <span data-ttu-id="5f062-130">値を`SetGCStartupLimits`セットは 1 回だけ指定できます。</span><span class="sxs-lookup"><span data-stu-id="5f062-130">The values that `SetGCStartupLimits` sets can be specified only once.</span></span> <span data-ttu-id="5f062-131">呼び出し後`SetGCStartupLimits`は無視されます。</span><span class="sxs-lookup"><span data-stu-id="5f062-131">Later calls to `SetGCStartupLimits` are ignored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f062-132">必要条件</span><span class="sxs-lookup"><span data-stu-id="5f062-132">Requirements</span></span>  
 <span data-ttu-id="5f062-133">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5f062-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f062-134">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5f062-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5f062-135">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="5f062-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5f062-136">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f062-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f062-137">参照</span><span class="sxs-lookup"><span data-stu-id="5f062-137">See Also</span></span>  
 [<span data-ttu-id="5f062-138">自動メモリ管理</span><span class="sxs-lookup"><span data-stu-id="5f062-138">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="5f062-139">ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="5f062-139">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)  
 [<span data-ttu-id="5f062-140">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5f062-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="5f062-141">ICLRGCManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5f062-141">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
