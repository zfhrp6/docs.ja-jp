---
title: "ICorProfilerFunctionControl::SetCodegenFlags メソッド"
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
- ICorProfilerFunctionControl.SetCodegenFlags
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags
helpviewer_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags method [.NET Framework profiling]
- SetCodegenFlags method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: a2d5daa5-b990-4ae5-bf2a-c0862fe58bd7
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9264e717da62c88b6f2f6eca262b5635fc928741
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a><span data-ttu-id="2311a-102">ICorProfilerFunctionControl::SetCodegenFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="2311a-102">ICorProfilerFunctionControl::SetCodegenFlags Method</span></span>
<span data-ttu-id="2311a-103">1 つまたは複数のフラグを設定、 [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)のイン-タイム (JIT) のコード生成を制御する列挙型の再コンパイルされた関数。</span><span class="sxs-lookup"><span data-stu-id="2311a-103">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2311a-104">構文</span><span class="sxs-lookup"><span data-stu-id="2311a-104">Syntax</span></span>  
  
```  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2311a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2311a-105">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="2311a-106">[in]1 つまたは複数のフラグ、 [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)列挙します。</span><span class="sxs-lookup"><span data-stu-id="2311a-106">[in] One or more flags from the [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2311a-107">コメント</span><span class="sxs-lookup"><span data-stu-id="2311a-107">Remarks</span></span>  
 <span data-ttu-id="2311a-108">プロファイラーがを介して、このインターフェイスのインスタンスを取得、 [icorprofilercallback 4::getrejitparameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="2311a-108">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="2311a-109">`SetCodegenFlags`再コンパイルされた関数のコード生成を制御する、プロファイラーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="2311a-109">`SetCodegenFlags` allows the profiler to control the code generation for the recompiled function.</span></span> <span data-ttu-id="2311a-110">他のすべての JIT 再コンパイル パラメーターと同様、コード生成フラグは、関数のすべてのインスタンスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="2311a-110">As with all other JIT recompilation parameters, the code generation flags apply to all instances of the function.</span></span>  
  
 <span data-ttu-id="2311a-111">JIT コンパイラでは、関数をコンパイルするときに、他のソースで指定されたその他のフラグと共に、これらのコンパイル フラグと見なします。</span><span class="sxs-lookup"><span data-stu-id="2311a-111">The JIT compiler considers these compilation flags, along with other flags specified by other sources, when compiling a function.</span></span>  <span data-ttu-id="2311a-112">他のソースには、デバッガーが含まれます、スタートアップ時に、プロファイラーによってグローバル フラグ設定を使用して、 [icorprofilerinfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)メソッド (値を持つ`COR_PRF_DISABLE_INLINING`と`COR_PRF_DISABLE_OPTIMIZATIONS`)、およびプロファイラーの[。Icorprofilercallback::jitinlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="2311a-112">The other sources include the debugger, global flags set by the profiler on startup by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method (with the values `COR_PRF_DISABLE_INLINING` and `COR_PRF_DISABLE_OPTIMIZATIONS`), and the profiler’s [ICorProfilerCallback::JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) callback.</span></span>  <span data-ttu-id="2311a-113">JIT コンパイラでは、最低限の最適化を要求するソースを優先します。</span><span class="sxs-lookup"><span data-stu-id="2311a-113">The JIT compiler gives precedence to a source that requests the least amount of optimizing.</span></span>  <span data-ttu-id="2311a-114">たとえば、プロファイラーが指定されている場合`COR_PRF_DISABLE_INLINING`スタートアップ時が指定されていませんが、`COR_PRF_CODEGEN_DISABLE_INLINING`で、 [icorprofilerfunctioncontrol::setcodegenflags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)コールバック、インライン展開が無効のままです。</span><span class="sxs-lookup"><span data-stu-id="2311a-114">For example, if the profiler specifies `COR_PRF_DISABLE_INLINING` on startup, but does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) callback, inlining is still disabled.</span></span>  <span data-ttu-id="2311a-115">同様に、プロファイラーが指定されていない場合`COR_PRF_CODEGEN_DISABLE_INLINING`で`SetCodegenFlags`を使用してインライン展開し、無効、 [icorprofilercallback::jitinlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md)コールバック、インライン展開が無効になっています。</span><span class="sxs-lookup"><span data-stu-id="2311a-115">Similarly, if the profiler does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in `SetCodegenFlags`, but then disables inlining by using the [ICorProfilerCallback::JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) callback, inlining is disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2311a-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="2311a-116">Requirements</span></span>  
 <span data-ttu-id="2311a-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2311a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2311a-118">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2311a-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2311a-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2311a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2311a-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2311a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2311a-121">参照</span><span class="sxs-lookup"><span data-stu-id="2311a-121">See Also</span></span>  
 [<span data-ttu-id="2311a-122">ICorProfilerFunctionControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2311a-122">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
