---
title: "IHostMAlloc::Alloc メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMAlloc.Alloc
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMAlloc::Alloc
helpviewer_keywords:
- Alloc method, IHostMAlloc interface [.NET Framework hosting]
- IHostMAlloc::Alloc method [.NET Framework hosting]
ms.assetid: a3007f5e-d75d-4b37-842b-704e9edced5e
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d999425be2bc5963aaa9f15b82bd951f6f564af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmallocalloc-method"></a><span data-ttu-id="30768-102">IHostMAlloc::Alloc メソッド</span><span class="sxs-lookup"><span data-stu-id="30768-102">IHostMAlloc::Alloc Method</span></span>
<span data-ttu-id="30768-103">要求のホストが、ヒープから指定されたメモリ量を割り当てることです。</span><span class="sxs-lookup"><span data-stu-id="30768-103">Requests that the host allocate the specified amount of memory from the heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30768-104">構文</span><span class="sxs-lookup"><span data-stu-id="30768-104">Syntax</span></span>  
  
```  
HRESULT Alloc (  
    [in] SIZE_T  cbSize,   
    [in] EMemoryCriticalLevel dwCriticalLevel,   
    [out] void** ppMem  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="30768-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="30768-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="30768-106">[in]現在のメモリ割り当て要求のバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="30768-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="30768-107">[in]1 つ、 [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md)割り当てエラーの影響を示す値。</span><span class="sxs-lookup"><span data-stu-id="30768-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="30768-108">[out]ポインター、割り当てられたメモリは、または null の場合は、要求を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="30768-108">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30768-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="30768-109">Return Value</span></span>  
  
|<span data-ttu-id="30768-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="30768-110">HRESULT</span></span>|<span data-ttu-id="30768-111">説明</span><span class="sxs-lookup"><span data-stu-id="30768-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="30768-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="30768-112">S_OK</span></span>|<span data-ttu-id="30768-113">`Alloc`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="30768-113">`Alloc` returned successfully.</span></span>|  
|<span data-ttu-id="30768-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="30768-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="30768-115">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="30768-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="30768-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="30768-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="30768-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="30768-117">The call timed out.</span></span>|  
|<span data-ttu-id="30768-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="30768-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="30768-119">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="30768-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="30768-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="30768-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="30768-121">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="30768-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="30768-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="30768-122">E_FAIL</span></span>|<span data-ttu-id="30768-123">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="30768-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="30768-124">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="30768-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="30768-125">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="30768-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="30768-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="30768-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="30768-127">十分なメモリ割り当て要求を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="30768-127">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30768-128">コメント</span><span class="sxs-lookup"><span data-stu-id="30768-128">Remarks</span></span>  
 <span data-ttu-id="30768-129">CLR へのインターフェイス ポインターの取得、`IHostMalloc`を呼び出してインスタンス、 [ihostmemorymanager::createmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="30768-129">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30768-130">必要条件</span><span class="sxs-lookup"><span data-stu-id="30768-130">Requirements</span></span>  
 <span data-ttu-id="30768-131">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="30768-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30768-132">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="30768-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="30768-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="30768-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="30768-134">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30768-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30768-135">参照</span><span class="sxs-lookup"><span data-stu-id="30768-135">See Also</span></span>  
 [<span data-ttu-id="30768-136">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="30768-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="30768-137">IHostMalloc インターフェイス</span><span class="sxs-lookup"><span data-stu-id="30768-137">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
