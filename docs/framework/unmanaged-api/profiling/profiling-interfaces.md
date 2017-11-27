---
title: "プロファイリングのインターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
caps.latest.revision: "31"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5c0423f9c8b01c1289e1107c0c16c59968a6e2a4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="profiling-interfaces"></a><span data-ttu-id="9a1eb-102">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a1eb-102">Profiling Interfaces</span></span>
<span data-ttu-id="9a1eb-103">ここでは、共通言語ランタイム (CLR) で実行中のプログラムに対してプロファイルを可能にするアンマネージ インターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9a1eb-103">This section describes the unmanaged interfaces that enable you to profile a program that is being executed by the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9a1eb-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="9a1eb-104">In This Section</span></span>  
 [<span data-ttu-id="9a1eb-105">ICLRProfiling インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a1eb-105">ICLRProfiling Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-interface.md)  
 <span data-ttu-id="9a1eb-106">提供、 [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md)メソッドは、プロファイラーが実行中のプロセスにアタッチすることができます。</span><span class="sxs-lookup"><span data-stu-id="9a1eb-106">Provides the [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) method, which enables a profiler to attach to a running process.</span></span>  
  
 [<span data-ttu-id="9a1eb-107">ICorProfilerAssemblyReferenceProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a1eb-107">ICorProfilerAssemblyReferenceProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 <span data-ttu-id="9a1eb-108">プロファイラーのプロファイラーを追加するアセンブリ参照の CLR に通知を有効に、 [icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="9a1eb-108">Enables the profiler to inform the CLR of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
 [<span data-ttu-id="9a1eb-109">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a1eb-109">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 <span data-ttu-id="9a1eb-110">プロファイラーがサブスクライブしたイベントが発生したときにコード プロファイラーに通知するために、CLR が使用するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="9a1eb-110">Provides methods that are used by the CLR to notify a code profiler when the events to which the profiler has subscribed occur.</span></span>  
  
 [<span data-ttu-id="9a1eb-111">ICorProfilerCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a1eb-111">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 <span data-ttu-id="9a1eb-112">.NET Framework 2.0 以降でサポートされるコールバックによって、`ICorProfilerCallback` インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="9a1eb-112">Extends the `ICorProfilerCallback` interface with callbacks supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="9a1eb-113">ICorProfilerCallback3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a1eb-113">ICorProfilerCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 <span data-ttu-id="9a1eb-114">CLR がプロファイラーにアタッチとデタッチの状態情報を伝えるために使用するコールバック メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="9a1eb-114">Provides callback methods that the CLR uses to communicate attach and detach state information to the profiler.</span></span>  
  
 [<span data-ttu-id="9a1eb-115">ICorProfilerCallback4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a1eb-115">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 <span data-ttu-id="9a1eb-116">プロファイラーと情報をやりとりするために CLR が使用するコールバック メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="9a1eb-116">Provides callback methods that the CLR uses to communicate information to the profiler.</span></span>  
  
 [<span data-ttu-id="9a1eb-117">ICorProfilerCallback5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a1eb-117">ICorProfilerCallback5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)  
 <span data-ttu-id="9a1eb-118">ガベージ コレクションのルートによって参照されるオブジェクトの遷移的なクロージャを識別するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="9a1eb-118">Provides a method that identifies the transitive closure of objects referenced by garbage collection roots.</span></span>  
  
 [<span data-ttu-id="9a1eb-119">ICorProfilerCallback6 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a1eb-119">ICorProfilerCallback6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)  
 <span data-ttu-id="9a1eb-120">CLR が プロファイラーに対して、アセンブリがロード中であることを通知するために使用するコールバック メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="9a1eb-120">Provides a callback method that the CLR uses to notify a profiler that an assembly is loading.</span></span>  
  
 [<span data-ttu-id="9a1eb-121">ICorProfilerCallback7 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a1eb-121">ICorProfilerCallback7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)  
 <span data-ttu-id="9a1eb-122">共通言語ランタイムを使用してメモリ内のモジュールに関連付けられているシンボルのストリームが更新されることをプロファイラーに通知するコールバック メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="9a1eb-122">Provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
 [<span data-ttu-id="9a1eb-123">ICorProfilerFunctionControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a1eb-123">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)  
 <span data-ttu-id="9a1eb-124">コード プロファイラーが CLR と通信できるようにするためのメソッドを提供します。これは特定のメソッドを再コンパイルするときに、JIT コンパイラーがどのようにしてコードを生成するかを制御するためのものです。</span><span class="sxs-lookup"><span data-stu-id="9a1eb-124">Provides methods that allow a code profiler to communicate with the CLR to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
 [<span data-ttu-id="9a1eb-125">ICorProfilerFunctionEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a1eb-125">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 <span data-ttu-id="9a1eb-126">CLR で関数のコレクションを順番に反復処理するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="9a1eb-126">Provides methods to sequentially iterate through a collection of functions in the CLR.</span></span>  
  
 [<span data-ttu-id="9a1eb-127">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a1eb-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 <span data-ttu-id="9a1eb-128">コード プロファイラーが、イベントの監視および情報の要求を制御するために CLR との通信で使用するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="9a1eb-128">Provides methods for use by code profilers to communicate with the CLR to control event monitoring and request information.</span></span>  
  
 [<span data-ttu-id="9a1eb-129">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a1eb-129">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 <span data-ttu-id="9a1eb-130">.NET Framework 2.0 以降でサポートされるメソッドによって、`ICorProfilerInfo` インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="9a1eb-130">Extends the `ICorProfilerInfo` interface with methods supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="9a1eb-131">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a1eb-131">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 <span data-ttu-id="9a1eb-132">`ICorProfilerInfo2` 以降でサポートされるメソッドによって、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="9a1eb-132">Extends the `ICorProfilerInfo2` interface with methods supported in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] and later versions.</span></span>  
  
 [<span data-ttu-id="9a1eb-133">ICorProfilerInfo4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a1eb-133">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 <span data-ttu-id="9a1eb-134">コード プロファイラーが、イベントの監視および情報の要求を制御するために CLR との通信で使用するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="9a1eb-134">Provides methods that code profilers use to communicate with the CLR to control event monitoring and to request information.</span></span>  
  
 [<span data-ttu-id="9a1eb-135">ICorProfilerInfo5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a1eb-135">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 <span data-ttu-id="9a1eb-136">コード プロファイラーが、イベントの監視を制御するために CLR との通信で使用するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="9a1eb-136">Provides methods for use by code profilers to communicate with the CLR to control event monitoring.</span></span>  
  
 [<span data-ttu-id="9a1eb-137">ICorProfilerInfo6 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a1eb-137">ICorProfilerInfo6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)  
 <span data-ttu-id="9a1eb-138">列挙子を指定した NGen モジュールに属するし、は、特定のメソッドの本体でインライン展開をすべてのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="9a1eb-138">Provides an enumerator to all the methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>  
  
 [<span data-ttu-id="9a1eb-139">ICorProfilerInfo7 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a1eb-139">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)  
 <span data-ttu-id="9a1eb-140">新しくを適用するためのメソッドでは、モジュールにメタデータが定義されているし、メモリ内のシンボルのストリームへのアクセスを提供するを提供します。</span><span class="sxs-lookup"><span data-stu-id="9a1eb-140">Provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
 [<span data-ttu-id="9a1eb-141">ICorProfilerModuleEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a1eb-141">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 <span data-ttu-id="9a1eb-142">アプリケーションまたはプロファイラーによってロードされたモジュールのコレクションを順番に反復処理するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="9a1eb-142">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
 [<span data-ttu-id="9a1eb-143">ICorProfilerObjectEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a1eb-143">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)  
 <span data-ttu-id="9a1eb-144">によって生成される固定されたオブジェクトのコレクションを順番に反復処理するメソッドを提供[Ngen.exe (ネイティブ イメージ ジェネレーター)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md)です。</span><span class="sxs-lookup"><span data-stu-id="9a1eb-144">Provides methods to sequentially iterate through a collection of frozen objects that are generated by [Ngen.exe (Native Image Generator)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>  
  
 [<span data-ttu-id="9a1eb-145">ICorProfilerThreadEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a1eb-145">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 <span data-ttu-id="9a1eb-146">CLR でスレッドのコレクションを順番に反復処理するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="9a1eb-146">Provides methods to sequentially iterate through a collection of threads in the CLR.</span></span>  
  
 [<span data-ttu-id="9a1eb-147">IMethodMalloc インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a1eb-147">IMethodMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)  
 <span data-ttu-id="9a1eb-148">提供、[アロケーション](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)メソッドの新しい Microsoft intermediate language (MSIL) 関数本体にメモリを割り当てられません。</span><span class="sxs-lookup"><span data-stu-id="9a1eb-148">Provides the [Alloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9a1eb-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a1eb-149">Related Sections</span></span>  
 [<span data-ttu-id="9a1eb-150">プロファイルの概要</span><span class="sxs-lookup"><span data-stu-id="9a1eb-150">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="9a1eb-151">プロファイリング グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="9a1eb-151">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="9a1eb-152">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="9a1eb-152">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [<span data-ttu-id="9a1eb-153">構造体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="9a1eb-153">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
