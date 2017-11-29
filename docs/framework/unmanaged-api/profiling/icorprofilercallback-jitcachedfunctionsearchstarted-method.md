---
title: "ICorProfilerCallback::JITCachedFunctionSearchStarted メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITCachedFunctionSearchStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITCachedFunctionSearchStarted
helpviewer_keywords:
- JITCachedFunctionSearchStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchStarted method [.NET Framework profiling]
ms.assetid: 5cba642c-0d80-48ee-889d-198c5044d821
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 09fcdc67dc730b59b76a2da9f6ccea04800e20c2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a><span data-ttu-id="42300-102">ICorProfilerCallback::JITCachedFunctionSearchStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="42300-102">ICorProfilerCallback::JITCachedFunctionSearchStarted Method</span></span>
<span data-ttu-id="42300-103">ネイティブ イメージ ジェネレーター (NGen.exe) を使用して以前にコンパイルされた関数の検索が開始されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="42300-103">Notifies the profiler that a search has started for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42300-104">構文</span><span class="sxs-lookup"><span data-stu-id="42300-104">Syntax</span></span>  
  
```  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="42300-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="42300-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="42300-106">[in]検索が実行される関数の ID。</span><span class="sxs-lookup"><span data-stu-id="42300-106">[in] The ID of the function for which the search is being performed.</span></span>  
  
 `pbUseCachedFunction`  
 <span data-ttu-id="42300-107">[out]`true`実行エンジンは、(使用可能な場合) に、キャッシュされたバージョンの関数を使用する場合は、それ以外の`false`します。</span><span class="sxs-lookup"><span data-stu-id="42300-107">[out] `true` if the execution engine should use the cached version of a function (if available); otherwise `false`.</span></span> <span data-ttu-id="42300-108">値が場合`false`の実行エンジンは JIT コンパイルではないバージョンを使用する代わりに、関数、JIT コンパイルします。</span><span class="sxs-lookup"><span data-stu-id="42300-108">If the value is `false`, the execution engine JIT-compiles the function instead of using a version that is not JIT-compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42300-109">コメント</span><span class="sxs-lookup"><span data-stu-id="42300-109">Remarks</span></span>  
 <span data-ttu-id="42300-110">.NET framework version 2.0 では、`JITCachedFunctionSearchStarted`と[icorprofilercallback::jitcachedfunctionsearchfinished メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md)正規の NGen イメージのすべての関数のコールバックは行われません。</span><span class="sxs-lookup"><span data-stu-id="42300-110">In the .NET Framework version 2.0, the `JITCachedFunctionSearchStarted` and [ICorProfilerCallback::JITCachedFunctionSearchFinished Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="42300-111">プロファイル用に最適化された NGen イメージだけは、すべての関数のコールバックをイメージに生成されます。</span><span class="sxs-lookup"><span data-stu-id="42300-111">Only NGen images optimized for a profile will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="42300-112">ただし、追加のオーバーヘッドにより、プロファイラー NGen イメージのプロファイラー最適化する必要があります要求した場合、関数のコンパイル済みジャストでタイム (JIT) を強制的にこれらのコールバックを使用する場合にのみにします。</span><span class="sxs-lookup"><span data-stu-id="42300-112">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="42300-113">それ以外の場合、プロファイラーは、関数の情報を収集するため、限定的な戦略を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="42300-113">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
 <span data-ttu-id="42300-114">プロファイラーは、プロファイリング対象のアプリケーションの複数のスレッドが、同じメソッドを同時に呼び出す場合をサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="42300-114">Profilers must support cases where multiple threads of a profiled application are calling the same method simultaneously.</span></span> <span data-ttu-id="42300-115">たとえば、スレッド A が`JITCachedFunctionSearchStarted`し応答する状態を設定して、プロファイラー *pbUseCachedFunction*JIT コンパイルを強制する場合は FALSE にします。</span><span class="sxs-lookup"><span data-stu-id="42300-115">For example, thread A calls `JITCachedFunctionSearchStarted` and the profiler responds by setting *pbUseCachedFunction*to FALSE to force JIT compilation.</span></span> <span data-ttu-id="42300-116">A はそのを呼び出すスレッド[icorprofilercallback::jitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)と[icorprofilercallback::jitcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="42300-116">Thread A then calls [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) and [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).</span></span>  
  
 <span data-ttu-id="42300-117">スレッド B の呼び出しのようになりました`JITCachedFunctionSearchStarted`同じ関数。</span><span class="sxs-lookup"><span data-stu-id="42300-117">Now thread B calls `JITCachedFunctionSearchStarted` for the same function.</span></span> <span data-ttu-id="42300-118">プロファイラーがスレッド B が A のスレッドの呼び出しにプロファイラーが前に、コールバックを送信するために、2 番目のコールバックを受け取る場合でも、プロファイラーは、関数の JIT コンパイルする意向を言うと、`JITCachedFunctionSearchStarted`です。</span><span class="sxs-lookup"><span data-stu-id="42300-118">Even though the profiler has stated its intention to JIT-compile the function, the profiler receives the second callback because thread B sends the callback before the profiler has responded to thread A's call to `JITCachedFunctionSearchStarted`.</span></span> <span data-ttu-id="42300-119">スレッドが呼び出しを行う順序は、スレッドのスケジュール方法によって異なります。</span><span class="sxs-lookup"><span data-stu-id="42300-119">The order in which the threads make calls depends on how the threads are scheduled.</span></span>  
  
 <span data-ttu-id="42300-120">によって参照される値を設定する必要があります、プロファイラーは、重複するコールバックを受信すると`pbUseCachedFunction`重複するすべてのコールバックの同じ値にします。</span><span class="sxs-lookup"><span data-stu-id="42300-120">When the profiler receives duplicate callbacks, it must set the value referenced by `pbUseCachedFunction` to the same value for all the duplicate callbacks.</span></span> <span data-ttu-id="42300-121">つまり、`JITCachedFunctionSearchStarted`同じで複数回呼び出された`functionId`値、プロファイラー対応する必要が同じたびにします。</span><span class="sxs-lookup"><span data-stu-id="42300-121">That is, when `JITCachedFunctionSearchStarted` is called multiple times with the same `functionId` value, the profiler must respond the same each time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42300-122">要件</span><span class="sxs-lookup"><span data-stu-id="42300-122">Requirements</span></span>  
 <span data-ttu-id="42300-123">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="42300-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42300-124">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="42300-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="42300-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42300-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42300-126">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42300-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42300-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="42300-127">See Also</span></span>  
 [<span data-ttu-id="42300-128">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42300-128">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
