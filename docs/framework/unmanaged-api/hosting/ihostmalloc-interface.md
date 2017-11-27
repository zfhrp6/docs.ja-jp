---
title: "IHostMalloc インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMAlloc
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMAlloc
helpviewer_keywords: IHostMAlloc interface [.NET Framework hosting]
ms.assetid: e3c6643b-6fc7-4a99-959d-4b7b4e63fdee
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f788456065a5508441b9fec38ad4a7f531f9f303
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmalloc-interface"></a><span data-ttu-id="50eb9-102">IHostMalloc インターフェイス</span><span class="sxs-lookup"><span data-stu-id="50eb9-102">IHostMalloc Interface</span></span>
<span data-ttu-id="50eb9-103">共通言語ランタイム (CLR) にはホストを介してヒープから詳細な割り当てを要求できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="50eb9-103">Provides methods that allow the common language runtime (CLR) to request fine-grained allocations from the heap through the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="50eb9-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="50eb9-104">Methods</span></span>  
  
|<span data-ttu-id="50eb9-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="50eb9-105">Method</span></span>|<span data-ttu-id="50eb9-106">説明</span><span class="sxs-lookup"><span data-stu-id="50eb9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="50eb9-107">Alloc メソッド</span><span class="sxs-lookup"><span data-stu-id="50eb9-107">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|<span data-ttu-id="50eb9-108">要求のホストが、ヒープから要求されたメモリ量を割り当てることです。</span><span class="sxs-lookup"><span data-stu-id="50eb9-108">Requests that the host allocate the requested amount of memory from the heap.</span></span>|  
|[<span data-ttu-id="50eb9-109">DebugAlloc メソッド</span><span class="sxs-lookup"><span data-stu-id="50eb9-109">DebugAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|<span data-ttu-id="50eb9-110">ホストが、ヒープから要求されたメモリ量を割り当てるし、さらに、メモリが割り当てられた場所を追跡を要求します。</span><span class="sxs-lookup"><span data-stu-id="50eb9-110">Requests that the host allocate the requested amount of memory from the heap, and additionally track where the memory was allocated.</span></span>|  
|[<span data-ttu-id="50eb9-111">Free メソッド</span><span class="sxs-lookup"><span data-stu-id="50eb9-111">Free Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|<span data-ttu-id="50eb9-112">使用して割り当てられたメモリを解放、`Alloc`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="50eb9-112">Frees memory that was allocated by using the `Alloc` method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50eb9-113">コメント</span><span class="sxs-lookup"><span data-stu-id="50eb9-113">Remarks</span></span>  
 <span data-ttu-id="50eb9-114">CLR へのインターフェイス ポインターの取得、`IHostMalloc`を呼び出してインスタンス、 [ihostmemorymanager::createmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="50eb9-114">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50eb9-115">要件</span><span class="sxs-lookup"><span data-stu-id="50eb9-115">Requirements</span></span>  
 <span data-ttu-id="50eb9-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="50eb9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50eb9-117">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="50eb9-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="50eb9-118">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="50eb9-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50eb9-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50eb9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50eb9-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="50eb9-120">See Also</span></span>  
 [<span data-ttu-id="50eb9-121">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="50eb9-121">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="50eb9-122">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="50eb9-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
