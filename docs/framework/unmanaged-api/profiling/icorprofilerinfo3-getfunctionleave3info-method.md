---
title: ICorProfilerInfo3::GetFunctionLeave3Info メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionLeave3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionLeave3Info
helpviewer_keywords:
- GetFunctionLeave3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionLeave3Info method [.NET Framework profiling]
ms.assetid: df7083d2-fd43-44c7-9ce5-912c25cef0ff
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 70fdc548c02015f0950f009abe94652795cba568
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459797"
---
# <a name="icorprofilerinfo3getfunctionleave3info-method"></a><span data-ttu-id="3835e-102">ICorProfilerInfo3::GetFunctionLeave3Info メソッド</span><span class="sxs-lookup"><span data-stu-id="3835e-102">ICorProfilerInfo3::GetFunctionLeave3Info Method</span></span>
<span data-ttu-id="3835e-103">スタック フレームとによってプロファイラーに報告される関数の戻り値を提供、 [FunctionLeave3WithInfo 関数](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)関数。</span><span class="sxs-lookup"><span data-stu-id="3835e-103">Provides the stack frame and return value of the function that is being reported to the profiler by the [FunctionLeave3WithInfo function](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) function.</span></span> <span data-ttu-id="3835e-104">このメソッドは、`FunctionLeave3WithInfo` コールバック中にのみ呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="3835e-104">This method can be called only during the `FunctionLeave3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3835e-105">構文</span><span class="sxs-lookup"><span data-stu-id="3835e-105">Syntax</span></span>  
  
```  
HRESULT GetFunctionLeave3Info(  
            [in]  FunctionID functionId,  
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [out] COR_PRF_FUNCTION_ARGUMENT_RANGE *pRetvalRange);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3835e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3835e-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="3835e-107">[in]`FunctionID`を返す関数。</span><span class="sxs-lookup"><span data-stu-id="3835e-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="3835e-108">[in] 特定のスタック フレームに関する情報を表す不透明ハンドル。</span><span class="sxs-lookup"><span data-stu-id="3835e-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="3835e-109">プロファイラーを提供する必要があります同じ`eltInfo`によってプロファイラーに指定されている、 [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)関数。</span><span class="sxs-lookup"><span data-stu-id="3835e-109">The profiler should provide the same `eltInfo` that was given to the profiler by the [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="3835e-110">[out] 特定のスタック フレームに関するジェネリック情報を表す不透明ハンドル。</span><span class="sxs-lookup"><span data-stu-id="3835e-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="3835e-111">このハンドルは、プロファイラーが `FunctionLeave3WithInfo` メソッドを呼び出した `GetFunctionLeave3Info` コールバック内でのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="3835e-111">This handle is valid only during the `FunctionLeave3WithInfo` callback in which the profiler called the `GetFunctionLeave3Info` method.</span></span>  
  
 `pRetvalRange`  
 <span data-ttu-id="3835e-112">[out]ポインター、 [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md)関数から返される値を格納する構造体。</span><span class="sxs-lookup"><span data-stu-id="3835e-112">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structure that contains the value that is returned from the function.</span></span> <span data-ttu-id="3835e-113">戻り値の情報にアクセスする、`COR_PRF_ENABLE_FUNCTION_RETVAL`フラグを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3835e-113">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="3835e-114">プロファイラーは、使用、 [icorprofilerinfo::seteventmask メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)イベントのフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="3835e-114">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3835e-115">コメント</span><span class="sxs-lookup"><span data-stu-id="3835e-115">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3835e-116">要件</span><span class="sxs-lookup"><span data-stu-id="3835e-116">Requirements</span></span>  
 <span data-ttu-id="3835e-117">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3835e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3835e-118">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3835e-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3835e-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3835e-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3835e-120">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3835e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3835e-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="3835e-121">See Also</span></span>  
 [<span data-ttu-id="3835e-122">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="3835e-122">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="3835e-123">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="3835e-123">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="3835e-124">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="3835e-124">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="3835e-125">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3835e-125">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="3835e-126">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="3835e-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="3835e-127">プロファイル</span><span class="sxs-lookup"><span data-stu-id="3835e-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
