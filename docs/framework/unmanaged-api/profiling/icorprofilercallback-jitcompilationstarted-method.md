---
title: "ICorProfilerCallback::JITCompilationStarted メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITCompilationStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITCompilationStarted
helpviewer_keywords:
- JITCompilationStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationStarted method [.NET Framework profiling]
ms.assetid: 31782b36-d311-4518-8f45-25f65385af5b
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 12a25f452ccb121ef7ebcae05048eb7116b4ac48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a><span data-ttu-id="4e45f-102">ICorProfilerCallback::JITCompilationStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="4e45f-102">ICorProfilerCallback::JITCompilationStarted Method</span></span>
<span data-ttu-id="4e45f-103">関数をコンパイル ・ イン タイム (JIT) コンパイラが開始されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="4e45f-103">Notifies the profiler that the just-in-time (JIT) compiler has started to compile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e45f-104">構文</span><span class="sxs-lookup"><span data-stu-id="4e45f-104">Syntax</span></span>  
  
```  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4e45f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4e45f-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="4e45f-106">[in]コンパイルの開始を関数の ID。</span><span class="sxs-lookup"><span data-stu-id="4e45f-106">[in] The ID of the function for which the compilation is starting.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="4e45f-107">[in]プロファイラーをブロックするかどうかを示す値は、ランタイムの動作に影響されます。</span><span class="sxs-lookup"><span data-stu-id="4e45f-107">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="4e45f-108">値が`true`ブロックにより、ランタイムでこのコールバックから戻るには、呼び出し元のスレッドを待機する場合は、それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="4e45f-108">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="4e45f-109">値が`true`は妨げられませんが、ランタイム、プロファイルの結果の傾斜を実行できます。</span><span class="sxs-lookup"><span data-stu-id="4e45f-109">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e45f-110">コメント</span><span class="sxs-lookup"><span data-stu-id="4e45f-110">Remarks</span></span>  
 <span data-ttu-id="4e45f-111">2 つ以上のペアを受信することは`JITCompilationStarted`と[icorprofilercallback::jitcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)各関数の方法により、ランタイム ハンドル クラス コンス トラクターを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4e45f-111">It is possible to receive more than one pair of `JITCompilationStarted` and [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="4e45f-112">たとえば、ランタイム JIT コンパイル メソッド A を開始がクラス B のクラス コンス トラクターを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4e45f-112">For example, the runtime starts to JIT-compile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="4e45f-113">したがって、ランタイム JIT コンパイル クラス B のコンス トラクターおよびそれを実行します。</span><span class="sxs-lookup"><span data-stu-id="4e45f-113">Therefore, the runtime JIT-compiles the constructor for class B and runs it.</span></span> <span data-ttu-id="4e45f-114">コンス トラクターが実行されている、メソッド、メソッドを JIT コンパイルもう一度 A A への呼び出しになります。</span><span class="sxs-lookup"><span data-stu-id="4e45f-114">While the constructor is running, it makes a call to method A, which causes method A to be JIT-compiled again.</span></span> <span data-ttu-id="4e45f-115">このシナリオでは、メソッド A の最初の JIT コンパイルは中断されます。</span><span class="sxs-lookup"><span data-stu-id="4e45f-115">In this scenario, the first JIT compilation of method A is halted.</span></span> <span data-ttu-id="4e45f-116">ただし、JIT コンパイル メソッド A に両方の試行は、JIT コンパイル イベントで報告されます。</span><span class="sxs-lookup"><span data-stu-id="4e45f-116">However, both attempts to JIT-compile method A are reported with JIT-compilation events.</span></span> <span data-ttu-id="4e45f-117">プロファイラーを呼び出してメソッド A の Microsoft intermediate language (MSIL) コードを交換する場合は、 [icorprofilerinfo::setilfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)メソッド、両方のようにする必要があります`JITCompilationStarted`可能性があります、同じ MSIL ブロックを使用して、イベントが、両方です。</span><span class="sxs-lookup"><span data-stu-id="4e45f-117">If the profiler is going to replace Microsoft intermediate language (MSIL) code for method A by calling the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, it must do so for both `JITCompilationStarted` events, but it may use the same MSIL block for both.</span></span>  
  
 <span data-ttu-id="4e45f-118">プロファイラーは、場合は、2 つのスレッドでは、コールバックを行う同時に JIT コールバックのシーケンスをサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4e45f-118">Profilers must support the sequence of JIT callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="4e45f-119">たとえば、スレッド A が`JITCompilationStarted`です。</span><span class="sxs-lookup"><span data-stu-id="4e45f-119">For example, thread A calls `JITCompilationStarted`.</span></span> <span data-ttu-id="4e45f-120">ただし、スレッド A 呼び出し前に`JITCompilationFinished`、スレッド B 呼び出し[icorprofilercallback::exceptionsearchfunctionenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) A のスレッドから関数の ID を持つ`JITCompilationStarted`コールバック。</span><span class="sxs-lookup"><span data-stu-id="4e45f-120">However, before thread A calls `JITCompilationFinished`, thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from thread A's `JITCompilationStarted` callback.</span></span> <span data-ttu-id="4e45f-121">関数の ID がないまだ有効であることが表示されるためへの呼び出し`JITCompilationFinished`がまだ受信されていません、プロファイラーによってです。</span><span class="sxs-lookup"><span data-stu-id="4e45f-121">It might appear that the function ID should not yet be valid because a call to `JITCompilationFinished` had not yet been received by the profiler.</span></span> <span data-ttu-id="4e45f-122">ただし、このような場合は、関数の ID は有効です。</span><span class="sxs-lookup"><span data-stu-id="4e45f-122">However, in a case like this one, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e45f-123">必要条件</span><span class="sxs-lookup"><span data-stu-id="4e45f-123">Requirements</span></span>  
 <span data-ttu-id="4e45f-124">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4e45f-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e45f-125">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4e45f-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4e45f-126">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e45f-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e45f-127">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e45f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e45f-128">参照</span><span class="sxs-lookup"><span data-stu-id="4e45f-128">See Also</span></span>  
 [<span data-ttu-id="4e45f-129">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4e45f-129">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="4e45f-130">JITCompilationFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="4e45f-130">JITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
