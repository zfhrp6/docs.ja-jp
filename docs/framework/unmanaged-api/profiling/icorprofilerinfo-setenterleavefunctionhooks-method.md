---
title: "ICorProfilerInfo::SetEnterLeaveFunctionHooks メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.SetEnterLeaveFunctionHooks
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::SetEnterLeaveFunctionHooks
helpviewer_keywords:
- SetEnterLeaveFunctionHooks method [.NET Framework profiling]
- ICorProfilerInfo::SetEnterLeaveFunctionHooks method [.NET Framework profiling]
ms.assetid: 72399636-c219-4ffd-8ac8-39432c9d4641
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c2bf897ce41e2d9a8b4c7b9eeb4053ea0e9ad951
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a><span data-ttu-id="b0832-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks メソッド</span><span class="sxs-lookup"><span data-stu-id="b0832-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks Method</span></span>
<span data-ttu-id="b0832-103">「の入力」、「のまま」、およびマネージ関数の"tailcall"フックで呼び出されるプロファイラー実装関数を指定します。</span><span class="sxs-lookup"><span data-stu-id="b0832-103">Specifies profiler-implemented functions to be called on "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0832-104">構文</span><span class="sxs-lookup"><span data-stu-id="b0832-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b0832-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b0832-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="b0832-106">[in]として使用する実装へのポインター、 [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="b0832-106">[in] A pointer to the implementation to be used as the [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="b0832-107">[in]として使用する実装へのポインター、 [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="b0832-107">[in] A pointer to the implementation to be used as the [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="b0832-108">[in]として使用する実装へのポインター、 [FunctionTailcall](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="b0832-108">[in] A pointer to the implementation to be used as the [FunctionTailcall](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0832-109">コメント</span><span class="sxs-lookup"><span data-stu-id="b0832-109">Remarks</span></span>  
 <span data-ttu-id="b0832-110">.NET framework version 1.0 では、各関数ポインターは、その対応するコールバックを無効にする null でもかまいません。</span><span class="sxs-lookup"><span data-stu-id="b0832-110">In the .NET Framework version 1.0, each function pointer can be null to disable that corresponding callback.</span></span>  
  
 <span data-ttu-id="b0832-111">一度にアクティブにできるコールバックのセットを 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="b0832-111">Only one set of callbacks can be active at a time.</span></span> <span data-ttu-id="b0832-112">したがって、プロファイラーは、両方を呼び出す場合`SetEnterLeaveFunctionHooks`と[icorprofilerinfo 2::setenterleavefunctionhooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)、し`SetEnterLeaveFunctionHooks2`が優先されます。</span><span class="sxs-lookup"><span data-stu-id="b0832-112">Thus, if a profiler calls both `SetEnterLeaveFunctionHooks` and [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), then `SetEnterLeaveFunctionHooks2` takes precedence.</span></span>  
  
 <span data-ttu-id="b0832-113">`SetEnterLeaveFunctionHooks`メソッドは、プロファイラーからのみ呼び出すことが[icorprofilercallback::initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="b0832-113">The `SetEnterLeaveFunctionHooks` method can be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0832-114">要件</span><span class="sxs-lookup"><span data-stu-id="b0832-114">Requirements</span></span>  
 <span data-ttu-id="b0832-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b0832-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0832-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b0832-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b0832-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0832-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0832-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0832-118">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0832-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="b0832-119">See Also</span></span>  
 [<span data-ttu-id="b0832-120">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b0832-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
