---
title: "ICorProfilerInfo::SetFunctionIDMapper メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.SetFunctionIDMapper
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::SetFunctionIDMapper
helpviewer_keywords:
- ICorProfilerInfo::SetFunctionIDMapper method [.NET Framework profiling]
- SetFunctionIDMapper method [.NET Framework profiling]
ms.assetid: 1a6e5dae-d366-4497-9c02-7b5b1f43f9ec
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7caaecdbd73a183e2d188a2ab9e799c5eb3efaca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfosetfunctionidmapper-method"></a><span data-ttu-id="0d8ff-102">ICorProfilerInfo::SetFunctionIDMapper メソッド</span><span class="sxs-lookup"><span data-stu-id="0d8ff-102">ICorProfilerInfo::SetFunctionIDMapper Method</span></span>
<span data-ttu-id="0d8ff-103">`FunctionID` 値を代替値に対応付けるために呼び出すプロファイラー実装関数を指定します。代替値は、プロファイラーの関数の開始フックと終了フックに渡されます。</span><span class="sxs-lookup"><span data-stu-id="0d8ff-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d8ff-104">構文</span><span class="sxs-lookup"><span data-stu-id="0d8ff-104">Syntax</span></span>  
  
```  
HRESULT SetFunctionIDMapper (  
    [in] FunctionIDMapper *pFunc);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0d8ff-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0d8ff-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="0d8ff-106">[in]ポインター、 [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)実装にマップすると呼び出される、`FunctionID`値を代替値にします。</span><span class="sxs-lookup"><span data-stu-id="0d8ff-106">[in] A pointer to the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d8ff-107">コメント</span><span class="sxs-lookup"><span data-stu-id="0d8ff-107">Remarks</span></span>  
 <span data-ttu-id="0d8ff-108">その他の方法、`FunctionID`プロファイラーの関数の開始フックと終了フックに渡される値 ([FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)、 [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)、および[FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md))指定されている、 [icorprofilerinfo 2::setenterleavefunctionhooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="0d8ff-108">The alternatives for the `FunctionID` values will be passed to the profiler's function entry/exit hooks ([FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), and [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)) that are specified by the [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) method.</span></span>  
  
 <span data-ttu-id="0d8ff-109">`FunctionIDMapper` 1 回だけ設定することができに設定することをお勧めしますが、 [icorprofilercallback::initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="0d8ff-109">The `FunctionIDMapper` can be set only once and it is recommended that you set it in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d8ff-110">要件</span><span class="sxs-lookup"><span data-stu-id="0d8ff-110">Requirements</span></span>  
 <span data-ttu-id="0d8ff-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0d8ff-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d8ff-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0d8ff-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0d8ff-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d8ff-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d8ff-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d8ff-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d8ff-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="0d8ff-115">See Also</span></span>  
 [<span data-ttu-id="0d8ff-116">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0d8ff-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
