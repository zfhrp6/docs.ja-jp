---
title: "IGCHost インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHost
api_location: mscoree.dll
api_type: COM
f1_keywords: IGCHost
helpviewer_keywords: IGCHost interface [.NET Framework hosting]
ms.assetid: 9ad70ffd-6963-4ab2-8c84-3d86c3fb8deb
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5c0f398c09569a855291a1565ce63b513161a803
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="igchost-interface"></a><span data-ttu-id="1a626-102">IGCHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1a626-102">IGCHost Interface</span></span>
<span data-ttu-id="1a626-103">ガベージ コレクション システムに関する情報を取得して、ガベージ コレクションの一部の側面を制御するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="1a626-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1a626-104">以降で、 [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]、使用することができます、 [igchost 2::setgcstartuplimitsex](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)ガベージ コレクション セグメントのサイズと、ガベージ コレクション システムのジェネレーション 0 の最大サイズの値より大きいに設定する方法、`DWORD`によって課される制限、 [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="1a626-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can use the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1a626-105">インターフェイスは上級者のみです。</span><span class="sxs-lookup"><span data-stu-id="1a626-105">This interface is for expert usage only.</span></span> <span data-ttu-id="1a626-106">不適切に使用する場合に、アプリケーションのパフォーマンスに影響ことができます。</span><span class="sxs-lookup"><span data-stu-id="1a626-106">It can affect the performance of an application if used improperly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1a626-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="1a626-107">Methods</span></span>  
  
|<span data-ttu-id="1a626-108">メソッド</span><span class="sxs-lookup"><span data-stu-id="1a626-108">Method</span></span>|<span data-ttu-id="1a626-109">説明</span><span class="sxs-lookup"><span data-stu-id="1a626-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1a626-110">Collect メソッド</span><span class="sxs-lookup"><span data-stu-id="1a626-110">Collect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-collect-method.md)|<span data-ttu-id="1a626-111">現在のガベージ コレクションの状態に関係なく、特定のジェネレーションで発生するコレクションを強制的にします。</span><span class="sxs-lookup"><span data-stu-id="1a626-111">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>|  
|[<span data-ttu-id="1a626-112">GetStats メソッド</span><span class="sxs-lookup"><span data-stu-id="1a626-112">GetStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-getstats-method.md)|<span data-ttu-id="1a626-113">ガベージ コレクション システムの現在の状態の統計情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="1a626-113">Gets the statistics for the current state of the garbage collection system.</span></span>|  
|[<span data-ttu-id="1a626-114">GetThreadStats メソッド</span><span class="sxs-lookup"><span data-stu-id="1a626-114">GetThreadStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-getthreadstats-method.md)|<span data-ttu-id="1a626-115">ガベージ コレクションのスレッドあたりの統計情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="1a626-115">Gets the per-thread statistics for garbage collection.</span></span>|  
|[<span data-ttu-id="1a626-116">SetGCStartupLimits メソッド</span><span class="sxs-lookup"><span data-stu-id="1a626-116">SetGCStartupLimits Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)|<span data-ttu-id="1a626-117">ジェネレーション 0 のセグメントのサイズと最大サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="1a626-117">Sets the segment size and the maximum size for generation 0.</span></span>|  
|[<span data-ttu-id="1a626-118">SetVirtualMemLimit メソッド</span><span class="sxs-lookup"><span data-stu-id="1a626-118">SetVirtualMemLimit Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-setvirtualmemlimit-method.md)|<span data-ttu-id="1a626-119">ランタイムの仮想メモリの最大サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="1a626-119">Sets the maximum size of the runtime's virtual memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1a626-120">要件</span><span class="sxs-lookup"><span data-stu-id="1a626-120">Requirements</span></span>  
 <span data-ttu-id="1a626-121">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1a626-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a626-122">**ヘッダー:** GCHost.idl、GCHost.h</span><span class="sxs-lookup"><span data-stu-id="1a626-122">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="1a626-123">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="1a626-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1a626-124">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a626-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a626-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="1a626-125">See Also</span></span>  
 [<span data-ttu-id="1a626-126">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1a626-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="1a626-127">CorRuntimeHost コクラス</span><span class="sxs-lookup"><span data-stu-id="1a626-127">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
