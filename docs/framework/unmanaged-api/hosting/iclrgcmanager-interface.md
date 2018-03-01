---
title: "ICLRGCManager インターフェイス"
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
- ICLRGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager
helpviewer_keywords:
- ICLRGCManager interface [.NET Framework hosting]
ms.assetid: fb511c9b-3fe4-41b0-822a-6ba4a079d1f5
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6cc6c84d57e4114a28a8b363b99b98f3c4d21410
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrgcmanager-interface"></a><span data-ttu-id="b25ae-102">ICLRGCManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b25ae-102">ICLRGCManager Interface</span></span>
<span data-ttu-id="b25ae-103">ホストが共通言語ランタイムのガベージ コレクション システムとやり取りできるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="b25ae-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b25ae-104">以降で、 [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]、使用することができます、 [iclrgcmanager 2::setgcstartuplimitsex](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)ガベージ コレクション セグメントのサイズおよび最大サイズ、ガベージ コレクション システムのジェネレーション 0 の値に設定する大きいメソッド`DWORD`によって課される制限、 [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="b25ae-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can use the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b25ae-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="b25ae-105">Methods</span></span>  
  
|<span data-ttu-id="b25ae-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="b25ae-106">Method</span></span>|<span data-ttu-id="b25ae-107">説明</span><span class="sxs-lookup"><span data-stu-id="b25ae-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b25ae-108">Collect メソッド</span><span class="sxs-lookup"><span data-stu-id="b25ae-108">Collect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-collect-method.md)|<span data-ttu-id="b25ae-109">指定したジェネレーションのガベージ コレクションを強制的にします。</span><span class="sxs-lookup"><span data-stu-id="b25ae-109">Forces a garbage collection for the specified generation.</span></span>|  
|[<span data-ttu-id="b25ae-110">GetStats メソッド</span><span class="sxs-lookup"><span data-stu-id="b25ae-110">GetStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)|<span data-ttu-id="b25ae-111">ガベージ コレクション システムに関する現在の統計情報のセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="b25ae-111">Gets a set of current statistics about the garbage collection system.</span></span>|  
|[<span data-ttu-id="b25ae-112">SetGCStartupLimits メソッド</span><span class="sxs-lookup"><span data-stu-id="b25ae-112">SetGCStartupLimits Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)|<span data-ttu-id="b25ae-113">ガベージ コレクション セグメントのサイズと、ガベージ コレクション システムのジェネレーション 0 の最大サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="b25ae-113">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b25ae-114">コメント</span><span class="sxs-lookup"><span data-stu-id="b25ae-114">Remarks</span></span>  
 <span data-ttu-id="b25ae-115">共通言語ランタイム (CLR) が、管理されていると、ガベージ コレクションのメカニズムを実装する<xref:System.GC>型です。</span><span class="sxs-lookup"><span data-stu-id="b25ae-115">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="b25ae-116">ガベージ コレクション システムに関する詳細については、次を参照してください。[ガベージ コレクション](../../../../docs/standard/garbage-collection/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="b25ae-116">For more information about the garbage collection system, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b25ae-117">必要条件</span><span class="sxs-lookup"><span data-stu-id="b25ae-117">Requirements</span></span>  
 <span data-ttu-id="b25ae-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b25ae-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b25ae-119">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b25ae-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b25ae-120">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="b25ae-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b25ae-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b25ae-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b25ae-122">参照</span><span class="sxs-lookup"><span data-stu-id="b25ae-122">See Also</span></span>  
 [<span data-ttu-id="b25ae-123">自動メモリ管理</span><span class="sxs-lookup"><span data-stu-id="b25ae-123">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="b25ae-124">COR_GC_STATS 構造体</span><span class="sxs-lookup"><span data-stu-id="b25ae-124">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [<span data-ttu-id="b25ae-125">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b25ae-125">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="b25ae-126">CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b25ae-126">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [<span data-ttu-id="b25ae-127">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b25ae-127">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="b25ae-128">ホスティング</span><span class="sxs-lookup"><span data-stu-id="b25ae-128">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
