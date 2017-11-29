---
title: "ICLRGCManager インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRGCManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRGCManager
helpviewer_keywords: ICLRGCManager interface [.NET Framework hosting]
ms.assetid: fb511c9b-3fe4-41b0-822a-6ba4a079d1f5
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7215ce1423e8541b23daae7b9e051ade6e25f1b7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrgcmanager-interface"></a><span data-ttu-id="a0d3c-102">ICLRGCManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a0d3c-102">ICLRGCManager Interface</span></span>
<span data-ttu-id="a0d3c-103">ホストが共通言語ランタイムのガベージ コレクション システムとやり取りできるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a0d3c-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0d3c-104">以降で、 [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]、使用することができます、 [iclrgcmanager 2::setgcstartuplimitsex](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)ガベージ コレクション セグメントのサイズおよび最大サイズ、ガベージ コレクション システムのジェネレーション 0 の値に設定する大きいメソッド`DWORD`によって課される制限、 [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="a0d3c-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can use the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a0d3c-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a0d3c-105">Methods</span></span>  
  
|<span data-ttu-id="a0d3c-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="a0d3c-106">Method</span></span>|<span data-ttu-id="a0d3c-107">説明</span><span class="sxs-lookup"><span data-stu-id="a0d3c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a0d3c-108">Collect メソッド</span><span class="sxs-lookup"><span data-stu-id="a0d3c-108">Collect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-collect-method.md)|<span data-ttu-id="a0d3c-109">指定したジェネレーションのガベージ コレクションを強制的にします。</span><span class="sxs-lookup"><span data-stu-id="a0d3c-109">Forces a garbage collection for the specified generation.</span></span>|  
|[<span data-ttu-id="a0d3c-110">GetStats メソッド</span><span class="sxs-lookup"><span data-stu-id="a0d3c-110">GetStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)|<span data-ttu-id="a0d3c-111">ガベージ コレクション システムに関する現在の統計情報のセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="a0d3c-111">Gets a set of current statistics about the garbage collection system.</span></span>|  
|[<span data-ttu-id="a0d3c-112">SetGCStartupLimits メソッド</span><span class="sxs-lookup"><span data-stu-id="a0d3c-112">SetGCStartupLimits Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)|<span data-ttu-id="a0d3c-113">ガベージ コレクション セグメントのサイズと、ガベージ コレクション システムのジェネレーション 0 の最大サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="a0d3c-113">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0d3c-114">コメント</span><span class="sxs-lookup"><span data-stu-id="a0d3c-114">Remarks</span></span>  
 <span data-ttu-id="a0d3c-115">共通言語ランタイム (CLR) が、管理されていると、ガベージ コレクションのメカニズムを実装する<xref:System.GC>型です。</span><span class="sxs-lookup"><span data-stu-id="a0d3c-115">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="a0d3c-116">ガベージ コレクション システムに関する詳細については、次を参照してください。[ガベージ コレクション](../../../../docs/standard/garbage-collection/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="a0d3c-116">For more information about the garbage collection system, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0d3c-117">要件</span><span class="sxs-lookup"><span data-stu-id="a0d3c-117">Requirements</span></span>  
 <span data-ttu-id="a0d3c-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a0d3c-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0d3c-119">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a0d3c-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a0d3c-120">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="a0d3c-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a0d3c-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0d3c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0d3c-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0d3c-122">See Also</span></span>  
 [<span data-ttu-id="a0d3c-123">自動メモリ管理</span><span class="sxs-lookup"><span data-stu-id="a0d3c-123">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="a0d3c-124">COR_GC_STATS 構造体</span><span class="sxs-lookup"><span data-stu-id="a0d3c-124">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [<span data-ttu-id="a0d3c-125">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a0d3c-125">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="a0d3c-126">CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a0d3c-126">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [<span data-ttu-id="a0d3c-127">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a0d3c-127">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="a0d3c-128">ホスティング</span><span class="sxs-lookup"><span data-stu-id="a0d3c-128">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
