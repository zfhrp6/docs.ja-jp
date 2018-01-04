---
title: "COR_GC_STATS 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_GC_STATS
api_location: mscoree.dll
api_type: COM
f1_keywords: COR_GC_STATS
helpviewer_keywords: COR_GC_STATS structure [.NET Framework hosting]
ms.assetid: 8d4ff73e-739b-40f6-9349-359fbc99c2f9
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 02a775be4976760b354a492e7252a67ef04eace9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="corgcstats-structure"></a><span data-ttu-id="1ec31-102">COR_GC_STATS 構造体</span><span class="sxs-lookup"><span data-stu-id="1ec31-102">COR_GC_STATS Structure</span></span>
<span data-ttu-id="1ec31-103">共通言語ランタイム (CLR) のガベージ コレクションのメカニズムについての統計情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="1ec31-103">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ec31-104">構文</span><span class="sxs-lookup"><span data-stu-id="1ec31-104">Syntax</span></span>  
  
```  
typedef struct _COR_GC_STATS {  
    ULONG   Flags;   
    SIZE_T  ExplicitGCCount;  
    SIZE_T  GenCollectionsTaken[3];  
    SIZE_T  CommittedKBytes;   
    SIZE_T  ReservedKBytes;  
    SIZE_T  Gen0HeapSizeKBytes;  
    SIZE_T  Gen1HeapSizeKBytes;  
    SIZE_T  Gen2HeapSizeKBytes;  
    SIZE_T  LargeObjectHeapSizeKBytes;  
    SIZE_T  KBytesPromotedFromGen0;  
    SIZE_T  KBytesPromotedFromGen1;  
} COR_GC_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="1ec31-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="1ec31-105">Members</span></span>  
  
|<span data-ttu-id="1ec31-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="1ec31-106">Member</span></span>|<span data-ttu-id="1ec31-107">説明</span><span class="sxs-lookup"><span data-stu-id="1ec31-107">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="1ec31-108">フィールドの値を計算して、返される必要がありますを示します。</span><span class="sxs-lookup"><span data-stu-id="1ec31-108">Indicates which field values should be calculated and returned.</span></span>|  
|`ExplicitGCCount`|<span data-ttu-id="1ec31-109">外部の要求によって強制的に実行されたガベージ コレクションの数を示します。</span><span class="sxs-lookup"><span data-stu-id="1ec31-109">Indicates the number of garbage collections that were forced by external request.</span></span>|  
|`GenCollectionsTaken`|<span data-ttu-id="1ec31-110">実行の各ジェネレーションのガベージ コレクションの数を示します。</span><span class="sxs-lookup"><span data-stu-id="1ec31-110">Indicates the number of garbage collections performed for each generation.</span></span>|  
|`CommittedKBytes`|<span data-ttu-id="1ec31-111">すべてのヒープでコミットされたキロバイト単位の合計数。</span><span class="sxs-lookup"><span data-stu-id="1ec31-111">The total number of kilobytes committed in all heaps.</span></span>|  
|`ReservedKBytes`|<span data-ttu-id="1ec31-112">すべてのヒープ内で予約されたキロバイト単位の合計数。</span><span class="sxs-lookup"><span data-stu-id="1ec31-112">The total number of kilobytes reserved in all heaps.</span></span>|  
|`Gen0HeapSizeKBytes`|<span data-ttu-id="1ec31-113">ジェネレーション 0 ヒープのサイズ。</span><span class="sxs-lookup"><span data-stu-id="1ec31-113">The size, in kilobytes, of the generation-zero heap.</span></span>|  
|`Gen1HeapSizeKBytes`|<span data-ttu-id="1ec31-114">ジェネレーション 1 ヒープのサイズ。</span><span class="sxs-lookup"><span data-stu-id="1ec31-114">The size, in kilobytes, of the generation-one heap.</span></span>|  
|`Gen2HeapSizeKBytes`|<span data-ttu-id="1ec31-115">ジェネレーション 2 のヒープのサイズ。</span><span class="sxs-lookup"><span data-stu-id="1ec31-115">The size, in kilobytes, of the generation-two heap.</span></span>|  
|`LargeObjectHeapSizeKBytes`|<span data-ttu-id="1ec31-116">大きなオブジェクト ヒープのサイズ。</span><span class="sxs-lookup"><span data-stu-id="1ec31-116">The size, in kilobytes, of the large object heap.</span></span>|  
|`KBytesPromotedFromGen0`|<span data-ttu-id="1ec31-117">ジェネレーション 0 からジェネレーション 1 に昇格オブジェクトのサイズ。</span><span class="sxs-lookup"><span data-stu-id="1ec31-117">The size, in kilobytes, of the objects promoted from generation zero to generation one.</span></span>|  
|`KBytesPromotedFromGen1`|<span data-ttu-id="1ec31-118">ジェネレーション 1 からジェネレーション 2 に昇格オブジェクトのサイズ。</span><span class="sxs-lookup"><span data-stu-id="1ec31-118">The size, in kilobytes, of the objects promoted from generation one to generation two.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ec31-119">コメント</span><span class="sxs-lookup"><span data-stu-id="1ec31-119">Remarks</span></span>  
 <span data-ttu-id="1ec31-120">[Iclrgcmanager::getstats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)メソッドが必要な`Flags`のフィールド、`COR_GC_STATS`の 1 つまたは複数の値に設定する構造体、 [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)を指定する列挙体統計情報では、設定します。</span><span class="sxs-lookup"><span data-stu-id="1ec31-120">The [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method requires the `Flags` field of the `COR_GC_STATS` structure to be set to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics are to be set.</span></span>  
  
 <span data-ttu-id="1ec31-121">次の表は、2 つに、この構造体で提供される統計[COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)列挙値、`COR_GC_COUNTS`と`COR_GC_MEMORYUSAGE`です。</span><span class="sxs-lookup"><span data-stu-id="1ec31-121">The following table maps the statistics provided by this structure to the two [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration values, `COR_GC_COUNTS` and `COR_GC_MEMORYUSAGE`.</span></span>  
  
|<span data-ttu-id="1ec31-122">COR_GC_COUNTS で指定されました。</span><span class="sxs-lookup"><span data-stu-id="1ec31-122">Specified by COR_GC_COUNTS</span></span>|<span data-ttu-id="1ec31-123">COR_GC_MEMORYUSAGE で指定されました。</span><span class="sxs-lookup"><span data-stu-id="1ec31-123">Specified by COR_GC_MEMORYUSAGE</span></span>|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 <span data-ttu-id="1ec31-124">使用状況の例は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1ec31-124">An example of the usage is as follows:</span></span>  
  
```  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="1ec31-125">必要条件</span><span class="sxs-lookup"><span data-stu-id="1ec31-125">Requirements</span></span>  
 <span data-ttu-id="1ec31-126">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1ec31-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ec31-127">**ヘッダー:** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="1ec31-127">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="1ec31-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="1ec31-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1ec31-129">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ec31-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ec31-130">参照</span><span class="sxs-lookup"><span data-stu-id="1ec31-130">See Also</span></span>  
 [<span data-ttu-id="1ec31-131">ホスト構造体</span><span class="sxs-lookup"><span data-stu-id="1ec31-131">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="1ec31-132">自動メモリ管理</span><span class="sxs-lookup"><span data-stu-id="1ec31-132">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="1ec31-133">ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="1ec31-133">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
