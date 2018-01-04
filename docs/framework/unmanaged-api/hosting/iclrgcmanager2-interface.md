---
title: "ICLRGCManager2 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRGCManager2
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRGCManager2
helpviewer_keywords: ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 4b5ffd7b-9ad7-41cd-9bba-34030ae3da7e
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4a8b51cf4297c1ccadbef8730c06148263d310e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrgcmanager2-interface"></a><span data-ttu-id="9ca88-102">ICLRGCManager2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9ca88-102">ICLRGCManager2 Interface</span></span>
<span data-ttu-id="9ca88-103">ホストが共通言語ランタイムのガベージ コレクション システムとやり取りできるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="9ca88-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9ca88-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="9ca88-104">Methods</span></span>  
  
|<span data-ttu-id="9ca88-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="9ca88-105">Method</span></span>|<span data-ttu-id="9ca88-106">説明</span><span class="sxs-lookup"><span data-stu-id="9ca88-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9ca88-107">SetGCStartupLimitsEx メソッド</span><span class="sxs-lookup"><span data-stu-id="9ca88-107">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)|<span data-ttu-id="9ca88-108">ガベージ コレクション セグメントのサイズと、ガベージ コレクション システムのジェネレーション 0 の最大サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="9ca88-108">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span> <span data-ttu-id="9ca88-109">により、ジェネレーション 0 とセグメントのサイズよりも大きい`DWORD`です。</span><span class="sxs-lookup"><span data-stu-id="9ca88-109">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ca88-110">コメント</span><span class="sxs-lookup"><span data-stu-id="9ca88-110">Remarks</span></span>  
 <span data-ttu-id="9ca88-111">このインターフェイスから継承、 [ICLRGCManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="9ca88-111">This interface inherits from the [ICLRGCManager Interface](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
 <span data-ttu-id="9ca88-112">共通言語ランタイム (CLR) が、管理されていると、ガベージ コレクションのメカニズムを実装する<xref:System.GC>型です。</span><span class="sxs-lookup"><span data-stu-id="9ca88-112">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="9ca88-113">ガベージ コレクション システムに関する詳細については、次を参照してください。[ガベージ コレクション](../../../../docs/standard/garbage-collection/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="9ca88-113">For more information about the garbage collection system, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ca88-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="9ca88-114">Requirements</span></span>  
 <span data-ttu-id="9ca88-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9ca88-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ca88-116">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9ca88-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9ca88-117">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="9ca88-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ca88-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ca88-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ca88-119">参照</span><span class="sxs-lookup"><span data-stu-id="9ca88-119">See Also</span></span>  
 [<span data-ttu-id="9ca88-120">自動メモリ管理</span><span class="sxs-lookup"><span data-stu-id="9ca88-120">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="9ca88-121">COR_GC_STATS 構造体</span><span class="sxs-lookup"><span data-stu-id="9ca88-121">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [<span data-ttu-id="9ca88-122">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9ca88-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="9ca88-123">.NET Framework 4 および 4.5 で追加された CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9ca88-123">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 [<span data-ttu-id="9ca88-124">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9ca88-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="9ca88-125">ホスティング</span><span class="sxs-lookup"><span data-stu-id="9ca88-125">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
