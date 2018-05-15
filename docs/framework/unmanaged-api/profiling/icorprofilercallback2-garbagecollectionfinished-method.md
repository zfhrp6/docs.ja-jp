---
title: ICorProfilerCallback2::GarbageCollectionFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.GarbageCollectionFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::GarbageCollectionFinished
helpviewer_keywords:
- ICorProfilerCallback2::GarbageCollectionFinished method [.NET Framework profiling]
- GarbageCollectionFinished method [.NET Framework profiling]
ms.assetid: 1a5758ea-2354-43c0-92a3-32c9909d64e1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 21f7e9fa0e567063c49caa390ace09c43454b092
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a><span data-ttu-id="0c6e7-102">ICorProfilerCallback2::GarbageCollectionFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="0c6e7-102">ICorProfilerCallback2::GarbageCollectionFinished Method</span></span>
<span data-ttu-id="0c6e7-103">ガベージ コレクションが完了し、それに対してガベージ コレクションのすべてのコールバックが発行されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="0c6e7-103">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c6e7-104">構文</span><span class="sxs-lookup"><span data-stu-id="0c6e7-104">Syntax</span></span>  
  
```  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="0c6e7-105">コメント</span><span class="sxs-lookup"><span data-stu-id="0c6e7-105">Remarks</span></span>  
 <span data-ttu-id="0c6e7-106">プロファイラーの最終的な場所にオブジェクトを検査するは安全ではときに、`GarbageCollectionFinished`メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="0c6e7-106">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c6e7-107">要件</span><span class="sxs-lookup"><span data-stu-id="0c6e7-107">Requirements</span></span>  
 <span data-ttu-id="0c6e7-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0c6e7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c6e7-109">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0c6e7-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0c6e7-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c6e7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c6e7-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c6e7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c6e7-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="0c6e7-112">See Also</span></span>  
 [<span data-ttu-id="0c6e7-113">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0c6e7-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="0c6e7-114">ICorProfilerCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0c6e7-114">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
