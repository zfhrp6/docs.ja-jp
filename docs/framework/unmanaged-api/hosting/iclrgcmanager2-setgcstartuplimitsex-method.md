---
title: "ICLRGCManager2::SetGCStartupLimitsEx メソッド"
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
- ICLRGCManager2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2::SetCLRGCStartupLimitsEx
helpviewer_keywords:
- ICLRGCManager2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 6c3a08a9-5d65-48d4-8bbf-2a86ed7d356a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 371d6d32b3f9f5da0411234438972a8d2df4cc3b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a><span data-ttu-id="9fe3f-102">ICLRGCManager2::SetGCStartupLimitsEx メソッド</span><span class="sxs-lookup"><span data-stu-id="9fe3f-102">ICLRGCManager2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="9fe3f-103">ガベージ コレクション セグメントのサイズと、ガベージ コレクション システムのジェネレーション 0 の最大サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="9fe3f-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fe3f-104">構文</span><span class="sxs-lookup"><span data-stu-id="9fe3f-104">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,   
    [in] SIZE_T MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9fe3f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9fe3f-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="9fe3f-106">[in]ガベージ コレクション セグメントの指定したサイズ。</span><span class="sxs-lookup"><span data-stu-id="9fe3f-106">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="9fe3f-107">セグメントの最小サイズは、4 MB です。</span><span class="sxs-lookup"><span data-stu-id="9fe3f-107">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="9fe3f-108">セグメントには、1 mb 単位で増やす以上を指定できます。</span><span class="sxs-lookup"><span data-stu-id="9fe3f-108">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="9fe3f-109">[in]ジェネレーション 0 の指定した最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="9fe3f-109">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="9fe3f-110">ジェネレーション 0 の最小サイズは、64 KB です。</span><span class="sxs-lookup"><span data-stu-id="9fe3f-110">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9fe3f-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="9fe3f-111">Return Value</span></span>  
  
|<span data-ttu-id="9fe3f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9fe3f-112">HRESULT</span></span>|<span data-ttu-id="9fe3f-113">説明</span><span class="sxs-lookup"><span data-stu-id="9fe3f-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9fe3f-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="9fe3f-114">S_OK</span></span>|<span data-ttu-id="9fe3f-115">`SetGCStartupLimitsEx`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="9fe3f-115">`SetGCStartupLimitsEx` returned successfully.</span></span>|  
|<span data-ttu-id="9fe3f-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9fe3f-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9fe3f-117">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="9fe3f-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9fe3f-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9fe3f-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9fe3f-119">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="9fe3f-119">The call timed out.</span></span>|  
|<span data-ttu-id="9fe3f-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9fe3f-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9fe3f-121">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="9fe3f-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9fe3f-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9fe3f-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9fe3f-123">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="9fe3f-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9fe3f-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9fe3f-124">E_FAIL</span></span>|<span data-ttu-id="9fe3f-125">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="9fe3f-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9fe3f-126">メソッドには、E_FAIL が返された、後に、CLR はプロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="9fe3f-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9fe3f-127">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="9fe3f-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9fe3f-128">コメント</span><span class="sxs-lookup"><span data-stu-id="9fe3f-128">Remarks</span></span>  
 <span data-ttu-id="9fe3f-129">値を`SetGCStartupLimitsEx`ホストを起動する前に、セットを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="9fe3f-129">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="9fe3f-130">呼び出し後`SetGCStartupLimitsEx`は無視されます。</span><span class="sxs-lookup"><span data-stu-id="9fe3f-130">Later calls to `SetGCStartupLimitsEx` are ignored.</span></span>  
  
 <span data-ttu-id="9fe3f-131">他の影響を与えずにどちらかのパラメーターを設定するには、変更しないパラメーターを 0 (ゼロ) を指定します。</span><span class="sxs-lookup"><span data-stu-id="9fe3f-131">To set either parameter without affecting the other, specify 0 (zero) for the parameter you don't want to change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fe3f-132">必要条件</span><span class="sxs-lookup"><span data-stu-id="9fe3f-132">Requirements</span></span>  
 <span data-ttu-id="9fe3f-133">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9fe3f-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fe3f-134">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9fe3f-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9fe3f-135">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="9fe3f-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9fe3f-136">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fe3f-136">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fe3f-137">参照</span><span class="sxs-lookup"><span data-stu-id="9fe3f-137">See Also</span></span>  
 [<span data-ttu-id="9fe3f-138">自動メモリ管理</span><span class="sxs-lookup"><span data-stu-id="9fe3f-138">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="9fe3f-139">ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="9fe3f-139">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)  
 [<span data-ttu-id="9fe3f-140">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9fe3f-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="9fe3f-141">ICLRGCManager2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9fe3f-141">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)
