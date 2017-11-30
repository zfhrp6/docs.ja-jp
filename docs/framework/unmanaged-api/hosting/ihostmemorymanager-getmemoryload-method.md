---
title: "IHostMemoryManager::GetMemoryLoad メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.GetMemoryLoad
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::GetMemoryLoad
helpviewer_keywords:
- IHostMemoryManager::GetMemoryLoad method [.NET Framework hosting]
- GetMemoryLoad method [.NET Framework hosting]
ms.assetid: e8138f6e-a0a4-48d4-8dae-9466b4dc6180
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7296790eb80fe90cd115150749e533ce1800834b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmemorymanagergetmemoryload-method"></a><span data-ttu-id="58b2a-102">IHostMemoryManager::GetMemoryLoad メソッド</span><span class="sxs-lookup"><span data-stu-id="58b2a-102">IHostMemoryManager::GetMemoryLoad Method</span></span>
<span data-ttu-id="58b2a-103">現在使用中で利用できない、ホストによって報告された、物理メモリの量を取得します。</span><span class="sxs-lookup"><span data-stu-id="58b2a-103">Gets the amount of physical memory that is currently in use, and therefore unavailable, as reported by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58b2a-104">構文</span><span class="sxs-lookup"><span data-stu-id="58b2a-104">Syntax</span></span>  
  
```  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,   
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="58b2a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="58b2a-105">Parameters</span></span>  
 `pMemoryLoad`  
 <span data-ttu-id="58b2a-106">[out]現在使用されている物理メモリの総量のおおよその割合を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="58b2a-106">[out] A pointer to the approximate percentage of total physical memory that is currently in use.</span></span>  
  
 `pAvailableBytes`  
 <span data-ttu-id="58b2a-107">[out]共通言語ランタイム (CLR) に使用できるバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="58b2a-107">[out] A pointer to the number of bytes available to the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="58b2a-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="58b2a-108">Return Value</span></span>  
  
|<span data-ttu-id="58b2a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="58b2a-109">HRESULT</span></span>|<span data-ttu-id="58b2a-110">説明</span><span class="sxs-lookup"><span data-stu-id="58b2a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="58b2a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="58b2a-111">S_OK</span></span>|<span data-ttu-id="58b2a-112">`GetMemoryLoad`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="58b2a-112">`GetMemoryLoad` returned successfully.</span></span>|  
|<span data-ttu-id="58b2a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="58b2a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="58b2a-114">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="58b2a-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="58b2a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="58b2a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="58b2a-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="58b2a-116">The call timed out.</span></span>|  
|<span data-ttu-id="58b2a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="58b2a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="58b2a-118">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="58b2a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="58b2a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="58b2a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="58b2a-120">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="58b2a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="58b2a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="58b2a-121">E_FAIL</span></span>|<span data-ttu-id="58b2a-122">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="58b2a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="58b2a-123">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="58b2a-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="58b2a-124">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="58b2a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58b2a-125">コメント</span><span class="sxs-lookup"><span data-stu-id="58b2a-125">Remarks</span></span>  
 <span data-ttu-id="58b2a-126">`GetMemoryLoad`Win32 のラップ`GlobalMemoryStatus`関数。</span><span class="sxs-lookup"><span data-stu-id="58b2a-126">`GetMemoryLoad` wraps the Win32 `GlobalMemoryStatus` function.</span></span> <span data-ttu-id="58b2a-127">値`pMemoryLoad`のと同じ、`dwMemoryLoad`フィールドで、`MEMORYSTATUS`から返される構造体`GlobalMemoryStatus`です。</span><span class="sxs-lookup"><span data-stu-id="58b2a-127">The value of `pMemoryLoad` is the equivalent of the `dwMemoryLoad` field in the `MEMORYSTATUS` structure returned from `GlobalMemoryStatus`.</span></span>  
  
 <span data-ttu-id="58b2a-128">ランタイムは、ガベージ コレクターのヒューリスティックとして戻り値を使用します。</span><span class="sxs-lookup"><span data-stu-id="58b2a-128">The runtime uses the return value as a heuristic for the garbage collector.</span></span> <span data-ttu-id="58b2a-129">たとえば、ホストは、そのメモリの大部分が使用を報告する場合、ガベージ コレクター高めても差し支え複数生成結果になることができます可能性のある使用可能なメモリの量を増やしてから収集します。</span><span class="sxs-lookup"><span data-stu-id="58b2a-129">For example, if the host reports that the majority of memory is in use, the garbage collector may elect to collect from multiple generations to increase the amount of memory that can potentially become available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58b2a-130">要件</span><span class="sxs-lookup"><span data-stu-id="58b2a-130">Requirements</span></span>  
 <span data-ttu-id="58b2a-131">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="58b2a-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58b2a-132">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="58b2a-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="58b2a-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="58b2a-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="58b2a-134">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58b2a-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58b2a-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="58b2a-135">See Also</span></span>  
 <xref:System.GC?displayProperty=nameWithType>  
 [<span data-ttu-id="58b2a-136">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="58b2a-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
