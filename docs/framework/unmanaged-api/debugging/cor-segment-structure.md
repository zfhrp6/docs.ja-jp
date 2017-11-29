---
title: "COR_SEGMENT 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_SEGMENT
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_SEGMENT
helpviewer_keywords: COR_SEGMENT structure [.NET Framework debugging]
ms.assetid: 93aeecb9-7fef-4545-8daf-f566dfc47084
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fc7a749f92149d7f0f5725aec6d90d72e0582c13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="corsegment-structure"></a><span data-ttu-id="1ba4d-102">COR_SEGMENT 構造体</span><span class="sxs-lookup"><span data-stu-id="1ba4d-102">COR_SEGMENT Structure</span></span>
<span data-ttu-id="1ba4d-103">マネージ ヒープのメモリ領域に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1ba4d-103">Contains information about a region of memory in the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ba4d-104">構文</span><span class="sxs-lookup"><span data-stu-id="1ba4d-104">Syntax</span></span>  
  
```  
typedef struct _COR_SEGMENT {  
    CORDB_ADDRESS start;            
    CORDB_ADDRESS end;              
    CorDebugGenerationTypes gen;    
    ULONG heap;                     
} COR_SEGMENT;  
```  
  
## <a name="members"></a><span data-ttu-id="1ba4d-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="1ba4d-105">Members</span></span>  
  
|<span data-ttu-id="1ba4d-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="1ba4d-106">Member</span></span>|<span data-ttu-id="1ba4d-107">説明</span><span class="sxs-lookup"><span data-stu-id="1ba4d-107">Description</span></span>|  
|------------|-----------------|  
|`start`|<span data-ttu-id="1ba4d-108">メモリ領域の開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="1ba4d-108">The starting address of the memory region.</span></span>|  
|`end`|<span data-ttu-id="1ba4d-109">メモリ領域の終了アドレス。</span><span class="sxs-lookup"><span data-stu-id="1ba4d-109">The ending address of the memory region.</span></span>|  
|`gen`|<span data-ttu-id="1ba4d-110">A [CorDebugGenerationTypes](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md)メモリ領域の生成を示す列挙メンバー。</span><span class="sxs-lookup"><span data-stu-id="1ba4d-110">A [CorDebugGenerationTypes](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md) enumeration member that indicates the generation of the memory region.</span></span>|  
|`heap`|<span data-ttu-id="1ba4d-111">メモリ領域が存在するヒープ数です。</span><span class="sxs-lookup"><span data-stu-id="1ba4d-111">The heap number in which the memory region resides.</span></span> <span data-ttu-id="1ba4d-112">詳細については、次の「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ba4d-112">See the Remarks section for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ba4d-113">コメント</span><span class="sxs-lookup"><span data-stu-id="1ba4d-113">Remarks</span></span>  
 <span data-ttu-id="1ba4d-114">`COR_SEGMENTS`構造体がマネージ ヒープのメモリ領域を表します。</span><span class="sxs-lookup"><span data-stu-id="1ba4d-114">The `COR_SEGMENTS` structure represents a region of memory in the managed heap.</span></span>  <span data-ttu-id="1ba4d-115">`COR_SEGMENTS`オブジェクトのメンバーである、 [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)が呼び出すことによって設定されているコレクション オブジェクト、[icordebugprocess 5::enumerateheapregions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="1ba4d-115">`COR_SEGMENTS` objects are members of the [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) collection object, which is populated by calling the[ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) method.</span></span>  
  
 <span data-ttu-id="1ba4d-116">`heap`フィールドは、プロセッサ番号、報告されているヒープに対応しています。</span><span class="sxs-lookup"><span data-stu-id="1ba4d-116">The `heap` field is the processor number, which corresponds to the heap being reported.</span></span> <span data-ttu-id="1ba4d-117">ワークステーション ガベージ コレクターでは、その値は常に 0、ワークステーション ガベージ コレクション ヒープの 1 つだけがあるためです。</span><span class="sxs-lookup"><span data-stu-id="1ba4d-117">For workstation garbage collectors, its value is always zero, because workstations have only one garbage collection heap.</span></span> <span data-ttu-id="1ba4d-118">サーバー ガベージ コレクターでは、その値は、ヒープに接続されているプロセッサに対応します。</span><span class="sxs-lookup"><span data-stu-id="1ba4d-118">For server garbage collectors, its value corresponds to the processor the heap is attached to.</span></span> <span data-ttu-id="1ba4d-119">ありますまたはより少ないガベージ コレクション ヒープがよりも多いため、ガベージ コレクターの実装の詳細の実際のプロセッサに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1ba4d-119">Note that there may be more or fewer garbage collection heaps than there are actual processors due to the implementation details of the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ba4d-120">要件</span><span class="sxs-lookup"><span data-stu-id="1ba4d-120">Requirements</span></span>  
 <span data-ttu-id="1ba4d-121">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1ba4d-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ba4d-122">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ba4d-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ba4d-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ba4d-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ba4d-124">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ba4d-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ba4d-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="1ba4d-125">See Also</span></span>  
 [<span data-ttu-id="1ba4d-126">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="1ba4d-126">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="1ba4d-127">デバッグ</span><span class="sxs-lookup"><span data-stu-id="1ba4d-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
