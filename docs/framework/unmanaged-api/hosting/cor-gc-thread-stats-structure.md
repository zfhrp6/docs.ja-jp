---
title: "COR_GC_THREAD_STATS 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_GC_THREAD_STATS
api_location: mscoree.dll
api_type: COM
f1_keywords: COR_GC_THREAD_STATS
helpviewer_keywords: COR_GC_THREAD_STATS structure [.NET Framework hosting]
ms.assetid: 01f9a59b-7679-4d42-9ced-4a8981625c3d
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 266352984cf50dc906e77598e8dcc9216526ce17
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="corgcthreadstats-structure"></a><span data-ttu-id="0e8d5-102">COR_GC_THREAD_STATS 構造体</span><span class="sxs-lookup"><span data-stu-id="0e8d5-102">COR_GC_THREAD_STATS Structure</span></span>
<span data-ttu-id="0e8d5-103">ガベージ コレクションに関連するスレッドごとの統計情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0e8d5-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e8d5-104">構文</span><span class="sxs-lookup"><span data-stu-id="0e8d5-104">Syntax</span></span>  
  
```  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;   
    ULONG      Flags;   
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="0e8d5-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="0e8d5-105">Members</span></span>  
  
|<span data-ttu-id="0e8d5-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="0e8d5-106">Member</span></span>|<span data-ttu-id="0e8d5-107">説明</span><span class="sxs-lookup"><span data-stu-id="0e8d5-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="0e8d5-108">現在関連付けられているスレッドに割り当てられたメモリのバイト数`COR_GC_THREAD_STATS`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="0e8d5-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="0e8d5-109">この番号は、ジェネレーション 0 ガベージ コレクションが発生するたびに 0 にクリアされます。</span><span class="sxs-lookup"><span data-stu-id="0e8d5-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="0e8d5-110">バイト数では、最新のガベージ コレクションを上位のジェネレーションに昇格します。</span><span class="sxs-lookup"><span data-stu-id="0e8d5-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e8d5-111">コメント</span><span class="sxs-lookup"><span data-stu-id="0e8d5-111">Remarks</span></span>  
 <span data-ttu-id="0e8d5-112">[Iclrtask::getmemstats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md)型の出力パラメーターを取る`COR_GC_THREAD_STATS`です。</span><span class="sxs-lookup"><span data-stu-id="0e8d5-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e8d5-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="0e8d5-113">Requirements</span></span>  
 <span data-ttu-id="0e8d5-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0e8d5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e8d5-115">**ヘッダー:** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="0e8d5-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="0e8d5-116">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="0e8d5-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0e8d5-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e8d5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e8d5-118">参照</span><span class="sxs-lookup"><span data-stu-id="0e8d5-118">See Also</span></span>  
 [<span data-ttu-id="0e8d5-119">ホスト構造体</span><span class="sxs-lookup"><span data-stu-id="0e8d5-119">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="0e8d5-120">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0e8d5-120">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
