---
title: "ICorProfilerFunctionEnum インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerFunctionEnum
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerFunctionEnum
helpviewer_keywords: ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0a1d4a38-cd0b-4231-91df-13646218ae72
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1067fa6738b23492b3a58500b4cb6ba1d030304f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerfunctionenum-interface"></a><span data-ttu-id="441b3-102">ICorProfilerFunctionEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="441b3-102">ICorProfilerFunctionEnum Interface</span></span>
<span data-ttu-id="441b3-103">共通言語ランタイムの関数のコレクションを順番に反復処理するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="441b3-103">Provides methods to sequentially iterate through a collection of functions in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="441b3-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="441b3-104">Methods</span></span>  
  
|<span data-ttu-id="441b3-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="441b3-105">Method</span></span>|<span data-ttu-id="441b3-106">説明</span><span class="sxs-lookup"><span data-stu-id="441b3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="441b3-107">Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="441b3-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-clone-method.md)|<span data-ttu-id="441b3-108">この `ICorProfilerFunctionEnum` インターフェイスのコピーに対するインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="441b3-108">Gets an interface pointer to a copy of this `ICorProfilerFunctionEnum` interface.</span></span>|  
|[<span data-ttu-id="441b3-109">GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="441b3-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-getcount-method.md)|<span data-ttu-id="441b3-110">アプリケーションによって読み込まれたか、またはプロファイラーによって強制的に読み込まれた関数の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="441b3-110">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>|  
|[<span data-ttu-id="441b3-111">Next メソッド</span><span class="sxs-lookup"><span data-stu-id="441b3-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-next-method.md)|<span data-ttu-id="441b3-112">関数のシーケンシャル コレクションから、列挙子の現在の位置以降にある、指定した数の隣接する関数を取得します。</span><span class="sxs-lookup"><span data-stu-id="441b3-112">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="441b3-113">Reset メソッド</span><span class="sxs-lookup"><span data-stu-id="441b3-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-reset-method.md)|<span data-ttu-id="441b3-114">列挙子のカーソルをシーケンスの開始位置に移動します。</span><span class="sxs-lookup"><span data-stu-id="441b3-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="441b3-115">Skip メソッド</span><span class="sxs-lookup"><span data-stu-id="441b3-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-skip-method.md)|<span data-ttu-id="441b3-116">指定した数の要素がスキップされるように、この列挙子のカーソルを現在の位置から進めます。</span><span class="sxs-lookup"><span data-stu-id="441b3-116">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="441b3-117">コメント</span><span class="sxs-lookup"><span data-stu-id="441b3-117">Remarks</span></span>  
 <span data-ttu-id="441b3-118">`ICorProfilerFunctionEnum` インターフェイスは列挙子です。</span><span class="sxs-lookup"><span data-stu-id="441b3-118">The `ICorProfilerFunctionEnum` interface is an enumerator.</span></span> <span data-ttu-id="441b3-119">このインターフェイスにより、配列の受信側は、受信側に適した速度で送信側から要素をプルできます。</span><span class="sxs-lookup"><span data-stu-id="441b3-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="441b3-120">つまり、受信側は配列要素のフローを明示的に制御できるため、大きな配列をメソッド パラメーターとして渡す場合に関連する問題を回避できます。</span><span class="sxs-lookup"><span data-stu-id="441b3-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
 <span data-ttu-id="441b3-121">`ICorProfilerFunctionEnum` は、既に JIT コンパイルされた関数を列挙しますが、この中に Ngen.exe で生成されたネイティブ イメージから読み込まれた関数は含まれません。</span><span class="sxs-lookup"><span data-stu-id="441b3-121">`ICorProfilerFunctionEnum` enumerates over functions that have already been JIT-compiled, but does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="441b3-122">要件</span><span class="sxs-lookup"><span data-stu-id="441b3-122">Requirements</span></span>  
 <span data-ttu-id="441b3-123">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="441b3-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="441b3-124">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="441b3-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="441b3-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="441b3-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="441b3-126">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="441b3-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="441b3-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="441b3-127">See Also</span></span>  
 [<span data-ttu-id="441b3-128">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="441b3-128">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="441b3-129">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="441b3-129">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="441b3-130">EnumJITedFunctions メソッド</span><span class="sxs-lookup"><span data-stu-id="441b3-130">EnumJITedFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)
