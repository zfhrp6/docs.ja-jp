---
title: "グローバル静的関数のプロファイル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- global static functions [.NET Framework profiling]
- profiling global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], profiling
ms.assetid: 08a13a57-dc49-488d-b937-31e3051fda97
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 66f22557dd6020ff5040d5aaf76cb12e9ae9965c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="profiling-global-static-functions"></a><span data-ttu-id="e5bef-102">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="e5bef-102">Profiling Global Static Functions</span></span>
<span data-ttu-id="e5bef-103">このセクションでは、プロファイル API で使用されるアンマネージ API 関数について説明します。</span><span class="sxs-lookup"><span data-stu-id="e5bef-103">This section describes the unmanaged API functions that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e5bef-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="e5bef-104">In This Section</span></span>  
  
## <a name="net-framework-version-1-profiling-functions"></a><span data-ttu-id="e5bef-105">.NET framework バージョン 1 プロファイリング関数</span><span class="sxs-lookup"><span data-stu-id="e5bef-105">.NET Framework version 1 Profiling Functions</span></span>  
 [<span data-ttu-id="e5bef-106">FunctionEnter 関数</span><span class="sxs-lookup"><span data-stu-id="e5bef-106">FunctionEnter Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md)  
 <span data-ttu-id="e5bef-107">コントロールが関数に渡されることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e5bef-107">Notifies the profiler that control is being passed to a function.</span></span> <span data-ttu-id="e5bef-108">.NET Framework 2.0 で廃止されました。</span><span class="sxs-lookup"><span data-stu-id="e5bef-108">Deprecated in the .NET Framework 2.0.</span></span>  
  
 [<span data-ttu-id="e5bef-109">FunctionLeave 関数</span><span class="sxs-lookup"><span data-stu-id="e5bef-109">FunctionLeave Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)  
 <span data-ttu-id="e5bef-110">関数が呼び出し元に戻るには約ことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e5bef-110">Notifies the profiler that a function is about to return to the caller.</span></span> <span data-ttu-id="e5bef-111">.NET Framework 2.0 で廃止されました。</span><span class="sxs-lookup"><span data-stu-id="e5bef-111">Deprecated in the .NET Framework 2.0.</span></span>  
  
 [<span data-ttu-id="e5bef-112">FunctionTailcall 関数</span><span class="sxs-lookup"><span data-stu-id="e5bef-112">FunctionTailcall Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md)  
 <span data-ttu-id="e5bef-113">現在実行中の関数は、別の関数の末尾呼び出しを実行しようとして、プロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e5bef-113">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span> <span data-ttu-id="e5bef-114">.NET Framework 2.0 で廃止されました。</span><span class="sxs-lookup"><span data-stu-id="e5bef-114">Deprecated in the .NET Framework 2.0.</span></span>  
  
## <a name="net-framework-version-2-profiling-functions"></a><span data-ttu-id="e5bef-115">.NET framework バージョン 2 プロファイリング関数</span><span class="sxs-lookup"><span data-stu-id="e5bef-115">.NET Framework version 2 Profiling Functions</span></span>  
 [<span data-ttu-id="e5bef-116">FunctionIDMapper 関数</span><span class="sxs-lookup"><span data-stu-id="e5bef-116">FunctionIDMapper Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)  
 <span data-ttu-id="e5bef-117">関数の特定の識別子が可能性がありますで使用される代替 ID に再割り当てされることをプロファイラーに通知、 [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)、 [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)、および[FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)その関数のコールバック。</span><span class="sxs-lookup"><span data-stu-id="e5bef-117">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), and [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="e5bef-118">プロファイラーがその関数のコールバックを受信するかどうかを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="e5bef-118">Also enables the profiler to indicate whether it wants to receive callbacks for that function</span></span>  
  
 [<span data-ttu-id="e5bef-119">FunctionEnter2 関数</span><span class="sxs-lookup"><span data-stu-id="e5bef-119">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 <span data-ttu-id="e5bef-120">コントロールが関数に渡されると、フレームと関数の引数の履歴に関する情報を提供をプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e5bef-120">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="e5bef-121">非推奨、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="e5bef-121">Deprecated in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
 [<span data-ttu-id="e5bef-122">FunctionLeave2 関数</span><span class="sxs-lookup"><span data-stu-id="e5bef-122">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 <span data-ttu-id="e5bef-123">プロファイラーに通知関数が呼び出し元に戻るには、し、スタック フレームと関数の戻り値に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="e5bef-123">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span> <span data-ttu-id="e5bef-124">非推奨、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="e5bef-124">Deprecated in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
 [<span data-ttu-id="e5bef-125">FunctionTailcall2 関数</span><span class="sxs-lookup"><span data-stu-id="e5bef-125">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 <span data-ttu-id="e5bef-126">現在実行中の関数は、別の関数の末尾呼び出しを実行する直前と、スタック フレームに関する情報を提供をプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e5bef-126">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span> <span data-ttu-id="e5bef-127">非推奨、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="e5bef-127">Deprecated in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
 [<span data-ttu-id="e5bef-128">StackSnapshotCallback 関数</span><span class="sxs-lookup"><span data-stu-id="e5bef-128">StackSnapshotCallback Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md)  
 <span data-ttu-id="e5bef-129">によって開始されるスタック ウォーク中のスタックの各マネージ フレームとアンマネージのフレームの各実行に関する情報を使用してプロファイラーを提供、 [icorprofilerinfo 2::dostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="e5bef-129">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="net-framework-version-4-profiling-functions"></a><span data-ttu-id="e5bef-130">.NET framework version 4 プロファイリング関数</span><span class="sxs-lookup"><span data-stu-id="e5bef-130">.NET Framework version 4 Profiling Functions</span></span>  
 [<span data-ttu-id="e5bef-131">FunctionIDMapper2 関数</span><span class="sxs-lookup"><span data-stu-id="e5bef-131">FunctionIDMapper2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)  
 <span data-ttu-id="e5bef-132">関数の特定の識別子が可能性がありますで使用される代替 ID に再割り当てされることをプロファイラーに通知、 [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)、 [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)、および[FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)、または[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)、 [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)、および[FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)その関数のコールバック。</span><span class="sxs-lookup"><span data-stu-id="e5bef-132">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), or[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) callbacks for that function.</span></span> <span data-ttu-id="e5bef-133">プロファイラーがその関数のコールバックを受信するかどうかを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="e5bef-133">Also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
 <span data-ttu-id="e5bef-134">`FunctionIDMapper2`拡張、 [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)で機能、`clientData`プロファイラーをランタイムの間で区別するために使用するパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="e5bef-134">`FunctionIDMapper2` extends the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function with a `clientData` parameter, which profilers may use to disambiguate among runtimes.</span></span>  
  
 [<span data-ttu-id="e5bef-135">FunctionEnter3 関数</span><span class="sxs-lookup"><span data-stu-id="e5bef-135">FunctionEnter3 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 <span data-ttu-id="e5bef-136">コントロールが関数に渡されることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e5bef-136">Notifies the profiler that control is being passed to a function.</span></span>  
  
 [<span data-ttu-id="e5bef-137">FunctionEnter3WithInfo 関数</span><span class="sxs-lookup"><span data-stu-id="e5bef-137">FunctionEnter3WithInfo Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 <span data-ttu-id="e5bef-138">コントロールが、関数に渡されることをプロファイラーに通知しに渡すことができるハンドルを提供[icorprofilerinfo 3::getfunctionenter3info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)スタック フレームと関数の引数を取得します。</span><span class="sxs-lookup"><span data-stu-id="e5bef-138">Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionEnter3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.</span></span>  
  
 [<span data-ttu-id="e5bef-139">FunctionLeave3 関数</span><span class="sxs-lookup"><span data-stu-id="e5bef-139">FunctionLeave3 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 <span data-ttu-id="e5bef-140">コントロールが関数から返されていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e5bef-140">Notifies the profiler that control is being returned from a function.</span></span>  
  
 [<span data-ttu-id="e5bef-141">FunctionLeave3WithInfo 関数</span><span class="sxs-lookup"><span data-stu-id="e5bef-141">FunctionLeave3WithInfo Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 <span data-ttu-id="e5bef-142">コントロールが、関数から返されていることをプロファイラーに通知しに渡すことができるハンドルを提供[icorprofilerinfo 3::getfunctionleave3info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)スタック フレームおよび戻り値を取得します。</span><span class="sxs-lookup"><span data-stu-id="e5bef-142">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionLeave3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span></span>  
  
 [<span data-ttu-id="e5bef-143">FunctionTailcall3 関数</span><span class="sxs-lookup"><span data-stu-id="e5bef-143">FunctionTailcall3 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 <span data-ttu-id="e5bef-144">現在実行中の関数は、別の関数の末尾呼び出しを実行しようとして、プロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e5bef-144">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
 [<span data-ttu-id="e5bef-145">FunctionTailcall3WithInfo 関数</span><span class="sxs-lookup"><span data-stu-id="e5bef-145">FunctionTailcall3WithInfo Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 <span data-ttu-id="e5bef-146">現在実行中の関数は、別の関数の末尾呼び出しを実行しようとして、プロファイラーに通知しに渡すことができるハンドルを提供[icorprofilerinfo 3::getfunctiontailcall3info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md)スタック フレームを取得します。</span><span class="sxs-lookup"><span data-stu-id="e5bef-146">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionTailcall3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e5bef-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="e5bef-147">Related Sections</span></span>  
 [<span data-ttu-id="e5bef-148">プロファイルの概要</span><span class="sxs-lookup"><span data-stu-id="e5bef-148">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [<span data-ttu-id="e5bef-149">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="e5bef-149">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [<span data-ttu-id="e5bef-150">列挙型のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="e5bef-150">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [<span data-ttu-id="e5bef-151">構造体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="e5bef-151">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
