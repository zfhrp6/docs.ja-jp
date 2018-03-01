---
title: "IHostMemoryManager インターフェイス"
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
- IHostMemoryManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager
helpviewer_keywords:
- IHostMemoryManager interface [.NET Framework hosting]
ms.assetid: a945d439-3b34-4aa4-b575-8413dd7806ce
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b39a43874bc1808928f21e0a35638aae9a99ca8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmemorymanager-interface"></a><span data-ttu-id="3cb95-102">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3cb95-102">IHostMemoryManager Interface</span></span>
<span data-ttu-id="3cb95-103">標準の Win32 仮想メモリ関数を使用する代わりに、共通言語ランタイム (CLR) はホストを介して仮想メモリの要求を行うことができるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="3cb95-103">Provides methods that allow the common language runtime (CLR) to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3cb95-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="3cb95-104">Methods</span></span>  
  
|<span data-ttu-id="3cb95-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="3cb95-105">Method</span></span>|<span data-ttu-id="3cb95-106">説明</span><span class="sxs-lookup"><span data-stu-id="3cb95-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3cb95-107">AcquiredVirtualAddressSpace メソッド</span><span class="sxs-lookup"><span data-stu-id="3cb95-107">AcquiredVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|<span data-ttu-id="3cb95-108">共通言語ランタイム (CLR) が、オペレーティング システムから指定されたメモリを取得したことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="3cb95-108">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>|  
|[<span data-ttu-id="3cb95-109">CreateMAlloc メソッド</span><span class="sxs-lookup"><span data-stu-id="3cb95-109">CreateMAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|<span data-ttu-id="3cb95-110">インターフェイス ポインターを取得、 [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)ホストによって作成されたヒープからメモリの割り当てを要求するために使用するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="3cb95-110">Gets an interface pointer to an [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance that is used to request memory allocations from a heap created by the host.</span></span>|  
|[<span data-ttu-id="3cb95-111">GetMemoryLoad メソッド</span><span class="sxs-lookup"><span data-stu-id="3cb95-111">GetMemoryLoad Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|<span data-ttu-id="3cb95-112">ホストで報告された、現在使用されている物理メモリの量を取得します。</span><span class="sxs-lookup"><span data-stu-id="3cb95-112">Gets the amount of physical memory that is currently being used, as reported by the host.</span></span>|  
|[<span data-ttu-id="3cb95-113">NeedsVirtualAddressSpace メソッド</span><span class="sxs-lookup"><span data-stu-id="3cb95-113">NeedsVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|<span data-ttu-id="3cb95-114">CLR が指定されたメモリを使用しようとしています。 しようとしていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="3cb95-114">Notifies the host that the CLR is going to attempt to use the specified memory.</span></span>|  
|[<span data-ttu-id="3cb95-115">RegisterMemoryNotificationCallback メソッド</span><span class="sxs-lookup"><span data-stu-id="3cb95-115">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|<span data-ttu-id="3cb95-116">ホストが、現在のメモリ負荷、コンピューター上の CLR に通知するために呼び出すコールバック関数へのポインターを登録します。</span><span class="sxs-lookup"><span data-stu-id="3cb95-116">Registers a pointer to a callback function that the host invokes to notify the CLR of the current memory load on the computer.</span></span>|  
|[<span data-ttu-id="3cb95-117">ReleasedVirtualAddressSpace メソッド</span><span class="sxs-lookup"><span data-stu-id="3cb95-117">ReleasedVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|<span data-ttu-id="3cb95-118">指定されたメモリを使用して、CLR が完了したことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="3cb95-118">Notifies the host that the CLR has finished using the specified memory.</span></span>|  
|[<span data-ttu-id="3cb95-119">VirtualAlloc メソッド</span><span class="sxs-lookup"><span data-stu-id="3cb95-119">VirtualAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|<span data-ttu-id="3cb95-120">対応する Win32 関数では、予約または呼び出し元のプロセス仮想アドレス空間内のページの領域をコミットの論理ラッパーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="3cb95-120">Serves as a logical wrapper for the corresponding Win32 function, which reserves or commits a region of pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="3cb95-121">VirtualFree メソッド</span><span class="sxs-lookup"><span data-stu-id="3cb95-121">VirtualFree Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|<span data-ttu-id="3cb95-122">解放、デコミット、または解放され、呼び出し元のプロセス仮想アドレス空間内のページの領域をデコミット、対応する Win32 関数の論理ラッパーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="3cb95-122">Serves as a logical wrapper for the corresponding Win32 function, which releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="3cb95-123">VirtualProtect メソッド</span><span class="sxs-lookup"><span data-stu-id="3cb95-123">VirtualProtect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|<span data-ttu-id="3cb95-124">対応する Win32 関数では、呼び出し元プロセスの仮想アドレス空間でコミットされたページの領域に保護を変更する論理ラッパーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="3cb95-124">Serves as a logical wrapper for the corresponding Win32 function, which changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="3cb95-125">VirtualQuery メソッド</span><span class="sxs-lookup"><span data-stu-id="3cb95-125">VirtualQuery Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|<span data-ttu-id="3cb95-126">対応する Win32 関数では、呼び出し元プロセスの仮想アドレス空間内のページの範囲に関する情報を取得する論理ラッパーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="3cb95-126">Serves as a logical wrapper for the corresponding Win32 function, which retrieves information about a range of pages in the virtual address space of the calling process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3cb95-127">コメント</span><span class="sxs-lookup"><span data-stu-id="3cb95-127">Remarks</span></span>  
 <span data-ttu-id="3cb95-128">`IHostMemoryManager`また、CLR ホストによって報告された、ヒープのメモリ要求を行うと、プロセスでは、メモリ不足のレベルを取得するためのポインターを取得するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="3cb95-128">`IHostMemoryManager` also provides methods for the CLR to obtain a pointer through which to make memory requests on the heap and to get the level of memory pressure in the process, as reported by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cb95-129">必要条件</span><span class="sxs-lookup"><span data-stu-id="3cb95-129">Requirements</span></span>  
 <span data-ttu-id="3cb95-130">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3cb95-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cb95-131">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3cb95-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3cb95-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="3cb95-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3cb95-133">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cb95-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cb95-134">参照</span><span class="sxs-lookup"><span data-stu-id="3cb95-134">See Also</span></span>  
 [<span data-ttu-id="3cb95-135">IHostMalloc インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3cb95-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 [<span data-ttu-id="3cb95-136">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3cb95-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
