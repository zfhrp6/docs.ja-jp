---
title: IHostMAlloc::Free メソッド
ms.date: 03/30/2017
api_name:
- IHostMAlloc.Free
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::Free
helpviewer_keywords:
- IHostMAlloc::Free method [.NET Framework hosting]
- Free method, IHostMAlloc interface [.NET Framework hosting]
ms.assetid: c89abf5b-1120-4437-8b57-4a99fb3ae7f9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a8bd7b16f06433970d1222dbeaa843e187715faa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438998"
---
# <a name="ihostmallocfree-method"></a><span data-ttu-id="3ca16-102">IHostMAlloc::Free メソッド</span><span class="sxs-lookup"><span data-stu-id="3ca16-102">IHostMAlloc::Free Method</span></span>
<span data-ttu-id="3ca16-103">使用して割り当てられたメモリを解放、[アロケーション](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)関数。</span><span class="sxs-lookup"><span data-stu-id="3ca16-103">Frees memory that was allocated by using the [Alloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ca16-104">構文</span><span class="sxs-lookup"><span data-stu-id="3ca16-104">Syntax</span></span>  
  
```  
HRESULT Free (  
    [in] void* pMem  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3ca16-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3ca16-105">Parameters</span></span>  
 `pMem`  
 <span data-ttu-id="3ca16-106">[in]解放するメモリへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3ca16-106">[in] A pointer to the memory to be freed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ca16-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="3ca16-107">Return Value</span></span>  
  
|<span data-ttu-id="3ca16-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3ca16-108">HRESULT</span></span>|<span data-ttu-id="3ca16-109">説明</span><span class="sxs-lookup"><span data-stu-id="3ca16-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3ca16-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3ca16-110">S_OK</span></span>|<span data-ttu-id="3ca16-111">`Free` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="3ca16-111">`Free` returned successfully.</span></span>|  
|<span data-ttu-id="3ca16-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3ca16-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3ca16-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="3ca16-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3ca16-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3ca16-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3ca16-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="3ca16-115">The call timed out.</span></span>|  
|<span data-ttu-id="3ca16-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3ca16-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3ca16-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="3ca16-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3ca16-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3ca16-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3ca16-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="3ca16-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3ca16-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3ca16-120">E_FAIL</span></span>|<span data-ttu-id="3ca16-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="3ca16-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3ca16-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="3ca16-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3ca16-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="3ca16-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3ca16-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="3ca16-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="3ca16-125">ホストが割り当てられていないメモリを解放しようとしました。</span><span class="sxs-lookup"><span data-stu-id="3ca16-125">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ca16-126">コメント</span><span class="sxs-lookup"><span data-stu-id="3ca16-126">Remarks</span></span>  
 <span data-ttu-id="3ca16-127">場合、`pMem`パラメーターへの呼び出しを使用して、割り当てられていないメモリの領域を指す`Alloc`ホストが HOST_E_INVALIDOPERATION を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ca16-127">If the `pMem` parameter refers to a region of memory that was not allocated by using a call to `Alloc`, the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ca16-128">要件</span><span class="sxs-lookup"><span data-stu-id="3ca16-128">Requirements</span></span>  
 <span data-ttu-id="3ca16-129">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3ca16-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ca16-130">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3ca16-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3ca16-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="3ca16-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3ca16-132">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ca16-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ca16-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="3ca16-133">See Also</span></span>  
 [<span data-ttu-id="3ca16-134">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3ca16-134">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="3ca16-135">IHostMalloc インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3ca16-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
