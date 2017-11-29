---
title: "ICorProfilerInfo3::GetFunctionTailcall3Info メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.GetFunctionTailcall3Info Method
api_location: Mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::GetFunctionTailcall3Info
helpviewer_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info method [.NET Framework profiling]
- GetFunctionTailcall3Info method [.NET Framework profiling]
ms.assetid: afdb5ac9-5bf5-4b91-b7cb-f81db23d7da3
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: aae55a9e183c9e013603218ba217be79b2425e46
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a><span data-ttu-id="5ee58-102">ICorProfilerInfo3::GetFunctionTailcall3Info メソッド</span><span class="sxs-lookup"><span data-stu-id="5ee58-102">ICorProfilerInfo3::GetFunctionTailcall3Info Method</span></span>
<span data-ttu-id="5ee58-103">によってプロファイラーに報告される関数のスタック フレームを提供、 [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)関数。</span><span class="sxs-lookup"><span data-stu-id="5ee58-103">Provides the stack frame of the function that is being reported to the profiler by the [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) function.</span></span> <span data-ttu-id="5ee58-104">このメソッドは、`FunctionTailcall3WithInfo` コールバック中にのみ呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="5ee58-104">This method can be called only during the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ee58-105">構文</span><span class="sxs-lookup"><span data-stu-id="5ee58-105">Syntax</span></span>  
  
```  
HRESULT GetFunctionTailcall3Info(   
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5ee58-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5ee58-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="5ee58-107">[in]`FunctionID`を返す関数。</span><span class="sxs-lookup"><span data-stu-id="5ee58-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="5ee58-108">[in] 特定のスタック フレームに関する情報を表す不透明ハンドル。</span><span class="sxs-lookup"><span data-stu-id="5ee58-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="5ee58-109">プロファイラーを提供する必要があります同じ`eltInfo`によってプロファイラーに指定されている、`FunctionTailcall3WithInfo`関数。</span><span class="sxs-lookup"><span data-stu-id="5ee58-109">The profiler should provide the same `eltInfo` that was given to the profiler by the `FunctionTailcall3WithInfo` function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="5ee58-110">[out] 特定のスタック フレームに関するジェネリック情報を表す不透明ハンドル。</span><span class="sxs-lookup"><span data-stu-id="5ee58-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="5ee58-111">このハンドルは、プロファイラーが `FunctionTailcall3WithInfo` メソッドを呼び出した `GetFunctionTailcall3Info` コールバック内でのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="5ee58-111">This handle is valid only during the `FunctionTailcall3WithInfo` callback in which the profiler called the `GetFunctionTailcall3Info` method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ee58-112">コメント</span><span class="sxs-lookup"><span data-stu-id="5ee58-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ee58-113">要件</span><span class="sxs-lookup"><span data-stu-id="5ee58-113">Requirements</span></span>  
 <span data-ttu-id="5ee58-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5ee58-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ee58-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5ee58-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5ee58-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ee58-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ee58-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ee58-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ee58-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ee58-118">See Also</span></span>  
 [<span data-ttu-id="5ee58-119">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="5ee58-119">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="5ee58-120">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="5ee58-120">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="5ee58-121">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="5ee58-121">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="5ee58-122">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5ee58-122">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="5ee58-123">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="5ee58-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="5ee58-124">プロファイル</span><span class="sxs-lookup"><span data-stu-id="5ee58-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
