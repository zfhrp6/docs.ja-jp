---
title: "ICorProfilerThreadEnum インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerThreadEnum
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerThreadEnum
helpviewer_keywords: ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: 1e35031b-e095-4c14-9644-8deeb3081e0b
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2ce48c836070018059becd1ece269ce7c878c7ba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerthreadenum-interface"></a><span data-ttu-id="769aa-102">ICorProfilerThreadEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="769aa-102">ICorProfilerThreadEnum Interface</span></span>
<span data-ttu-id="769aa-103">共通言語ランタイムのスレッドのコレクションを順番に反復処理するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="769aa-103">Provides methods to sequentially iterate through a collection of threads in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="769aa-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="769aa-104">Methods</span></span>  
  
|<span data-ttu-id="769aa-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="769aa-105">Method</span></span>|<span data-ttu-id="769aa-106">説明</span><span class="sxs-lookup"><span data-stu-id="769aa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="769aa-107">Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="769aa-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-clone-method.md)|<span data-ttu-id="769aa-108">この `ICorProfilerThreadEnum` インターフェイスのコピーに対するインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="769aa-108">Gets an interface pointer to a copy of this `ICorProfilerThreadEnum` interface.</span></span>|  
|[<span data-ttu-id="769aa-109">GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="769aa-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-getcount-method.md)|<span data-ttu-id="769aa-110">アプリケーションで使用されるスレッドの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="769aa-110">Gets the number of threads that are used by the application.</span></span>|  
|[<span data-ttu-id="769aa-111">Next メソッド</span><span class="sxs-lookup"><span data-stu-id="769aa-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-next-method.md)|<span data-ttu-id="769aa-112">スレッドのシーケンシャル コレクションから、列挙子の現在の位置以降にある指定した数の隣接するスレッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="769aa-112">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="769aa-113">Reset メソッド</span><span class="sxs-lookup"><span data-stu-id="769aa-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-reset-method.md)|<span data-ttu-id="769aa-114">列挙子のカーソルをシーケンスの開始位置に移動します。</span><span class="sxs-lookup"><span data-stu-id="769aa-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="769aa-115">Skip メソッド</span><span class="sxs-lookup"><span data-stu-id="769aa-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-skip-method.md)|<span data-ttu-id="769aa-116">指定した数の要素をスキップするため、この列挙子のカーソルを現在の位置から進めます。</span><span class="sxs-lookup"><span data-stu-id="769aa-116">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="769aa-117">コメント</span><span class="sxs-lookup"><span data-stu-id="769aa-117">Remarks</span></span>  
 <span data-ttu-id="769aa-118">`ICorProfilerThreadEnum` インターフェイスは列挙子です。</span><span class="sxs-lookup"><span data-stu-id="769aa-118">The `ICorProfilerThreadEnum` interface is an enumerator.</span></span> <span data-ttu-id="769aa-119">このインターフェイスにより、配列の受信側は、受信側に適した速度で送信側から要素をプルできます。</span><span class="sxs-lookup"><span data-stu-id="769aa-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="769aa-120">つまり、受信側は配列要素のフローを明示的に制御できるため、大きな配列をメソッド パラメーターとして渡す場合に関連する問題を回避できます。</span><span class="sxs-lookup"><span data-stu-id="769aa-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="769aa-121">要件</span><span class="sxs-lookup"><span data-stu-id="769aa-121">Requirements</span></span>  
 <span data-ttu-id="769aa-122">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="769aa-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="769aa-123">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="769aa-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="769aa-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="769aa-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="769aa-125">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="769aa-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="769aa-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="769aa-126">See Also</span></span>  
 [<span data-ttu-id="769aa-127">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="769aa-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="769aa-128">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="769aa-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
