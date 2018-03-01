---
title: "ICorProfilerCallback4 インターフェイス"
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
- ICorProfilerCallback4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4
helpviewer_keywords:
- ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 665f3cfc-cd6f-4880-906c-ea65ad384783
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: efcbc9adce9b5cfc39c5eb3e1649a35d458e99c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback4-interface"></a><span data-ttu-id="a359c-102">ICorProfilerCallback4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a359c-102">ICorProfilerCallback4 Interface</span></span>
<span data-ttu-id="a359c-103">共通言語ランタイム (CLR) がプロファイラーに情報を通信するために使用するコールバック メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a359c-103">Provides callback methods that the common language runtime (CLR) uses to communicate information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a359c-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="a359c-104">Methods</span></span>  
  
|<span data-ttu-id="a359c-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a359c-105">Method</span></span>|<span data-ttu-id="a359c-106">説明</span><span class="sxs-lookup"><span data-stu-id="a359c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a359c-107">GetReJITParameters メソッド</span><span class="sxs-lookup"><span data-stu-id="a359c-107">GetReJITParameters Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)|<span data-ttu-id="a359c-108">新しい再コンパイルされたメソッドの本体の代替コード生成フラグを設定するコード プロファイラーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a359c-108">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>|  
|[<span data-ttu-id="a359c-109">MovedReferences2 メソッド</span><span class="sxs-lookup"><span data-stu-id="a359c-109">MovedReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)|<span data-ttu-id="a359c-110">圧縮ガベージ コレクション ヒープ内のオブジェクトの新しいレイアウトを報告します。</span><span class="sxs-lookup"><span data-stu-id="a359c-110">Reports the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>|  
|[<span data-ttu-id="a359c-111">ReJITCompilationFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="a359c-111">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)|<span data-ttu-id="a359c-112">・ イン タイム (JIT) コンパイラが関数の再コンパイルを完了したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="a359c-112">Notifies the profiler that the just-in-time (JIT) compiler has finished the recompilation of a function.</span></span>|  
|[<span data-ttu-id="a359c-113">ReJITCompilationStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="a359c-113">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)|<span data-ttu-id="a359c-114">関数を再コンパイルする・ イン タイム (JIT) コンパイラが開始されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="a359c-114">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>|  
|[<span data-ttu-id="a359c-115">ReJITError メソッド</span><span class="sxs-lookup"><span data-stu-id="a359c-115">ReJITError Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md)|<span data-ttu-id="a359c-116">再コンパイル要求の処理中に発生したエラーを報告します。</span><span class="sxs-lookup"><span data-stu-id="a359c-116">Reports an error encountered while processing a recompile request.</span></span>|  
|[<span data-ttu-id="a359c-117">SurvivingReferences2 メソッド</span><span class="sxs-lookup"><span data-stu-id="a359c-117">SurvivingReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)|<span data-ttu-id="a359c-118">非圧縮ガベージ コレクションを実行した後の、ヒープ内のオブジェクトのレイアウトを報告します。</span><span class="sxs-lookup"><span data-stu-id="a359c-118">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a359c-119">コメント</span><span class="sxs-lookup"><span data-stu-id="a359c-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a359c-120">必要条件</span><span class="sxs-lookup"><span data-stu-id="a359c-120">Requirements</span></span>  
 <span data-ttu-id="a359c-121">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a359c-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a359c-122">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a359c-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a359c-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a359c-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a359c-124">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a359c-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a359c-125">参照</span><span class="sxs-lookup"><span data-stu-id="a359c-125">See Also</span></span>  
 [<span data-ttu-id="a359c-126">ICorProfilerCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a359c-126">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [<span data-ttu-id="a359c-127">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="a359c-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="a359c-128">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a359c-128">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
