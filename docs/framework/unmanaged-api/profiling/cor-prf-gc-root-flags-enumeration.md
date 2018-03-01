---
title: "COR_PRF_GC_ROOT_FLAGS 列挙型"
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
- COR_PRF_GC_ROOT_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_FLAGS
helpviewer_keywords:
- COR_PRF_GC_ROOT_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 4611ee6f-0f05-4d84-91e1-e83d5e7dd7e4
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5e00f695edb94acbd54d6bd009ccd629aeec1b14
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="corprfgcrootflags-enumeration"></a><span data-ttu-id="c8084-102">COR_PRF_GC_ROOT_FLAGS 列挙型</span><span class="sxs-lookup"><span data-stu-id="c8084-102">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>
<span data-ttu-id="c8084-103">ガーベッジ コレクション ルートのプロパティを示します。</span><span class="sxs-lookup"><span data-stu-id="c8084-103">Indicates a property of a garbage collection root.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8084-104">構文</span><span class="sxs-lookup"><span data-stu-id="c8084-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_ROOT_PINNING = 0x1,  
    COR_PRF_GC_ROOT_WEAKREF = 0x2,  
    COR_PRF_GC_ROOT_INTERIOR = 0x4,  
    COR_PRF_GC_ROOT_REFCOUNTED = 0x8,  
} COR_PRF_GC_ROOT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="c8084-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="c8084-105">Members</span></span>  
  
|<span data-ttu-id="c8084-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="c8084-106">Member</span></span>|<span data-ttu-id="c8084-107">説明</span><span class="sxs-lookup"><span data-stu-id="c8084-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_PINNING`|<span data-ttu-id="c8084-108">ルートでは、ガベージ コレクション オブジェクトを移動できないようにします。</span><span class="sxs-lookup"><span data-stu-id="c8084-108">The root prevents a garbage collection from moving the object.</span></span>|  
|`COR_PRF_GC_ROOT_WEAKREF`|<span data-ttu-id="c8084-109">ルートは、ガベージ コレクションを阻止されません。</span><span class="sxs-lookup"><span data-stu-id="c8084-109">The root does not prevent garbage collection.</span></span>|  
|`COR_PRF_GC_ROOT_INTERIOR`|<span data-ttu-id="c8084-110">ルートは、オブジェクト自体ではなく、オブジェクトのフィールドを参照します。</span><span class="sxs-lookup"><span data-stu-id="c8084-110">The root refers to a field of the object rather than the object itself.</span></span>|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|<span data-ttu-id="c8084-111">ルートは、オブジェクトの参照カウントが特定の値である場合に、ガベージ コレクションを回避します。</span><span class="sxs-lookup"><span data-stu-id="c8084-111">The root prevents garbage collection if the reference count of the object is a certain value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8084-112">コメント</span><span class="sxs-lookup"><span data-stu-id="c8084-112">Remarks</span></span>  
 <span data-ttu-id="c8084-113">`COR_PRF_GC_ROOT_FLAGS`特殊なルートに関する追加情報を提供できるビットマスクであります。</span><span class="sxs-lookup"><span data-stu-id="c8084-113">`COR_PRF_GC_ROOT_FLAGS` is a bitmask that provides additional information about special roots.</span></span> <span data-ttu-id="c8084-114">ただし、すべてのルートは特殊です。</span><span class="sxs-lookup"><span data-stu-id="c8084-114">However, not all roots are special.</span></span> <span data-ttu-id="c8084-115">たとえば、一部のルートは、弱い参照を内部ポインター、ピン留めされた、または参照カウントではありません。</span><span class="sxs-lookup"><span data-stu-id="c8084-115">For example, some roots are not weak references, interior pointers, pinned, or reference-counted.</span></span> <span data-ttu-id="c8084-116">このようなルートを伝えるためにフラグがありません。</span><span class="sxs-lookup"><span data-stu-id="c8084-116">For such roots, there are no flags to convey.</span></span> <span data-ttu-id="c8084-117">したがってなど、この列挙を使用するメソッド、 [icorprofilercallback 2::rootreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)メソッド、送信 0 すべてフラグを設定するかを示す、フラグ ビットがオフになっています。</span><span class="sxs-lookup"><span data-stu-id="c8084-117">Therefore, methods that use this enumeration, such as the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) method, send 0 for the flags bitmask, indicating that all flags are turned off.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8084-118">必要条件</span><span class="sxs-lookup"><span data-stu-id="c8084-118">Requirements</span></span>  
 <span data-ttu-id="c8084-119">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c8084-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8084-120">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c8084-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c8084-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8084-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8084-122">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8084-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8084-123">参照</span><span class="sxs-lookup"><span data-stu-id="c8084-123">See Also</span></span>  
 [<span data-ttu-id="c8084-124">列挙型のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="c8084-124">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
