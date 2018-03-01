---
title: "ICorProfilerFunctionControl インターフェイス"
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
- ICorProfilerFunctionControl
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl
helpviewer_keywords:
- ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 4e3d3141-4662-4166-8f05-bc857c1b4216
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 043e97595ba29d0fb5320b8f1bdc4aad4f755067
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerfunctioncontrol-interface"></a><span data-ttu-id="dd5fb-102">ICorProfilerFunctionControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dd5fb-102">ICorProfilerFunctionControl Interface</span></span>
<span data-ttu-id="dd5fb-103">特定のメソッドを再コンパイルする時に JIT コンパイラーがコードをどのように生成するかを制御するために、コード プロファイラーが共通言語ランタイム (CLR) と通信できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="dd5fb-103">Provides methods that allow a code profiler to communicate with the common language runtime (CLR) to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dd5fb-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="dd5fb-104">Methods</span></span>  
  
|<span data-ttu-id="dd5fb-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="dd5fb-105">Method</span></span>|<span data-ttu-id="dd5fb-106">説明</span><span class="sxs-lookup"><span data-stu-id="dd5fb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dd5fb-107">SetCodegenFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="dd5fb-107">SetCodegenFlags Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)|<span data-ttu-id="dd5fb-108">1 つまたは複数のフラグを設定、 [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)のイン-タイム (JIT) のコード生成を制御する列挙型の再コンパイルされた関数。</span><span class="sxs-lookup"><span data-stu-id="dd5fb-108">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>|  
|[<span data-ttu-id="dd5fb-109">SetILFunctionBody メソッド</span><span class="sxs-lookup"><span data-stu-id="dd5fb-109">SetILFunctionBody Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilfunctionbody-method.md)|<span data-ttu-id="dd5fb-110">メソッドの中間共通言語 (CIL) 本体を置換します。</span><span class="sxs-lookup"><span data-stu-id="dd5fb-110">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>|  
|[<span data-ttu-id="dd5fb-111">SetILInstrumentedCodeMap メソッド</span><span class="sxs-lookup"><span data-stu-id="dd5fb-111">SetILInstrumentedCodeMap Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md)|<span data-ttu-id="dd5fb-112">指定した共通中間言語 (CIL) マップ エントリを使用して、指定される関数のコード マップを設定します。</span><span class="sxs-lookup"><span data-stu-id="dd5fb-112">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd5fb-113">コメント</span><span class="sxs-lookup"><span data-stu-id="dd5fb-113">Remarks</span></span>  
 <span data-ttu-id="dd5fb-114">`ICorProfilerFunctionControl` インターフェイスは、単一の再コンパイルされた関数に対してコード生成を制御するためにメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="dd5fb-114">The `ICorProfilerFunctionControl` interface provides methods for controlling code generation for a single recompiled function.</span></span> <span data-ttu-id="dd5fb-115">プロファイラーがを介して、このインターフェイスのインスタンスを取得、 [icorprofilercallback 4::getrejitparameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="dd5fb-115">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="dd5fb-116">`ICorProfilerFunctionControl` の各インスタンスは一つの関数の全てのインスタンスを制御します。</span><span class="sxs-lookup"><span data-stu-id="dd5fb-116">Each instance of `ICorProfilerFunctionControl` controls all instances of one function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd5fb-117">必要条件</span><span class="sxs-lookup"><span data-stu-id="dd5fb-117">Requirements</span></span>  
 <span data-ttu-id="dd5fb-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="dd5fb-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd5fb-119">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dd5fb-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dd5fb-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd5fb-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd5fb-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd5fb-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd5fb-122">参照</span><span class="sxs-lookup"><span data-stu-id="dd5fb-122">See Also</span></span>  
 [<span data-ttu-id="dd5fb-123">ICorProfilerInfo4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dd5fb-123">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="dd5fb-124">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="dd5fb-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="dd5fb-125">EnumJITedFunctions2 メソッド</span><span class="sxs-lookup"><span data-stu-id="dd5fb-125">EnumJITedFunctions2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)
