---
title: "ICorProfilerCallback4::ReJITError メソッド"
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
- ICorProfilerCallback4.ReJITError
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITError
helpviewer_keywords:
- ReJITError method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITError method [.NET Framework profiling]
ms.assetid: d7888aa9-dfaa-420f-9f99-e06ab35ca482
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c746d0f7a6be96f95f1a051e22de0ad1bd2d2269
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback4rejiterror-method"></a><span data-ttu-id="b45c0-102">ICorProfilerCallback4::ReJITError メソッド</span><span class="sxs-lookup"><span data-stu-id="b45c0-102">ICorProfilerCallback4::ReJITError Method</span></span>
<span data-ttu-id="b45c0-103">・ イン タイム (JIT) コンパイラが再コンパイル プロセスでエラーが発生したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="b45c0-103">Notifies the profiler that the just-in-time (JIT) compiler encountered an error in the recompilation process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b45c0-104">構文</span><span class="sxs-lookup"><span data-stu-id="b45c0-104">Syntax</span></span>  
  
```  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b45c0-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b45c0-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="b45c0-106">[in]`ModuleID`再コンパイルが失敗した試行が行われる。</span><span class="sxs-lookup"><span data-stu-id="b45c0-106">[in] The `ModuleID` in which the failed recompilation attempt was made.</span></span>  
  
 `methodId`  
 <span data-ttu-id="b45c0-107">[in]`MethodDef`再コンパイルが失敗した試行が行われたメソッドの。</span><span class="sxs-lookup"><span data-stu-id="b45c0-107">[in] The `MethodDef` of the method on which the failed recompilation attempt was made.</span></span>  
  
 `functionId`  
 <span data-ttu-id="b45c0-108">[in]再コンパイルまたは用にマークの再コンパイルされている関数のインスタンス。</span><span class="sxs-lookup"><span data-stu-id="b45c0-108">[in] The function instance that is being recompiled or marked for recompilation.</span></span> <span data-ttu-id="b45c0-109">この値は、 `NULL` (たとえば、プロファイラーには、再コンパイルするメソッドを無効なメタデータ トークンが指定された) 場合、インスタンス化ごとにではなくメソッドごとに障害が発生したかどうか。</span><span class="sxs-lookup"><span data-stu-id="b45c0-109">This value may be `NULL` if the failure occurred on a per-method basis instead of a per-instantiation basis (for example, if the profiler specified an invalid metadata token for the method to be recompiled).</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="b45c0-110">[in]エラーの性質を示す HRESULT。</span><span class="sxs-lookup"><span data-stu-id="b45c0-110">[in] An HRESULT that indicates the nature of the failure.</span></span> <span data-ttu-id="b45c0-111">値の一覧については、状態 HRESULT」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b45c0-111">See the Status HRESULTS section for a list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b45c0-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="b45c0-112">Return Value</span></span>  
 <span data-ttu-id="b45c0-113">このコールバックからの戻り値は無視されます。</span><span class="sxs-lookup"><span data-stu-id="b45c0-113">Return values from this callback are ignored.</span></span>  
  
## <a name="status-hresults"></a><span data-ttu-id="b45c0-114">状態 HRESULT</span><span class="sxs-lookup"><span data-stu-id="b45c0-114">Status HRESULTS</span></span>  
  
|<span data-ttu-id="b45c0-115">状態配列 HRESULT</span><span class="sxs-lookup"><span data-stu-id="b45c0-115">Status array HRESULT</span></span>|<span data-ttu-id="b45c0-116">説明</span><span class="sxs-lookup"><span data-stu-id="b45c0-116">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="b45c0-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b45c0-117">E_INVALIDARG</span></span>|<span data-ttu-id="b45c0-118">`moduleID`または`methodDef`トークンが`NULL`です。</span><span class="sxs-lookup"><span data-stu-id="b45c0-118">The `moduleID` or `methodDef` token is `NULL`.</span></span>|  
|<span data-ttu-id="b45c0-119">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="b45c0-119">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="b45c0-120">モジュールが完全に読み込まれていないか、またはアンロード中です。</span><span class="sxs-lookup"><span data-stu-id="b45c0-120">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="b45c0-121">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="b45c0-121">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="b45c0-122">指定されたモジュールが動的に生成された (などによって、 `Reflection.Emit`)、このメソッドでサポートされないためです。</span><span class="sxs-lookup"><span data-stu-id="b45c0-122">The specified module was dynamically generated (for example, by `Reflection.Emit`), and is thus not supported by this method.</span></span>|  
|<span data-ttu-id="b45c0-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span><span class="sxs-lookup"><span data-stu-id="b45c0-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span></span>|<span data-ttu-id="b45c0-124">メソッドは、回収可能アセンブリにインスタンス化であるため再コンパイルすることができません。</span><span class="sxs-lookup"><span data-stu-id="b45c0-124">The method is instantiated into a collectible assembly, and is therefore not able to be recompiled.</span></span> <span data-ttu-id="b45c0-125">型および非リフレクション コンテキストで定義された関数 (たとえば、 `List<MyCollectibleStruct>`) 回収可能アセンブリにインスタンス化することができます。</span><span class="sxs-lookup"><span data-stu-id="b45c0-125">Note that types and functions defined in a non-reflection context (for example, `List<MyCollectibleStruct>`) can be instantiated into a collectible assembly.</span></span>|  
|<span data-ttu-id="b45c0-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b45c0-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="b45c0-127">CLR は JIT 再コンパイルの指定したメソッドをマークしているときにメモリ不足になりました。</span><span class="sxs-lookup"><span data-stu-id="b45c0-127">The CLR ran out of memory while trying to mark the specified method for JIT recompilation.</span></span>|  
|<span data-ttu-id="b45c0-128">その他</span><span class="sxs-lookup"><span data-stu-id="b45c0-128">Other</span></span>|<span data-ttu-id="b45c0-129">オペレーティング システムは、CLR 制御範囲外のエラーを返しました。</span><span class="sxs-lookup"><span data-stu-id="b45c0-129">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="b45c0-130">たとえば、メモリのページのアクセスの保護を変更するシステム呼び出しが失敗した場合、オペレーティング システム エラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b45c0-130">For example, if a system call to change the access protection of a page of memory fails, the operating system error is displayed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b45c0-131">必要条件</span><span class="sxs-lookup"><span data-stu-id="b45c0-131">Requirements</span></span>  
 <span data-ttu-id="b45c0-132">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b45c0-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b45c0-133">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b45c0-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b45c0-134">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b45c0-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b45c0-135">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b45c0-135">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b45c0-136">参照</span><span class="sxs-lookup"><span data-stu-id="b45c0-136">See Also</span></span>  
 [<span data-ttu-id="b45c0-137">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b45c0-137">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="b45c0-138">ICorProfilerCallback4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b45c0-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
