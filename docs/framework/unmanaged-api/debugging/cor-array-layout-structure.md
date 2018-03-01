---
title: "COR_ARRAY_LAYOUT 構造体"
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
- COR_ARRAY_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ARRAY_LAYOUT
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: aa20ac3d-6f60-4aa2-91c5-f3a86f82eba8
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b936b1b2187ec68db7f5fdecb0344e6cac211ab1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="corarraylayout-structure"></a><span data-ttu-id="9ca15-102">COR_ARRAY_LAYOUT 構造体</span><span class="sxs-lookup"><span data-stu-id="9ca15-102">COR_ARRAY_LAYOUT Structure</span></span>
<span data-ttu-id="9ca15-103">メモリ内の配列オブジェクトのレイアウトに関する情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="9ca15-103">Provides information about the layout of an array object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ca15-104">構文</span><span class="sxs-lookup"><span data-stu-id="9ca15-104">Syntax</span></span>  
  
```  
typedef struct COR_ARRAY_LAYOUT {  
    COR_TYPEID componentID;  
    CorElementType componentType;  
    ULONG32 firstElementOffset;  
    ULONG32 elementSize;  
    ULONG32 countOffset;   
    ULONG32 rankSize;   
    ULONG32 numRanks;   
    ULONG32 rankOffset;   
} COR_ARRAY_LAYOUT;  
```  
  
## <a name="members"></a><span data-ttu-id="9ca15-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="9ca15-105">Members</span></span>  
  
|<span data-ttu-id="9ca15-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="9ca15-106">Member</span></span>|<span data-ttu-id="9ca15-107">説明</span><span class="sxs-lookup"><span data-stu-id="9ca15-107">Description</span></span>|  
|------------|-----------------|  
|`componentID`|<span data-ttu-id="9ca15-108">配列が含まれているオブジェクトの種類の識別子。</span><span class="sxs-lookup"><span data-stu-id="9ca15-108">The identifier of the type of objects that the array contains.</span></span>|  
|`componentType`|<span data-ttu-id="9ca15-109">コンポーネントがガベージ コレクションの参照、値クラス、またはプリミティブであるかどうかを示す CorElementType 列挙型値。</span><span class="sxs-lookup"><span data-stu-id="9ca15-109">A CorElementType enumeration value that indicates whether the component is a garbage collection reference, a value class, or a primitive.</span></span>|  
|`firstElementOffset`|<span data-ttu-id="9ca15-110">配列の最初の要素のオフセット。</span><span class="sxs-lookup"><span data-stu-id="9ca15-110">The offset to the first element in the array.</span></span>|  
|`elementSize`|<span data-ttu-id="9ca15-111">各要素のサイズ。</span><span class="sxs-lookup"><span data-stu-id="9ca15-111">The size of each element.</span></span>|  
|`countOffset`|<span data-ttu-id="9ca15-112">配列内の要素の数をオフセットします。</span><span class="sxs-lookup"><span data-stu-id="9ca15-112">The offset to the number of elements in the array.</span></span>|  
|`rankSize`|<span data-ttu-id="9ca15-113">(バイト単位)、ランクのサイズ。</span><span class="sxs-lookup"><span data-stu-id="9ca15-113">The size of the rank, in bytes.</span></span>|  
|`numRanks`|<span data-ttu-id="9ca15-114">配列のランクの数。</span><span class="sxs-lookup"><span data-stu-id="9ca15-114">The number of ranks in the array.</span></span>|  
|`rankOffset`|<span data-ttu-id="9ca15-115">ランクを開始するオフセットです。</span><span class="sxs-lookup"><span data-stu-id="9ca15-115">The offset at which the ranks start.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ca15-116">コメント</span><span class="sxs-lookup"><span data-stu-id="9ca15-116">Remarks</span></span>  
 <span data-ttu-id="9ca15-117">`rankSize`フィールドは、多次元配列のランクのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="9ca15-117">The `rankSize` field specifies the size of a rank in a multi-dimensional array.</span></span> <span data-ttu-id="9ca15-118">これは、1 次元の配列も正確です。</span><span class="sxs-lookup"><span data-stu-id="9ca15-118">It is accurate for single-dimensional arrays as well.</span></span>  
  
 <span data-ttu-id="9ca15-119">値`numRanks`は 1 次元配列の場合は 1 と`N`の多次元配列を`N`ディメンションです。</span><span class="sxs-lookup"><span data-stu-id="9ca15-119">The value of `numRanks` is 1 for a single-dimensional array and `N` for a multi-dimensional array of `N` dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ca15-120">必要条件</span><span class="sxs-lookup"><span data-stu-id="9ca15-120">Requirements</span></span>  
 <span data-ttu-id="9ca15-121">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9ca15-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ca15-122">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ca15-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ca15-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ca15-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ca15-124">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ca15-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ca15-125">参照</span><span class="sxs-lookup"><span data-stu-id="9ca15-125">See Also</span></span>  
 [<span data-ttu-id="9ca15-126">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="9ca15-126">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="9ca15-127">デバッグ</span><span class="sxs-lookup"><span data-stu-id="9ca15-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
