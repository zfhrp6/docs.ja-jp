---
title: "列挙体のプロファイリング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- profiling enumerations [.NET Framework]
- enumerations [.NET Framework profiling]
- unmanaged enumerations [.NET Framework], profiling
ms.assetid: 8d5f9570-9853-4ce8-8101-df235d5b258e
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2e0b539c8e455040cc97f37f75476b0efe796abb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="profiling-enumerations"></a><span data-ttu-id="2a794-102">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="2a794-102">Profiling Enumerations</span></span>
<span data-ttu-id="2a794-103">このセクションでは、プロファイル API が使用するアンマネージ列挙について説明します。</span><span class="sxs-lookup"><span data-stu-id="2a794-103">This section describes the unmanaged enumerations that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2a794-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="2a794-104">In This Section</span></span>  
 [<span data-ttu-id="2a794-105">COR_PRF_CLAUSE_TYPE 列挙型</span><span class="sxs-lookup"><span data-stu-id="2a794-105">COR_PRF_CLAUSE_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md)  
 <span data-ttu-id="2a794-106">コードが入った、または出た例外句のタイプを示します。</span><span class="sxs-lookup"><span data-stu-id="2a794-106">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
 [<span data-ttu-id="2a794-107">COR_PRF_CODEGEN_FLAGS 列挙型</span><span class="sxs-lookup"><span data-stu-id="2a794-107">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)  
 <span data-ttu-id="2a794-108">コード生成フラグを設定することができますを定義、 [icorprofilerfunctioncontrol::setcodegenflags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="2a794-108">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
 [<span data-ttu-id="2a794-109">COR_PRF_FINALIZER_FLAGS 列挙型</span><span class="sxs-lookup"><span data-stu-id="2a794-109">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md)  
 <span data-ttu-id="2a794-110">オブジェクトのファイナライザーを記述します。</span><span class="sxs-lookup"><span data-stu-id="2a794-110">Describes the finalizer for an object.</span></span>  
  
 [<span data-ttu-id="2a794-111">COR_PRF_GC_GENERATION 列挙型</span><span class="sxs-lookup"><span data-stu-id="2a794-111">COR_PRF_GC_GENERATION Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md)  
 <span data-ttu-id="2a794-112">ガベージ コレクションのジェネレーションを識別します。</span><span class="sxs-lookup"><span data-stu-id="2a794-112">Identifies a garbage collection generation.</span></span>  
  
 [<span data-ttu-id="2a794-113">COR_PRF_GC_REASON 列挙型</span><span class="sxs-lookup"><span data-stu-id="2a794-113">COR_PRF_GC_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md)  
 <span data-ttu-id="2a794-114">ガベージ コレクションが発生している理由を示します。</span><span class="sxs-lookup"><span data-stu-id="2a794-114">Indicates the reason that garbage collection is occurring.</span></span>  
  
 [<span data-ttu-id="2a794-115">COR_PRF_GC_ROOT_FLAGS 列挙型</span><span class="sxs-lookup"><span data-stu-id="2a794-115">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md)  
 <span data-ttu-id="2a794-116">ガベージ コレクターのルートのプロパティを示します。</span><span class="sxs-lookup"><span data-stu-id="2a794-116">Indicates properties of a garbage collector root.</span></span>  
  
 [<span data-ttu-id="2a794-117">COR_PRF_GC_ROOT_KIND 列挙型</span><span class="sxs-lookup"><span data-stu-id="2a794-117">COR_PRF_GC_ROOT_KIND Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md)  
 <span data-ttu-id="2a794-118">によって公開されるガベージ コレクターのルートの種類を示す、 [icorprofilercallback 2::rootreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="2a794-118">Indicates the kind of garbage collector root that is exposed by the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
 [<span data-ttu-id="2a794-119">COR_PRF_HIGH_MONITOR 列挙型</span><span class="sxs-lookup"><span data-stu-id="2a794-119">COR_PRF_HIGH_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)  
 <span data-ttu-id="2a794-120">:Seteventmask2 フラグを提供、 [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)ために、プロファイラーが指定する列挙体、 [icorprofilerinfo 5::seteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)メソッドの読み込み時にします。</span><span class="sxs-lookup"><span data-stu-id="2a794-120">Provides flags in addition to those found in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
 [<span data-ttu-id="2a794-121">COR_PRF_JIT_CACHE 列挙型</span><span class="sxs-lookup"><span data-stu-id="2a794-121">COR_PRF_JIT_CACHE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md)  
 <span data-ttu-id="2a794-122">キャッシュされている関数検索の結果を示します。</span><span class="sxs-lookup"><span data-stu-id="2a794-122">Indicates the result of a cached function search.</span></span>  
  
 [<span data-ttu-id="2a794-123">COR_PRF_MISC 列挙型</span><span class="sxs-lookup"><span data-stu-id="2a794-123">COR_PRF_MISC Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-misc-enumeration.md)  
 <span data-ttu-id="2a794-124">特殊な識別子を指定する定数値を含めます。</span><span class="sxs-lookup"><span data-stu-id="2a794-124">Contains constant values that specify special identifiers.</span></span>  
  
 [<span data-ttu-id="2a794-125">COR_PRF_MODULE_FLAGS 列挙型</span><span class="sxs-lookup"><span data-stu-id="2a794-125">COR_PRF_MODULE_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md)  
 <span data-ttu-id="2a794-126">モジュールのプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="2a794-126">Specifies the properties of a module.</span></span>  
  
 [<span data-ttu-id="2a794-127">COR_PRF_MONITOR 列挙型</span><span class="sxs-lookup"><span data-stu-id="2a794-127">COR_PRF_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 <span data-ttu-id="2a794-128">プロファイラーがサブスクライブしようとする動作、機能、またはイベントの指定で使用する値を含めます。</span><span class="sxs-lookup"><span data-stu-id="2a794-128">Contains values that are used to specify behavior, capabilities, or events to which the profiler wishes to subscribe.</span></span>  
  
 [<span data-ttu-id="2a794-129">COR_PRF_RUNTIME_TYPE 列挙型</span><span class="sxs-lookup"><span data-stu-id="2a794-129">COR_PRF_RUNTIME_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-runtime-type-enumeration.md)  
 <span data-ttu-id="2a794-130">共通言語ランタイムのバージョンを表す値を含めます。</span><span class="sxs-lookup"><span data-stu-id="2a794-130">Contains values that indicate the version of the common language runtime.</span></span>  
  
 [<span data-ttu-id="2a794-131">COR_PRF_SNAPSHOT_INFO 列挙型</span><span class="sxs-lookup"><span data-stu-id="2a794-131">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md)  
 <span data-ttu-id="2a794-132">プロファイラーの `StackSnapshotCallback` 関数への各呼び出しにおいて、スタック スナップショットでどのくらいのデータが返されるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="2a794-132">Specifies how much data to pass back with a stack snapshot in each call to the profiler's `StackSnapshotCallback` function.</span></span>  
  
 [<span data-ttu-id="2a794-133">COR_PRF_STATIC_TYPE 列挙型</span><span class="sxs-lookup"><span data-stu-id="2a794-133">COR_PRF_STATIC_TYPE Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md)  
 <span data-ttu-id="2a794-134">フィールドが静的であるかどうかを示し、静的な場合は、フィールドに適用される静的なクオリティを示します。</span><span class="sxs-lookup"><span data-stu-id="2a794-134">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span>  
  
 [<span data-ttu-id="2a794-135">COR_PRF_SUSPEND_REASON 列挙型</span><span class="sxs-lookup"><span data-stu-id="2a794-135">COR_PRF_SUSPEND_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md)  
 <span data-ttu-id="2a794-136">ランタイムが中断された理由を示します。</span><span class="sxs-lookup"><span data-stu-id="2a794-136">Indicates the reason that the runtime was suspended.</span></span>  
  
 [<span data-ttu-id="2a794-137">COR_PRF_TRANSITION_REASON 列挙型</span><span class="sxs-lookup"><span data-stu-id="2a794-137">COR_PRF_TRANSITION_REASON Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)  
 <span data-ttu-id="2a794-138">マネージ コードからアンマネージ コードへ、またはその逆の遷移の理由を示します。</span><span class="sxs-lookup"><span data-stu-id="2a794-138">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2a794-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="2a794-139">Related Sections</span></span>  
 [<span data-ttu-id="2a794-140">プロファイルの概要</span><span class="sxs-lookup"><span data-stu-id="2a794-140">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="2a794-141">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="2a794-141">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [<span data-ttu-id="2a794-142">プロファイリング グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="2a794-142">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [<span data-ttu-id="2a794-143">構造体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="2a794-143">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
