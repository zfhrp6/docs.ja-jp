---
title: COR_PRF_GC_GENERATION 列挙型
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_GENERATION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_GENERATION
helpviewer_keywords:
- COR_GC_GENERATION_FLAGS enumeration [.NET Framework profiling]
ms.assetid: d6ece160-26ad-4d39-abd7-05acd6f78c48
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8283139566050b1858a003316dc46581822a9bbb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450155"
---
# <a name="corprfgcgeneration-enumeration"></a><span data-ttu-id="1c631-102">COR_PRF_GC_GENERATION 列挙型</span><span class="sxs-lookup"><span data-stu-id="1c631-102">COR_PRF_GC_GENERATION Enumeration</span></span>
<span data-ttu-id="1c631-103">ガベージ コレクション ジェネレーションを識別します。</span><span class="sxs-lookup"><span data-stu-id="1c631-103">Identifies a garbage-collection generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c631-104">構文</span><span class="sxs-lookup"><span data-stu-id="1c631-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3  
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a><span data-ttu-id="1c631-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="1c631-105">Members</span></span>  
  
|<span data-ttu-id="1c631-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="1c631-106">Member</span></span>|<span data-ttu-id="1c631-107">説明</span><span class="sxs-lookup"><span data-stu-id="1c631-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|<span data-ttu-id="1c631-108">オブジェクトは、ジェネレーション 0 として格納されます。</span><span class="sxs-lookup"><span data-stu-id="1c631-108">The object is stored as generation 0.</span></span>|  
|`COR_PRF_GC_GEN_1`|<span data-ttu-id="1c631-109">オブジェクトは、第 1 世代として格納されます。</span><span class="sxs-lookup"><span data-stu-id="1c631-109">The object is stored as generation 1.</span></span>|  
|`COR_PRF_GC_GEN_2`|<span data-ttu-id="1c631-110">オブジェクトは、第 2 世代として格納されます。</span><span class="sxs-lookup"><span data-stu-id="1c631-110">The object is stored as generation 2.</span></span>|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|<span data-ttu-id="1c631-111">オブジェクトは、大きなオブジェクト ヒープに格納されます。</span><span class="sxs-lookup"><span data-stu-id="1c631-111">The object is stored in the large-object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c631-112">コメント</span><span class="sxs-lookup"><span data-stu-id="1c631-112">Remarks</span></span>  
 <span data-ttu-id="1c631-113">ガベージ コレクターには、年齢に基づいてジェネレーションに分割オブジェクトによってメモリ管理のパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="1c631-113">The garbage collector improves memory management performance by dividing objects into generations based on age.</span></span> <span data-ttu-id="1c631-114">現在、ガベージ コレクターは、0、1、2、およびラージ オブジェクトに使用される特殊なヒープ セグメントの番号、3 つの世代を使用します。</span><span class="sxs-lookup"><span data-stu-id="1c631-114">The garbage collector currently uses three generations, numbered 0, 1, and 2, plus a special heap segment that is used for large objects.</span></span> <span data-ttu-id="1c631-115">サイズが特定の値より大きいオブジェクトは、大きなオブジェクト ヒープに格納されます。</span><span class="sxs-lookup"><span data-stu-id="1c631-115">Objects whose size is larger than a particular value are stored in the large-object heap.</span></span> <span data-ttu-id="1c631-116">割り当てられたその他のオブジェクトは、ジェネレーション 0 に属しているを開始します。</span><span class="sxs-lookup"><span data-stu-id="1c631-116">Other allocated objects start out belonging to generation 0.</span></span> <span data-ttu-id="1c631-117">ジェネレーション 0 のガベージ コレクションの発生後に存在するすべてのオブジェクトは、ジェネレーション 1 に昇格されます。</span><span class="sxs-lookup"><span data-stu-id="1c631-117">All objects that exist after garbage collection occurs in generation 0 are promoted to generation 1.</span></span> <span data-ttu-id="1c631-118">ジェネレーション 1 のガベージ コレクションが発生した後に存在するオブジェクトは、ジェネレーション 2 に移動します。</span><span class="sxs-lookup"><span data-stu-id="1c631-118">Objects that exist after garbage collection occurs in generation 1 move into generation 2.</span></span>  
  
 <span data-ttu-id="1c631-119">ジェネレーションの使用は、ガベージ コレクターは任意の時点で割り当てられたオブジェクトのサブセットのみを使用することを意味します。</span><span class="sxs-lookup"><span data-stu-id="1c631-119">The use of generations means that the garbage collector has to work with only a subset of the allocated objects at any one time.</span></span>  
  
 <span data-ttu-id="1c631-120">`COR_PRF_GC_GENERATION`列挙型を使用して、 [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md)構造体。</span><span class="sxs-lookup"><span data-stu-id="1c631-120">The `COR_PRF_GC_GENERATION` enumeration is used by the [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c631-121">要件</span><span class="sxs-lookup"><span data-stu-id="1c631-121">Requirements</span></span>  
 <span data-ttu-id="1c631-122">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1c631-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c631-123">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1c631-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1c631-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c631-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c631-125">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c631-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c631-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="1c631-126">See Also</span></span>  
 [<span data-ttu-id="1c631-127">列挙型のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="1c631-127">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
