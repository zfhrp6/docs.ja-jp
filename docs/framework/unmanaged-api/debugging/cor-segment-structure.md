---
title: COR_SEGMENT 構造体
ms.date: 03/30/2017
api_name:
- COR_SEGMENT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_SEGMENT
helpviewer_keywords:
- COR_SEGMENT structure [.NET Framework debugging]
ms.assetid: 93aeecb9-7fef-4545-8daf-f566dfc47084
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b816087f54e652f07dc791b7d66eb1af8f52f55e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406508"
---
# <a name="corsegment-structure"></a><span data-ttu-id="7dad6-102">COR_SEGMENT 構造体</span><span class="sxs-lookup"><span data-stu-id="7dad6-102">COR_SEGMENT Structure</span></span>
<span data-ttu-id="7dad6-103">マネージ ヒープのメモリ領域に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="7dad6-103">Contains information about a region of memory in the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dad6-104">構文</span><span class="sxs-lookup"><span data-stu-id="7dad6-104">Syntax</span></span>  
  
```  
typedef struct _COR_SEGMENT {  
    CORDB_ADDRESS start;            
    CORDB_ADDRESS end;              
    CorDebugGenerationTypes gen;    
    ULONG heap;                     
} COR_SEGMENT;  
```  
  
## <a name="members"></a><span data-ttu-id="7dad6-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="7dad6-105">Members</span></span>  
  
|<span data-ttu-id="7dad6-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="7dad6-106">Member</span></span>|<span data-ttu-id="7dad6-107">説明</span><span class="sxs-lookup"><span data-stu-id="7dad6-107">Description</span></span>|  
|------------|-----------------|  
|`start`|<span data-ttu-id="7dad6-108">メモリ領域の開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="7dad6-108">The starting address of the memory region.</span></span>|  
|`end`|<span data-ttu-id="7dad6-109">メモリ領域の終了アドレス。</span><span class="sxs-lookup"><span data-stu-id="7dad6-109">The ending address of the memory region.</span></span>|  
|`gen`|<span data-ttu-id="7dad6-110">A [CorDebugGenerationTypes](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md)メモリ領域の生成を示す列挙メンバー。</span><span class="sxs-lookup"><span data-stu-id="7dad6-110">A [CorDebugGenerationTypes](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md) enumeration member that indicates the generation of the memory region.</span></span>|  
|`heap`|<span data-ttu-id="7dad6-111">メモリ領域が存在するヒープ数です。</span><span class="sxs-lookup"><span data-stu-id="7dad6-111">The heap number in which the memory region resides.</span></span> <span data-ttu-id="7dad6-112">詳細については、次の「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7dad6-112">See the Remarks section for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7dad6-113">コメント</span><span class="sxs-lookup"><span data-stu-id="7dad6-113">Remarks</span></span>  
 <span data-ttu-id="7dad6-114">`COR_SEGMENTS`構造体がマネージ ヒープのメモリ領域を表します。</span><span class="sxs-lookup"><span data-stu-id="7dad6-114">The `COR_SEGMENTS` structure represents a region of memory in the managed heap.</span></span>  <span data-ttu-id="7dad6-115">`COR_SEGMENTS` オブジェクトのメンバーである、 [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)が呼び出すことによって設定されているコレクション オブジェクト、[icordebugprocess 5::enumerateheapregions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="7dad6-115">`COR_SEGMENTS` objects are members of the [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) collection object, which is populated by calling the[ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) method.</span></span>  
  
 <span data-ttu-id="7dad6-116">`heap`フィールドは、プロセッサ番号、報告されているヒープに対応しています。</span><span class="sxs-lookup"><span data-stu-id="7dad6-116">The `heap` field is the processor number, which corresponds to the heap being reported.</span></span> <span data-ttu-id="7dad6-117">ワークステーション ガベージ コレクターでは、その値は常に 0、ワークステーション ガベージ コレクション ヒープの 1 つだけがあるためです。</span><span class="sxs-lookup"><span data-stu-id="7dad6-117">For workstation garbage collectors, its value is always zero, because workstations have only one garbage collection heap.</span></span> <span data-ttu-id="7dad6-118">サーバー ガベージ コレクターでは、その値は、ヒープに接続されているプロセッサに対応します。</span><span class="sxs-lookup"><span data-stu-id="7dad6-118">For server garbage collectors, its value corresponds to the processor the heap is attached to.</span></span> <span data-ttu-id="7dad6-119">ありますまたはより少ないガベージ コレクション ヒープがよりも多いため、ガベージ コレクターの実装の詳細の実際のプロセッサに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7dad6-119">Note that there may be more or fewer garbage collection heaps than there are actual processors due to the implementation details of the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7dad6-120">要件</span><span class="sxs-lookup"><span data-stu-id="7dad6-120">Requirements</span></span>  
 <span data-ttu-id="7dad6-121">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7dad6-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7dad6-122">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7dad6-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7dad6-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7dad6-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7dad6-124">**.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7dad6-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dad6-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="7dad6-125">See Also</span></span>  
 [<span data-ttu-id="7dad6-126">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="7dad6-126">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="7dad6-127">デバッグ</span><span class="sxs-lookup"><span data-stu-id="7dad6-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
