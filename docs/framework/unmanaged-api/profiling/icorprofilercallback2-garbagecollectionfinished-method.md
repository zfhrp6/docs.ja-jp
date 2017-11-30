---
title: "ICorProfilerCallback2::GarbageCollectionFinished メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback2.GarbageCollectionFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback2::GarbageCollectionFinished
helpviewer_keywords:
- ICorProfilerCallback2::GarbageCollectionFinished method [.NET Framework profiling]
- GarbageCollectionFinished method [.NET Framework profiling]
ms.assetid: 1a5758ea-2354-43c0-92a3-32c9909d64e1
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 287c33a80144b9b04fd7e0797071d40e46a52454
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a><span data-ttu-id="13d34-102">ICorProfilerCallback2::GarbageCollectionFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="13d34-102">ICorProfilerCallback2::GarbageCollectionFinished Method</span></span>
<span data-ttu-id="13d34-103">ガベージ コレクションが完了し、それに対してガベージ コレクションのすべてのコールバックが発行されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="13d34-103">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13d34-104">構文</span><span class="sxs-lookup"><span data-stu-id="13d34-104">Syntax</span></span>  
  
```  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="13d34-105">コメント</span><span class="sxs-lookup"><span data-stu-id="13d34-105">Remarks</span></span>  
 <span data-ttu-id="13d34-106">プロファイラーの最終的な場所にオブジェクトを検査するは安全ではときに、`GarbageCollectionFinished`メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="13d34-106">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13d34-107">要件</span><span class="sxs-lookup"><span data-stu-id="13d34-107">Requirements</span></span>  
 <span data-ttu-id="13d34-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="13d34-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13d34-109">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="13d34-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="13d34-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13d34-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13d34-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13d34-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13d34-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="13d34-112">See Also</span></span>  
 [<span data-ttu-id="13d34-113">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="13d34-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="13d34-114">ICorProfilerCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="13d34-114">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
