---
title: ICorProfilerCallback5 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback5
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback5
helpviewer_keywords:
- ICorProfilerCallback5 interface [.NET Framework profiling]
ms.assetid: 61d2e9ef-5f1f-4771-8847-239616e35d84
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 338bc10e02ceba5fb38c70088c4151271fca9b2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454413"
---
# <a name="icorprofilercallback5-interface"></a><span data-ttu-id="cd6bb-102">ICorProfilerCallback5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cd6bb-102">ICorProfilerCallback5 Interface</span></span>
<span data-ttu-id="cd6bb-103">プロファイラーがいずれかを使用すると、ライブ オブジェクトの完全終了を識別する情報を補足するもの、 [icorprofilercallback::rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)または[icorprofilercallback 2::rootreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)メソッドと共に、 [icorprofilercallback::objectreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)と[ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="cd6bb-103">Supplements information to help a profiler identify the full closure of live objects, when used with either the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) or [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) method together with the [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) and [ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) methods.</span></span>  
  
 <span data-ttu-id="cd6bb-104">`ICorProfilerCallback5` は、依存ハンドルに関連する通知をサブスクライブするために、マネージ メモリ プロファイラーによって実装される必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd6bb-104">`ICorProfilerCallback5` must be implemented by a managed memory profiler to subscribe to notifications related to dependent handles.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd6bb-105">コメント</span><span class="sxs-lookup"><span data-stu-id="cd6bb-105">Remarks</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cd6bb-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="cd6bb-106">Methods</span></span>  
  
|<span data-ttu-id="cd6bb-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="cd6bb-107">Method</span></span>|<span data-ttu-id="cd6bb-108">説明</span><span class="sxs-lookup"><span data-stu-id="cd6bb-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cd6bb-109">ConditionalWeakTableElementReferences メソッド</span><span class="sxs-lookup"><span data-stu-id="cd6bb-109">ConditionalWeakTableElementReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md)|<span data-ttu-id="cd6bb-110">直接のメンバー フィールド参照および `ConditionalWeakTable` 依存を介してこれらのルーツによって参照されるオブジェクトの推移的終了を識別します。</span><span class="sxs-lookup"><span data-stu-id="cd6bb-110">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cd6bb-111">要件</span><span class="sxs-lookup"><span data-stu-id="cd6bb-111">Requirements</span></span>  
 <span data-ttu-id="cd6bb-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cd6bb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd6bb-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cd6bb-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cd6bb-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd6bb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd6bb-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd6bb-115">See Also</span></span>  
 [<span data-ttu-id="cd6bb-116">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="cd6bb-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="cd6bb-117">ICorProfilerCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cd6bb-117">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
