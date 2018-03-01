---
title: "FunctionIDMapper2 関数"
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
- FunctionIDMapper2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper2
helpviewer_keywords:
- FunctionIDMapper2 function [.NET Framework profiling]
ms.assetid: 466ad51b-8f0c-41d9-81f7-371aac3374cb
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 09aac1b9046153f56b591ac1815365ea4f90e4ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="functionidmapper2-function"></a><span data-ttu-id="530c3-102">FunctionIDMapper2 関数</span><span class="sxs-lookup"><span data-stu-id="530c3-102">FunctionIDMapper2 Function</span></span>
<span data-ttu-id="530c3-103">関数の特定の識別子が可能性がありますで使用される代替 ID に再割り当てされることをプロファイラーに通知、 [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)、 [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)、および[FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)、または[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)、 [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)、および[FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)その関数のコールバック。</span><span class="sxs-lookup"><span data-stu-id="530c3-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), or[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) callbacks for that function.</span></span> <span data-ttu-id="530c3-104">また `FunctionIDMapper2` により、プロファイラーはその関数のコールバックを受信するかどうかを示すことができます。</span><span class="sxs-lookup"><span data-stu-id="530c3-104">`FunctionIDMapper2` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="530c3-105">構文</span><span class="sxs-lookup"><span data-stu-id="530c3-105">Syntax</span></span>  
  
```  
UINT_PTR __stdcall FunctionIDMapper2 (  
    [in]  FunctionID  funcId,  
    [in]  void * clientData,  
    [out] BOOL       *pbHookFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="530c3-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="530c3-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="530c3-107">[入力] 再割り当てされる関数識別子。</span><span class="sxs-lookup"><span data-stu-id="530c3-107">[in] The function identifier to be remapped.</span></span>  
  
 `clientData`  
 <span data-ttu-id="530c3-108">[入力] ランタイム間のあいまいさを解消するために使用されるデータへのポインター。</span><span class="sxs-lookup"><span data-stu-id="530c3-108">[in] A pointer to data that is used to disambiguate among runtimes.</span></span>  
  
 `pbHookFunction`  
 <span data-ttu-id="530c3-109">[出力] 出力プロファイラーが `FunctionEnter3`、`FunctionLeave3`、`FunctionTailcall3`、または  `FunctionEnter3WithInfo`、`FunctionLeave3WithInfo`、`FunctionTailcall3WithInfo` の各コールバックを受信する場合は `true` に設定される値へのポインター。それ以外の場合、この値は  `false` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="530c3-109">[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter3`, `FunctionLeave3`, and `FunctionTailcall3`, or `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`, and `FunctionTailcall3WithInfo` callbacks; otherwise, it sets this value to `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="530c3-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="530c3-110">Return Value</span></span>  
 <span data-ttu-id="530c3-111">プロファイラーは、実行エンジンが代替関数識別子として使用する値を返します。</span><span class="sxs-lookup"><span data-stu-id="530c3-111">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="530c3-112">`false` で `pbHookFunction` を返さない限り、戻り値を null にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="530c3-112">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="530c3-113">これ以外の状況で戻り値を null にすると、プロセスの中止など、予測できない結果が発生します。</span><span class="sxs-lookup"><span data-stu-id="530c3-113">Otherwise, a null return value produces unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="530c3-114">コメント</span><span class="sxs-lookup"><span data-stu-id="530c3-114">Remarks</span></span>  
 <span data-ttu-id="530c3-115">このメソッドによって拡張、 [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)クライアント データを渡すために使用する追加パラメーターを持つ関数です。</span><span class="sxs-lookup"><span data-stu-id="530c3-115">This method extends the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function with an additional parameter that is used to pass client data.</span></span> <span data-ttu-id="530c3-116">クライアント データを使用すると、ランタイム間のあいまいさが解消されます。</span><span class="sxs-lookup"><span data-stu-id="530c3-116">The client data is used to disambiguate among runtimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="530c3-117">必要条件</span><span class="sxs-lookup"><span data-stu-id="530c3-117">Requirements</span></span>  
 <span data-ttu-id="530c3-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="530c3-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="530c3-119">**ヘッダー:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="530c3-119">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="530c3-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="530c3-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="530c3-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="530c3-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="530c3-122">参照</span><span class="sxs-lookup"><span data-stu-id="530c3-122">See Also</span></span>  
 [<span data-ttu-id="530c3-123">Icorprofilerinfo::setfunctionidmapper</span><span class="sxs-lookup"><span data-stu-id="530c3-123">ICorProfilerInfo::SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="530c3-124">Icorprofilerinfo 3::setfunctionidmapper2</span><span class="sxs-lookup"><span data-stu-id="530c3-124">ICorProfilerInfo3::SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [<span data-ttu-id="530c3-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="530c3-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="530c3-126">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="530c3-126">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="530c3-127">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="530c3-127">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="530c3-128">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="530c3-128">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="530c3-129">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="530c3-129">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="530c3-130">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="530c3-130">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="530c3-131">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="530c3-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
