---
title: "ICorProfilerCallback3::InitializeForAttach メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback3.InitializeForAttach Method
api_location: Mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback3::InitializeForAttach
helpviewer_keywords:
- InitializeForAttach method [.NET Framework profiling]
- ICorProfilerCallback3::InitializeForAttach method [.NET Framework profiling]
ms.assetid: bed097b3-6d52-46c9-bee7-ac7910b6fc3f
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 124e27e446e129173018aed9d3ab770582342c72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback3initializeforattach-method"></a><span data-ttu-id="9782f-102">ICorProfilerCallback3::InitializeForAttach メソッド</span><span class="sxs-lookup"><span data-stu-id="9782f-102">ICorProfilerCallback3::InitializeForAttach Method</span></span>
<span data-ttu-id="9782f-103">アタッチ操作後にその状態を初期化する機会をプロファイラーに与えるために、共通言語ランタイム (CLR) により呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="9782f-103">Called by the common language runtime (CLR) to give the profiler an opportunity to initialize its state after an attach operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9782f-104">構文</span><span class="sxs-lookup"><span data-stu-id="9782f-104">Syntax</span></span>  
  
```  
HRESULT InitializeForAttach(  
            [in] IUnknown * pCorProfilerInfoUnk,  
            [in] void * pvClientData,  
            [in] UINT cbClientData);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9782f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9782f-105">Parameters</span></span>  
 `pCorProfilerInfoUnk`  
 <span data-ttu-id="9782f-106">[in] `ICorProfilerInfo*` インターフェイスへのインターフェイス ポインター。</span><span class="sxs-lookup"><span data-stu-id="9782f-106">[in] An interface pointer for the `ICorProfilerInfo*` interface.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="9782f-107">[in]渡されるデータへのポインター、 [iclrprofiling::attachprofiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md)メソッドでその`pvClientData`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="9782f-107">[in] A pointer to the data passed to the [IClrProfiling::AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) method in its `pvClientData` parameter.</span></span> <span data-ttu-id="9782f-108">このパラメーターが null の場合、`cbClientData` は 0 (ゼロ) になります。</span><span class="sxs-lookup"><span data-stu-id="9782f-108">If this parameter is null, `cbClientData` will be 0 (zero).</span></span> <span data-ttu-id="9782f-109">CLR は、`InitializeForAttach` から戻るとこのメモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="9782f-109">The CLR frees this memory when it returns from `InitializeForAttach`.</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="9782f-110">[in] `pvClientData` がポイントするデータのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="9782f-110">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9782f-111">コメント</span><span class="sxs-lookup"><span data-stu-id="9782f-111">Remarks</span></span>  
 <span data-ttu-id="9782f-112">CLR は `InitializeForAttach` を呼び出し、コールバックを要求できる機会をプロファイラーに与えます。</span><span class="sxs-lookup"><span data-stu-id="9782f-112">The CLR calls `InitializeForAttach` to give the profiler an opportunity to request callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9782f-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="9782f-113">Requirements</span></span>  
 <span data-ttu-id="9782f-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9782f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9782f-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9782f-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9782f-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9782f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9782f-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9782f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9782f-118">参照</span><span class="sxs-lookup"><span data-stu-id="9782f-118">See Also</span></span>  
 [<span data-ttu-id="9782f-119">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9782f-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="9782f-120">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9782f-120">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="9782f-121">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="9782f-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="9782f-122">プロファイル</span><span class="sxs-lookup"><span data-stu-id="9782f-122">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
