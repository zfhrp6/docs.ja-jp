---
title: "ICorProfilerInfo4 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4
helpviewer_keywords: ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 80a5308e-c22f-4201-ba89-31cc8562515b
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: db91347ad2c951c28ea7b653336450929d37bdcb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4-interface"></a><span data-ttu-id="2ae0e-102">ICorProfilerInfo4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2ae0e-102">ICorProfilerInfo4 Interface</span></span>
<span data-ttu-id="2ae0e-103">コード プロファイラーが共通言語ランタイム (CLR) イベントの監視の制御と要求情報を通信に使用するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="2ae0e-103">Provides methods that code profilers use to communicate with the common language runtime (CLR) to control event monitoring and request information.</span></span> <span data-ttu-id="2ae0e-104">」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ae0e-104">.</span></span> <span data-ttu-id="2ae0e-105">`ICorProfilerInfo4`インターフェイスは、その他の拡張機能`ICorProfilerInfo`インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="2ae0e-105">The `ICorProfilerInfo4` interface is an extension of the other `ICorProfilerInfo` interfaces.</span></span> <span data-ttu-id="2ae0e-106">追加された、・ イン タイム (JIT) の再コンパイルをサポートする新しいメソッドを提供、[!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="2ae0e-106">It provides new methods to support just-in-time (JIT) recompilation, added in the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2ae0e-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="2ae0e-107">Methods</span></span>  
  
|<span data-ttu-id="2ae0e-108">メソッド</span><span class="sxs-lookup"><span data-stu-id="2ae0e-108">Method</span></span>|<span data-ttu-id="2ae0e-109">説明</span><span class="sxs-lookup"><span data-stu-id="2ae0e-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2ae0e-110">EnumJITedFunctions2 メソッド</span><span class="sxs-lookup"><span data-stu-id="2ae0e-110">EnumJITedFunctions2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)|<span data-ttu-id="2ae0e-111">以前に JIT コンパイルされ、JIT 再コンパイルしていたすべての関数の列挙子を返します。</span><span class="sxs-lookup"><span data-stu-id="2ae0e-111">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span>|  
|[<span data-ttu-id="2ae0e-112">EnumThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="2ae0e-112">EnumThreads Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumthreads-method.md)|<span data-ttu-id="2ae0e-113">プロファイリングされたプロセスのすべてのマネージ スレッドのコレクションを順番に反復処理するメソッドを提供する列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="2ae0e-113">Gets an enumerator that that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>|  
|[<span data-ttu-id="2ae0e-114">GetCodeInfo3 メソッド</span><span class="sxs-lookup"><span data-stu-id="2ae0e-114">GetCodeInfo3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)|<span data-ttu-id="2ae0e-115">指定した関数の JIT 再コンパイル バージョンに関連付けられているネイティブ コードの範囲を取得します。</span><span class="sxs-lookup"><span data-stu-id="2ae0e-115">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>|  
|[<span data-ttu-id="2ae0e-116">GetFunctionFromIP2 メソッド</span><span class="sxs-lookup"><span data-stu-id="2ae0e-116">GetFunctionFromIP2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getfunctionfromip2-method.md)|<span data-ttu-id="2ae0e-117">マネージ コードの命令ポインターを指定された関数の JIT 再コンパイル バージョンにマップします。</span><span class="sxs-lookup"><span data-stu-id="2ae0e-117">Maps a managed code instruction pointer to the JIT-recompiled version of a specified function.</span></span>|  
|[<span data-ttu-id="2ae0e-118">GetILToNativeMapping2 メソッド</span><span class="sxs-lookup"><span data-stu-id="2ae0e-118">GetILToNativeMapping2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)|<span data-ttu-id="2ae0e-119">Microsoft intermediate language (MSIL) が指定の関数の JIT 再コンパイル バージョンに含まれるコードのネイティブ オフセットへオフセットから、マップを取得します。</span><span class="sxs-lookup"><span data-stu-id="2ae0e-119">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function .</span></span>|  
|[<span data-ttu-id="2ae0e-120">GetObjectSize2 メソッド</span><span class="sxs-lookup"><span data-stu-id="2ae0e-120">GetObjectSize2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)|<span data-ttu-id="2ae0e-121">指定したオブジェクトのサイズを返します。</span><span class="sxs-lookup"><span data-stu-id="2ae0e-121">Returns the size of a specified object.</span></span>|  
|[<span data-ttu-id="2ae0e-122">GetReJITIDs メソッド</span><span class="sxs-lookup"><span data-stu-id="2ae0e-122">GetReJITIDs Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getrejitids-method.md)|<span data-ttu-id="2ae0e-123">JIT 再コンパイルのすべてのバージョン指定の関数はまだ割り当てられていることを識別する Id の配列を返します。</span><span class="sxs-lookup"><span data-stu-id="2ae0e-123">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span>|  
|[<span data-ttu-id="2ae0e-124">InitializeCurrentThread メソッド</span><span class="sxs-lookup"><span data-stu-id="2ae0e-124">InitializeCurrentThread Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-initializecurrentthread-method.md)|<span data-ttu-id="2ae0e-125">後続のプロファイラー API は、デッドロックを回避するため、同じスレッドで呼び出しの前に、現在のスレッドを初期化します。</span><span class="sxs-lookup"><span data-stu-id="2ae0e-125">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>|  
|[<span data-ttu-id="2ae0e-126">RequestReJIT メソッド</span><span class="sxs-lookup"><span data-stu-id="2ae0e-126">RequestReJIT Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)|<span data-ttu-id="2ae0e-127">指定された関数のすべてのインスタンスの JIT 再コンパイルを要求します。</span><span class="sxs-lookup"><span data-stu-id="2ae0e-127">Requests a JIT recompilation of all instances of the specified functions.</span></span>|  
|[<span data-ttu-id="2ae0e-128">RequestRevert メソッド</span><span class="sxs-lookup"><span data-stu-id="2ae0e-128">RequestRevert Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)|<span data-ttu-id="2ae0e-129">指定された関数のすべてのインスタンスを元のバージョンに戻します。</span><span class="sxs-lookup"><span data-stu-id="2ae0e-129">Reverts all instances of the specified functions to their original versions.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ae0e-130">コメント</span><span class="sxs-lookup"><span data-stu-id="2ae0e-130">Remarks</span></span>  
 <span data-ttu-id="2ae0e-131">CLR は、`ICorProfilerInfo4` インターフェイスのメソッドを、フリー スレッド モデルを使用して実装します。</span><span class="sxs-lookup"><span data-stu-id="2ae0e-131">The CLR implements the methods of the `ICorProfilerInfo4` interface by using the free-threaded model.</span></span> <span data-ttu-id="2ae0e-132">各メソッドが、成功または失敗を示す HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="2ae0e-132">Each method returns an HRESULT to indicate success or failure.</span></span> <span data-ttu-id="2ae0e-133">返される可能性があるリターン コードの一覧については、CorError.h ファイルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ae0e-133">For a list of possible return codes, see the CorError.h file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ae0e-134">要件</span><span class="sxs-lookup"><span data-stu-id="2ae0e-134">Requirements</span></span>  
 <span data-ttu-id="2ae0e-135">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2ae0e-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ae0e-136">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2ae0e-136">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2ae0e-137">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ae0e-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ae0e-138">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ae0e-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ae0e-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="2ae0e-139">See Also</span></span>  
 [<span data-ttu-id="2ae0e-140">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="2ae0e-140">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="2ae0e-141">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2ae0e-141">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
