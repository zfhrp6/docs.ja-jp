---
title: "IHostMemoryManager::VirtualAlloc メソッド"
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
- IHostMemoryManager.VirtualAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualAlloc
helpviewer_keywords:
- VirtualAlloc method [.NET Framework hosting]
- IHostMemoryManager::VirtualAlloc method [.NET Framework hosting]
ms.assetid: 4dff3646-a050-4bd9-ac31-fe307e8637ec
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 761958c44ad374d522a52826929e320e65957ffa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmemorymanagervirtualalloc-method"></a><span data-ttu-id="1ed18-102">IHostMemoryManager::VirtualAlloc メソッド</span><span class="sxs-lookup"><span data-stu-id="1ed18-102">IHostMemoryManager::VirtualAlloc Method</span></span>
<span data-ttu-id="1ed18-103">対応する Win32 関数の論理ラッパーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="1ed18-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="1ed18-104">Win32 実装`VirtualAlloc`予約または呼び出し元のプロセス仮想アドレス空間内のページの領域をコミットします。</span><span class="sxs-lookup"><span data-stu-id="1ed18-104">The Win32 implementation of `VirtualAlloc` reserves or commits a region of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ed18-105">構文</span><span class="sxs-lookup"><span data-stu-id="1ed18-105">Syntax</span></span>  
  
```  
HRESULT VirtualAlloc (  
    [in]  void*   pAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flAllocationType,  
    [in]  DWORD   flProtect,  
    [in]  EMemoryCriticalLevel dwCriticalLevel,  
    [out] void**  ppMem  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1ed18-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1ed18-106">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="1ed18-107">[in]割り当てる領域の開始アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1ed18-107">[in] A pointer to the starting address of the region to allocate.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="1ed18-108">[in]領域のバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="1ed18-108">[in] The size, in bytes, of the region.</span></span>  
  
 `flAllocationType`  
 <span data-ttu-id="1ed18-109">[in]メモリの割り当ての種類。</span><span class="sxs-lookup"><span data-stu-id="1ed18-109">[in] The type of memory allocation.</span></span>  
  
 `flProtect`  
 <span data-ttu-id="1ed18-110">[in]割り当てられるページの領域のメモリ保護します。</span><span class="sxs-lookup"><span data-stu-id="1ed18-110">[in] Memory protection for the region of pages to be allocated.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="1ed18-111">[in][EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md)割り当てエラーの影響を示す値。</span><span class="sxs-lookup"><span data-stu-id="1ed18-111">[in] An [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) value that indicates the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="1ed18-112">[out]割り当てられたメモリは、または要求を処理できなかった場合は null の開始アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1ed18-112">[out] Pointer to the starting address of the allocated memory, or null if the request could not be satisfied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ed18-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="1ed18-113">Return Value</span></span>  
  
|<span data-ttu-id="1ed18-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1ed18-114">HRESULT</span></span>|<span data-ttu-id="1ed18-115">説明</span><span class="sxs-lookup"><span data-stu-id="1ed18-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1ed18-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="1ed18-116">S_OK</span></span>|<span data-ttu-id="1ed18-117">`VirtualAlloc`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="1ed18-117">`VirtualAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="1ed18-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1ed18-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1ed18-119">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="1ed18-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1ed18-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1ed18-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1ed18-121">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="1ed18-121">The call timed out.</span></span>|  
|<span data-ttu-id="1ed18-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1ed18-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1ed18-123">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="1ed18-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1ed18-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1ed18-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1ed18-125">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="1ed18-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1ed18-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1ed18-126">E_FAIL</span></span>|<span data-ttu-id="1ed18-127">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="1ed18-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1ed18-128">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="1ed18-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1ed18-129">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="1ed18-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1ed18-130">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="1ed18-130">E_OUTOFMEMORY</span></span>|<span data-ttu-id="1ed18-131">十分なメモリ割り当て要求を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="1ed18-131">Not enough memory was available to complete the allocation request</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ed18-132">コメント</span><span class="sxs-lookup"><span data-stu-id="1ed18-132">Remarks</span></span>  
 <span data-ttu-id="1ed18-133">呼び出すことによって、プロセスのアドレス空間内の領域を予約する`VirtualAlloc`です。</span><span class="sxs-lookup"><span data-stu-id="1ed18-133">You reserve a region in the address space of your process by calling `VirtualAlloc`.</span></span> <span data-ttu-id="1ed18-134">`pAddress`パラメーターには、必要なメモリ ブロックの開始アドレスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1ed18-134">The `pAddress` parameter contains the beginning address of the memory block you want.</span></span> <span data-ttu-id="1ed18-135">通常、このパラメーターは設定を null にします。</span><span class="sxs-lookup"><span data-stu-id="1ed18-135">This parameter is typically set to null.</span></span> <span data-ttu-id="1ed18-136">オペレーティング システムをプロセスに使用可能な空きアドレス範囲のレコードを保持します。</span><span class="sxs-lookup"><span data-stu-id="1ed18-136">The operating system keeps a record of free address ranges available to your process.</span></span> <span data-ttu-id="1ed18-137">A`pAddress`値は null に適した場所に、領域を予約するシステムに指示します。</span><span class="sxs-lookup"><span data-stu-id="1ed18-137">A `pAddress` value of null instructs the system to reserve the region wherever it sees fit.</span></span> <span data-ttu-id="1ed18-138">また、メモリ ブロックの特定の開始アドレスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="1ed18-138">Alternatively, you can provide a specific starting address for the memory block.</span></span> <span data-ttu-id="1ed18-139">どちらの場合も、出力パラメーター`ppMem`が割り当てられたメモリへのポインターとして返されます。</span><span class="sxs-lookup"><span data-stu-id="1ed18-139">In both cases, the output parameter `ppMem` is returned as a pointer to the allocated memory.</span></span> <span data-ttu-id="1ed18-140">関数自体では、HRESULT 値を返します。</span><span class="sxs-lookup"><span data-stu-id="1ed18-140">The function itself returns an HRESULT value.</span></span>  
  
 <span data-ttu-id="1ed18-141">Win32`VirtualAlloc`関数はありません、`ppMem`パラメーター、し、代わりに割り当てられたメモリへのポインターを返します。</span><span class="sxs-lookup"><span data-stu-id="1ed18-141">The Win32 `VirtualAlloc` function does not have a `ppMem` parameter, and returns the pointer to the allocated memory instead.</span></span> <span data-ttu-id="1ed18-142">詳細については、Windows プラットフォームのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ed18-142">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ed18-143">必要条件</span><span class="sxs-lookup"><span data-stu-id="1ed18-143">Requirements</span></span>  
 <span data-ttu-id="1ed18-144">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1ed18-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ed18-145">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1ed18-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1ed18-146">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="1ed18-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1ed18-147">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ed18-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ed18-148">参照</span><span class="sxs-lookup"><span data-stu-id="1ed18-148">See Also</span></span>  
 [<span data-ttu-id="1ed18-149">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1ed18-149">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
