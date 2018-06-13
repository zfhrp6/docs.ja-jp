---
title: IHostMalloc インターフェイス
ms.date: 03/30/2017
api_name:
- IHostMAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc
helpviewer_keywords:
- IHostMAlloc interface [.NET Framework hosting]
ms.assetid: e3c6643b-6fc7-4a99-959d-4b7b4e63fdee
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bbf889aaa6a78e67d0f08758adc0bf31cd932e88
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441349"
---
# <a name="ihostmalloc-interface"></a><span data-ttu-id="6ce79-102">IHostMalloc インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6ce79-102">IHostMalloc Interface</span></span>
<span data-ttu-id="6ce79-103">共通言語ランタイム (CLR) にはホストを介してヒープから詳細な割り当てを要求できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="6ce79-103">Provides methods that allow the common language runtime (CLR) to request fine-grained allocations from the heap through the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6ce79-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="6ce79-104">Methods</span></span>  
  
|<span data-ttu-id="6ce79-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="6ce79-105">Method</span></span>|<span data-ttu-id="6ce79-106">説明</span><span class="sxs-lookup"><span data-stu-id="6ce79-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6ce79-107">Alloc メソッド</span><span class="sxs-lookup"><span data-stu-id="6ce79-107">Alloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|<span data-ttu-id="6ce79-108">要求のホストが、ヒープから要求されたメモリ量を割り当てることです。</span><span class="sxs-lookup"><span data-stu-id="6ce79-108">Requests that the host allocate the requested amount of memory from the heap.</span></span>|  
|[<span data-ttu-id="6ce79-109">DebugAlloc メソッド</span><span class="sxs-lookup"><span data-stu-id="6ce79-109">DebugAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|<span data-ttu-id="6ce79-110">ホストが、ヒープから要求されたメモリ量を割り当てるし、さらに、メモリが割り当てられた場所を追跡を要求します。</span><span class="sxs-lookup"><span data-stu-id="6ce79-110">Requests that the host allocate the requested amount of memory from the heap, and additionally track where the memory was allocated.</span></span>|  
|[<span data-ttu-id="6ce79-111">Free メソッド</span><span class="sxs-lookup"><span data-stu-id="6ce79-111">Free Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|<span data-ttu-id="6ce79-112">使用して割り当てられたメモリを解放、`Alloc`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="6ce79-112">Frees memory that was allocated by using the `Alloc` method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ce79-113">コメント</span><span class="sxs-lookup"><span data-stu-id="6ce79-113">Remarks</span></span>  
 <span data-ttu-id="6ce79-114">CLR へのインターフェイス ポインターの取得、`IHostMalloc`を呼び出してインスタンス、 [ihostmemorymanager::createmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="6ce79-114">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ce79-115">要件</span><span class="sxs-lookup"><span data-stu-id="6ce79-115">Requirements</span></span>  
 <span data-ttu-id="6ce79-116">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6ce79-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ce79-117">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6ce79-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6ce79-118">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="6ce79-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6ce79-119">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ce79-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ce79-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="6ce79-120">See Also</span></span>  
 [<span data-ttu-id="6ce79-121">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6ce79-121">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="6ce79-122">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6ce79-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
