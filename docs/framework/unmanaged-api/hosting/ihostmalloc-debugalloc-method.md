---
title: IHostMAlloc::DebugAlloc メソッド
ms.date: 03/30/2017
api_name:
- IHostMAlloc.DebugAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::DebugAlloc
helpviewer_keywords:
- DebugAlloc method [.NET Framework hosting]
- IHostMAlloc::DebugAlloc method [.NET Framework hosting]
ms.assetid: 0bfbc527-bea2-43ce-b041-69186f4440dd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8447f6fa2771128c1bdf424cb9aac141b2dfd486
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="ihostmallocdebugalloc-method"></a><span data-ttu-id="1fe1a-102">IHostMAlloc::DebugAlloc メソッド</span><span class="sxs-lookup"><span data-stu-id="1fe1a-102">IHostMAlloc::DebugAlloc Method</span></span>
<span data-ttu-id="1fe1a-103">ホストが、ヒープから指定されたメモリ量を割り当てるし、さらに、メモリが割り当てられた場所を追跡を要求します。</span><span class="sxs-lookup"><span data-stu-id="1fe1a-103">Requests that the host allocate the specified amount of memory from the heap, and additionally track where the memory was allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fe1a-104">構文</span><span class="sxs-lookup"><span data-stu-id="1fe1a-104">Syntax</span></span>  
  
```  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,   
    [in]  EMemoryCriticalLevel dwCriticalLevel,   
    [in]  char*   pszFileName,   
    [in]  int     iLineNo,   
    [out] void**  ppMem  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1fe1a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1fe1a-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="1fe1a-106">[in]現在のメモリ割り当て要求のバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="1fe1a-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="1fe1a-107">[in]1 つ、 [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md)割り当てエラーの影響を示す値。</span><span class="sxs-lookup"><span data-stu-id="1fe1a-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="1fe1a-108">[in]デバッグされている実行可能ファイルのコード ファイル。</span><span class="sxs-lookup"><span data-stu-id="1fe1a-108">[in] The code file of the executable being debugged.</span></span>  
  
 `iLineNo`  
 <span data-ttu-id="1fe1a-109">[in]内の行番号`pszFileName`割り当てが要求されました。</span><span class="sxs-lookup"><span data-stu-id="1fe1a-109">[in] The line number in `pszFileName` where the allocation was requested.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="1fe1a-110">[out]ポインター、割り当てられたメモリは、または null の場合は、要求を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="1fe1a-110">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1fe1a-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="1fe1a-111">Return Value</span></span>  
  
|<span data-ttu-id="1fe1a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1fe1a-112">HRESULT</span></span>|<span data-ttu-id="1fe1a-113">説明</span><span class="sxs-lookup"><span data-stu-id="1fe1a-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1fe1a-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="1fe1a-114">S_OK</span></span>|<span data-ttu-id="1fe1a-115">`DebugAlloc` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="1fe1a-115">`DebugAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="1fe1a-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1fe1a-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1fe1a-117">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="1fe1a-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1fe1a-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1fe1a-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1fe1a-119">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="1fe1a-119">The call timed out.</span></span>|  
|<span data-ttu-id="1fe1a-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1fe1a-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1fe1a-121">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="1fe1a-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1fe1a-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1fe1a-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1fe1a-123">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="1fe1a-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1fe1a-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1fe1a-124">E_FAIL</span></span>|<span data-ttu-id="1fe1a-125">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="1fe1a-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1fe1a-126">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="1fe1a-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1fe1a-127">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="1fe1a-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1fe1a-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="1fe1a-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="1fe1a-129">十分なメモリ割り当て要求を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="1fe1a-129">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1fe1a-130">コメント</span><span class="sxs-lookup"><span data-stu-id="1fe1a-130">Remarks</span></span>  
 <span data-ttu-id="1fe1a-131">CLR へのインターフェイス ポインターの取得、 [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)を呼び出してインスタンス、 [ihostmemorymanager::createmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="1fe1a-131">The CLR gets an interface pointer to an [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span> <span data-ttu-id="1fe1a-132">`DebugAlloc` により、デバッグ中に使用するためのコード ファイルの情報を取得するランタイム。</span><span class="sxs-lookup"><span data-stu-id="1fe1a-132">`DebugAlloc` allows the runtime to get code file information for use during debugging.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fe1a-133">要件</span><span class="sxs-lookup"><span data-stu-id="1fe1a-133">Requirements</span></span>  
 <span data-ttu-id="1fe1a-134">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1fe1a-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fe1a-135">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1fe1a-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1fe1a-136">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="1fe1a-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1fe1a-137">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fe1a-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fe1a-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="1fe1a-138">See Also</span></span>  
 [<span data-ttu-id="1fe1a-139">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1fe1a-139">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="1fe1a-140">IHostMalloc インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1fe1a-140">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
