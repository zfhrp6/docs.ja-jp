---
title: "IHostMemoryManager::CreateMAlloc メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.CreateMAlloc
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::CreateMAlloc
helpviewer_keywords:
- CreateAlloc method [.NET Framework hosting]
- IHostMemoryManager::CreateMAlloc method [.NET Framework hosting]
ms.assetid: 9ee6e052-bef7-4350-9e4f-edfffd99ad6f
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 19b43ccf7cb2429c28c052ab8ab3a009ec4a30a4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmemorymanagercreatemalloc-method"></a><span data-ttu-id="cb8f8-102">IHostMemoryManager::CreateMAlloc メソッド</span><span class="sxs-lookup"><span data-stu-id="cb8f8-102">IHostMemoryManager::CreateMAlloc Method</span></span>
<span data-ttu-id="cb8f8-103">インターフェイス ポインターを取得、 [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)インスタンス、ホストが作成したヒープから割り当て要求を作成するために使用します。</span><span class="sxs-lookup"><span data-stu-id="cb8f8-103">Gets an interface pointer to an [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance that is used to make allocation requests from a heap created by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb8f8-104">構文</span><span class="sxs-lookup"><span data-stu-id="cb8f8-104">Syntax</span></span>  
  
```  
HRESULT CreateMalloc (  
    [in]  DWORD         dwMallocType,  
    [out] IHostMalloc **ppMalloc  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cb8f8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cb8f8-105">Parameters</span></span>  
 `dwMallocType`  
 <span data-ttu-id="cb8f8-106">[in]組み合わせた[MALLOC_TYPE](../../../../docs/framework/unmanaged-api/hosting/malloc-type-enumeration.md)割り当てられるメモリの特性を示すフラグ。</span><span class="sxs-lookup"><span data-stu-id="cb8f8-106">[in] A combination of [MALLOC_TYPE](../../../../docs/framework/unmanaged-api/hosting/malloc-type-enumeration.md) flags that specifies the characteristics of the memory that is being allocated.</span></span>  
  
 `ppMAlloc`  
 <span data-ttu-id="cb8f8-107">[out]アドレスへのポインター、`IHostMAlloc`ホストによって指定されたインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="cb8f8-107">[out] A pointer to the address of an `IHostMAlloc` instance provided by the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb8f8-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="cb8f8-108">Return Value</span></span>  
  
|<span data-ttu-id="cb8f8-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cb8f8-109">HRESULT</span></span>|<span data-ttu-id="cb8f8-110">説明</span><span class="sxs-lookup"><span data-stu-id="cb8f8-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cb8f8-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="cb8f8-111">S_OK</span></span>|<span data-ttu-id="cb8f8-112">`CreateMAlloc`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="cb8f8-112">`CreateMAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="cb8f8-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cb8f8-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cb8f8-114">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="cb8f8-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cb8f8-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cb8f8-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cb8f8-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="cb8f8-116">The call timed out.</span></span>|  
|<span data-ttu-id="cb8f8-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cb8f8-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cb8f8-118">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="cb8f8-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cb8f8-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cb8f8-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cb8f8-120">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="cb8f8-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cb8f8-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cb8f8-121">E_FAIL</span></span>|<span data-ttu-id="cb8f8-122">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="cb8f8-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cb8f8-123">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="cb8f8-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cb8f8-124">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="cb8f8-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="cb8f8-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="cb8f8-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="cb8f8-126">十分な物理メモリは、割り当て要求を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="cb8f8-126">Not enough physical memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb8f8-127">コメント</span><span class="sxs-lookup"><span data-stu-id="cb8f8-127">Remarks</span></span>  
 <span data-ttu-id="cb8f8-128">`CreateMAlloc`標準の Win32 関数を使用する代わりに、ホストを通じて割り当て要求を行う CLR をできるようにするオブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="cb8f8-128">`CreateMAlloc` returns an object that allows the CLR to make allocation requests through the host instead of using the standard Win32 functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb8f8-129">必要条件</span><span class="sxs-lookup"><span data-stu-id="cb8f8-129">Requirements</span></span>  
 <span data-ttu-id="cb8f8-130">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cb8f8-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb8f8-131">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cb8f8-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cb8f8-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="cb8f8-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cb8f8-133">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb8f8-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb8f8-134">参照</span><span class="sxs-lookup"><span data-stu-id="cb8f8-134">See Also</span></span>  
 [<span data-ttu-id="cb8f8-135">IHostMalloc インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cb8f8-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 [<span data-ttu-id="cb8f8-136">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cb8f8-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
