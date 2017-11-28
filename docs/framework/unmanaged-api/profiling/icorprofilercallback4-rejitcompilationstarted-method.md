---
title: "ICorProfilerCallback4::ReJITCompilationStarted メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.ReJITCompilationStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::ReJITCompilationStarted
helpviewer_keywords:
- ReJITCompilationStarted method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITCompilationStarted method [.NET Framework profiling]
ms.assetid: 512fdd00-262a-4456-a075-365ef4133c4d
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ddcacf72d21ec076fe74a1c069311ef3f73a20c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a><span data-ttu-id="29d8d-102">ICorProfilerCallback4::ReJITCompilationStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="29d8d-102">ICorProfilerCallback4::ReJITCompilationStarted Method</span></span>
<span data-ttu-id="29d8d-103">関数を再コンパイルする・ イン タイム (JIT) コンパイラが開始されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="29d8d-103">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29d8d-104">構文</span><span class="sxs-lookup"><span data-stu-id="29d8d-104">Syntax</span></span>  
  
```  
HRESULT ReJITCompilationStarted(    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29d8d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="29d8d-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="29d8d-106">[in]JIT コンパイラが再コンパイルを開始したこと、関数の ID。</span><span class="sxs-lookup"><span data-stu-id="29d8d-106">[in] The ID of the function that the JIT compiler has started to recompile.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="29d8d-107">[in]関数の新しいバージョンの再コンパイルの ID です。</span><span class="sxs-lookup"><span data-stu-id="29d8d-107">[in] The recompilation ID of the new version of the function.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="29d8d-108">[in]`true`ブロックことにより、ランタイムでこのコールバックから戻るには、呼び出し元のスレッドの待機を示すために`false`をブロックしていないに影響すること、ランタイムの動作を示します。</span><span class="sxs-lookup"><span data-stu-id="29d8d-108">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span> <span data-ttu-id="29d8d-109">値`true`、実行時に問題が発生しませんが、プロファイルの結果に影響を与えることができます。</span><span class="sxs-lookup"><span data-stu-id="29d8d-109">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29d8d-110">コメント</span><span class="sxs-lookup"><span data-stu-id="29d8d-110">Remarks</span></span>  
 <span data-ttu-id="29d8d-111">2 つ以上のペアを受信することは`ReJITCompilationStarted`と[ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)メソッドの各関数の方法により、ランタイム ハンドル クラス コンス トラクターを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="29d8d-111">It is possible to receive more than one pair of `ReJITCompilationStarted` and [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) method calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="29d8d-112">たとえば、ランタイム メソッド A には、再コンパイルを開始が、クラス B のクラス コンス トラクターを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="29d8d-112">For example, the runtime starts to recompile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="29d8d-113">そのため、ランタイムは、クラス B のコンス トラクターを再コンパイルし、それを実行します。</span><span class="sxs-lookup"><span data-stu-id="29d8d-113">Therefore, the runtime recompiles the constructor for class B and runs it.</span></span> <span data-ttu-id="29d8d-114">コンス トラクターが実行されている、メソッド、もう一度再コンパイルするメソッド A A への呼び出しになります。</span><span class="sxs-lookup"><span data-stu-id="29d8d-114">While the constructor is running, it makes a call to method A, which causes method A to be recompiled again.</span></span> <span data-ttu-id="29d8d-115">このシナリオでは、メソッド A の最初の再コンパイルは中断されます。</span><span class="sxs-lookup"><span data-stu-id="29d8d-115">In this scenario, the first recompilation of method A is halted.</span></span> <span data-ttu-id="29d8d-116">ただし、両方は、メソッドの JIT 再コンパイル イベントで報告されるされます再コンパイルを試みます。</span><span class="sxs-lookup"><span data-stu-id="29d8d-116">However, both attempts to recompile method A are reported with JIT recompilation events.</span></span>  
  
 <span data-ttu-id="29d8d-117">プロファイラーは、場合は、2 つのスレッドでは、コールバックを行う同時に JIT 再コンパイルのコールバックのシーケンスをサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="29d8d-117">Profilers must support the sequence of JIT recompilation callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="29d8d-118">たとえば、スレッド A が`ReJITCompilationStarted`ですただし、スレッド A 呼び出し前に[ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)、スレッド B 呼び出し[icorprofilercallback::exceptionsearchfunctionenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)関数の ID を持つ。`ReJITCompilationStarted`スレッド A のコールバック関数の ID がないまだ有効であることが表示されるためへの呼び出し[ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)がまだ受信されていません、プロファイラーによってです。</span><span class="sxs-lookup"><span data-stu-id="29d8d-118">For example, thread A calls `ReJITCompilationStarted`; however, before thread A calls [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from the `ReJITCompilationStarted` callback for thread A. It might appear that the function ID should not yet be valid because a call to [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) had not yet been received by the profiler.</span></span> <span data-ttu-id="29d8d-119">ただし、この場合、関数の ID は有効です。</span><span class="sxs-lookup"><span data-stu-id="29d8d-119">However, in this case, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29d8d-120">要件</span><span class="sxs-lookup"><span data-stu-id="29d8d-120">Requirements</span></span>  
 <span data-ttu-id="29d8d-121">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="29d8d-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29d8d-122">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="29d8d-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="29d8d-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29d8d-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29d8d-124">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29d8d-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29d8d-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="29d8d-125">See Also</span></span>  
 [<span data-ttu-id="29d8d-126">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="29d8d-126">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="29d8d-127">ICorProfilerCallback4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="29d8d-127">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 [<span data-ttu-id="29d8d-128">JITCompilationFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="29d8d-128">JITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)  
 [<span data-ttu-id="29d8d-129">ReJITCompilationFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="29d8d-129">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)
