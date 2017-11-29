---
title: "ICorProfilerCallback7 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorProfilerCallback7
api_location:
- mscorwks.dll
- corprof.idl
api_type: COM
ms.assetid: a0be019e-aaa1-4036-990f-565f114d4b5c
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f8eb370e4f16212c536c252661163b7eca6f74d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallback7-interface"></a><span data-ttu-id="8affd-102">ICorProfilerCallback7 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8affd-102">ICorProfilerCallback7 Interface</span></span>
<span data-ttu-id="8affd-103">[.NET Framework 4.6.1 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="8affd-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="8affd-104">[ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) のサブクラスは、メモリ内のモジュールに関連付けられているシンボルのストリームが更新されたことをプロファイラーに通知するために、共通言語ランタイムが使用するコールバック メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="8affd-104">A subclass of [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) that provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8affd-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="8affd-105">Methods</span></span>  
  
|<span data-ttu-id="8affd-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="8affd-106">Method</span></span>|<span data-ttu-id="8affd-107">説明</span><span class="sxs-lookup"><span data-stu-id="8affd-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8affd-108">ModuleInMemorySymbolsUpdated メソッド</span><span class="sxs-lookup"><span data-stu-id="8affd-108">ModuleInMemorySymbolsUpdated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|<span data-ttu-id="8affd-109">メモリ内のモジュールに関連付けられているシンボルのストリームが更新されていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="8affd-109">Notifies the profiler that the symbol stream associated with an in-memory module is updated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8affd-110">要件</span><span class="sxs-lookup"><span data-stu-id="8affd-110">Requirements</span></span>  
 <span data-ttu-id="8affd-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8affd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8affd-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8affd-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8affd-113">**.NET Framework のバージョン:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8affd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8affd-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="8affd-114">See Also</span></span>  
 [<span data-ttu-id="8affd-115">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="8affd-115">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
