---
title: "ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 メソッド"
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
- ICorProfilerInfo2.SetEnterLeaveFunctionHooks2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
helpviewer_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
- SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
ms.assetid: 3c26b3e7-f72b-48a5-bf8c-edc122523a4b
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0c460cfd24a83ca2a6c75e061b7a797c8f455bc1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a><span data-ttu-id="68725-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 メソッド</span><span class="sxs-lookup"><span data-stu-id="68725-102">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Method</span></span>
<span data-ttu-id="68725-103">「の入力」、「のまま」、およびマネージ関数の"tailcall"フックの更新されたバージョンで呼び出されるプロファイラー実装関数を指定します。</span><span class="sxs-lookup"><span data-stu-id="68725-103">Specifies profiler-implemented functions to be called on the updated versions of the "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68725-104">構文</span><span class="sxs-lookup"><span data-stu-id="68725-104">Syntax</span></span>  
  
```  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="68725-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="68725-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="68725-106">[in]として使用する実装へのポインター、 [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="68725-106">[in] A pointer to the implementation to be used as the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="68725-107">[in]として使用する実装へのポインター、 [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="68725-107">[in] A pointer to the implementation to be used as the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="68725-108">[in]として使用する実装へのポインター、 [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="68725-108">[in] A pointer to the implementation to be used as the [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68725-109">コメント</span><span class="sxs-lookup"><span data-stu-id="68725-109">Remarks</span></span>  
 <span data-ttu-id="68725-110">`SetEnterLeaveFunctionHooks2`メソッドがに似ていますが、 [icorprofilerinfo::setenterleavefunctionhooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="68725-110">The `SetEnterLeaveFunctionHooks2` method is similar to the [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) method.</span></span> <span data-ttu-id="68725-111">前者を使用して、enter/のままにして/tailcall コールバックの前のバージョンとして使用する関数を指定する入力/のままにして/tailcall コールバック、および後者の新しいバージョンとして使用する関数を指定します。</span><span class="sxs-lookup"><span data-stu-id="68725-111">Use the former to specify functions to be used as the newer versions of the enter/leave/tailcall callbacks, and the latter to specify functions to be used as the older versions of the enter/leave/tailcall callbacks.</span></span>  
  
 <span data-ttu-id="68725-112">コールバックの 1 つだけのセットは、一度にアクティブな可能性があります。</span><span class="sxs-lookup"><span data-stu-id="68725-112">Only one set of callbacks may be active at a time.</span></span> <span data-ttu-id="68725-113">したがって、プロファイラーは、両方を呼び出す場合`ICorProfilerInfo::SetEnterLeaveFunctionHooks`と`SetEnterLeaveFunctionHooks2`、`SetEnterLeaveFunctionHooks2`を使用します。</span><span class="sxs-lookup"><span data-stu-id="68725-113">Thus, if a profiler calls both `ICorProfilerInfo::SetEnterLeaveFunctionHooks` and `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` is used.</span></span>  
  
 <span data-ttu-id="68725-114">`SetEnterLeaveFunctionHooks2`メソッドは、プロファイラーからのみ呼び出すことがあります[icorprofilercallback::initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="68725-114">The `SetEnterLeaveFunctionHooks2` method may be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68725-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="68725-115">Requirements</span></span>  
 <span data-ttu-id="68725-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="68725-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68725-117">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="68725-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="68725-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68725-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68725-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68725-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68725-120">参照</span><span class="sxs-lookup"><span data-stu-id="68725-120">See Also</span></span>  
 [<span data-ttu-id="68725-121">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="68725-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="68725-122">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="68725-122">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
