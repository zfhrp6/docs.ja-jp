---
title: "COR_GC_STAT_TYPES 列挙体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_GC_STAT_TYPES
api_location: mscoree.dll
api_type: COM
f1_keywords: COR_GC_STAT_TYPES
helpviewer_keywords: COR_GC_STAT_TYPES enumeration [.NET Framework hosting]
ms.assetid: fc51d6db-f7f8-408b-b93d-c166fc712c99
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 86d0ce931518fa50dbd3b0d6d7f2755d19042eca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="corgcstattypes-enumeration"></a><span data-ttu-id="1ac25-102">COR_GC_STAT_TYPES 列挙体</span><span class="sxs-lookup"><span data-stu-id="1ac25-102">COR_GC_STAT_TYPES Enumeration</span></span>
<span data-ttu-id="1ac25-103">ガベージ コレクションについて記録する統計情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="1ac25-103">Specifies the statistics to be recorded for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ac25-104">構文</span><span class="sxs-lookup"><span data-stu-id="1ac25-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a><span data-ttu-id="1ac25-105">コメント</span><span class="sxs-lookup"><span data-stu-id="1ac25-105">Remarks</span></span>  
 <span data-ttu-id="1ac25-106">この列挙体の統計情報の指定、 [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)構造体は設定[iclrgcmanager::getstats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="1ac25-106">This enumeration specifies which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set by [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method.</span></span>  
  
## <a name="members"></a><span data-ttu-id="1ac25-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="1ac25-107">Members</span></span>  
  
|<span data-ttu-id="1ac25-108">メンバー</span><span class="sxs-lookup"><span data-stu-id="1ac25-108">Member</span></span>|<span data-ttu-id="1ac25-109">説明</span><span class="sxs-lookup"><span data-stu-id="1ac25-109">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_COUNTS`|<span data-ttu-id="1ac25-110">レコードの各ジェネレーションのガベージ コレクションの数が実行されます。</span><span class="sxs-lookup"><span data-stu-id="1ac25-110">Records the number of garbage collections performed for each generation.</span></span>|  
|`COR_GC_MEMORYUSAGE`|<span data-ttu-id="1ac25-111">レコード メモリ使用とガベージ コレクションのサイズの統計情報。</span><span class="sxs-lookup"><span data-stu-id="1ac25-111">Records memory usage and garbage collection size statistics.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1ac25-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="1ac25-112">Requirements</span></span>  
 <span data-ttu-id="1ac25-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1ac25-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ac25-114">**ヘッダー:** GCHost.idl、GCHost.h</span><span class="sxs-lookup"><span data-stu-id="1ac25-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="1ac25-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ac25-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ac25-116">参照</span><span class="sxs-lookup"><span data-stu-id="1ac25-116">See Also</span></span>  
 [<span data-ttu-id="1ac25-117">COR_GC_STATS 構造体</span><span class="sxs-lookup"><span data-stu-id="1ac25-117">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [<span data-ttu-id="1ac25-118">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="1ac25-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
