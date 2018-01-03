---
title: "COR_PRF_SNAPSHOT_INFO 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_SNAPSHOT_INFO
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_SNAPSHOT_INFO
helpviewer_keywords: COR_PRF_SNAPSHOT_INFO enumeration [.NET Framework profiling]
ms.assetid: a5906b2a-ad4a-4cc6-a421-2d7d8adf7468
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4573ec44253b1b0f26ae62591db149f0447d3935
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="corprfsnapshotinfo-enumeration"></a><span data-ttu-id="a6924-102">COR_PRF_SNAPSHOT_INFO 列挙型</span><span class="sxs-lookup"><span data-stu-id="a6924-102">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>
<span data-ttu-id="a6924-103">プロファイラーの各呼び出しにスタック スナップショットを使用して渡すデータをバックアップする作業がどの程度を示す[StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md)関数。</span><span class="sxs-lookup"><span data-stu-id="a6924-103">Specifies how much data to pass back with a stack snapshot in each call to the profiler's [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6924-104">構文</span><span class="sxs-lookup"><span data-stu-id="a6924-104">Syntax</span></span>  
  
```  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="a6924-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="a6924-105">Members</span></span>  
  
|<span data-ttu-id="a6924-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="a6924-106">Members</span></span>|<span data-ttu-id="a6924-107">説明</span><span class="sxs-lookup"><span data-stu-id="a6924-107">Description</span></span>|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|<span data-ttu-id="a6924-108">すべての値を渡す必要があることを示します`StackSnapshotCallback`パラメーターを除く、`context`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="a6924-108">Indicates that values must be passed for all `StackSnapshotCallback` parameters, except the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|<span data-ttu-id="a6924-109">すべての値を渡す必要があることを示します`StackSnapshotCallback`などのパラメーター、`context`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="a6924-109">Indicates that values must be passed for all `StackSnapshotCallback` parameters, including the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|<span data-ttu-id="a6924-110">単純化し、別のスタック ウォーク アルゴリズムを使用することを示します。</span><span class="sxs-lookup"><span data-stu-id="a6924-110">Indicates that a simpler, alternative stack-walking algorithm will be used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6924-111">コメント</span><span class="sxs-lookup"><span data-stu-id="a6924-111">Remarks</span></span>  
 <span data-ttu-id="a6924-112">によって指定された値を`COR_PRF_SNAPSHOT_INFO`へのパラメーターとして渡される列挙型、 [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="a6924-112">Values that are provided by the `COR_PRF_SNAPSHOT_INFO` enumeration are passed as parameters to the [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6924-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="a6924-113">Requirements</span></span>  
 <span data-ttu-id="a6924-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a6924-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6924-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a6924-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a6924-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6924-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6924-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6924-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6924-118">参照</span><span class="sxs-lookup"><span data-stu-id="a6924-118">See Also</span></span>  
 [<span data-ttu-id="a6924-119">DoStackSnapshot メソッド</span><span class="sxs-lookup"><span data-stu-id="a6924-119">DoStackSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
 [<span data-ttu-id="a6924-120">列挙型のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="a6924-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
