---
title: ICorProfilerCallback9 インターフェイス
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 488af069e7798fde650abb1473df256eed2d692f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452378"
---
# <a name="icorprofilercallback9-interface"></a><span data-ttu-id="534d2-102">ICorProfilerCallback9 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="534d2-102">ICorProfilerCallback9 Interface</span></span>
<span data-ttu-id="534d2-103">[.NET Framework 4.7.2 およびそれ以降のバージョンでサポート]</span><span class="sxs-lookup"><span data-stu-id="534d2-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  

 <span data-ttu-id="534d2-104">サブクラス[ICorProfilerCallback8](icorprofilercallback8-interface.md)動的メソッドがガベージ コレクションされ、後でアンロードされたことをプロファイラーに通知する、共通言語ランタイムで使用されるコールバック メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="534d2-104">A subclass of [ICorProfilerCallback8](icorprofilercallback8-interface.md) that provides a callback method used by the common language runtime to notify the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="534d2-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="534d2-105">Methods</span></span>  
  
|<span data-ttu-id="534d2-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="534d2-106">Method</span></span>|<span data-ttu-id="534d2-107">説明</span><span class="sxs-lookup"><span data-stu-id="534d2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="534d2-108">DynamicMethodUnloaded メソッド</span><span class="sxs-lookup"><span data-stu-id="534d2-108">DynamicMethodUnloaded Method</span></span>](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|<span data-ttu-id="534d2-109">動的メソッドがガベージ コレクションされ、後でアンロードされたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="534d2-109">Notifies the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="534d2-110">要件</span><span class="sxs-lookup"><span data-stu-id="534d2-110">Requirements</span></span>  
 <span data-ttu-id="534d2-111">**プラットフォーム:** を参照してください[システム要件](../../get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="534d2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="534d2-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="534d2-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="534d2-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="534d2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="534d2-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="534d2-114">See Also</span></span>  
<span data-ttu-id="534d2-115">[プロファイリングのインターフェイス](profiling-interfaces.md) </span><span class="sxs-lookup"><span data-stu-id="534d2-115">[Profiling Interfaces](profiling-interfaces.md) </span></span>  
<span data-ttu-id="534d2-116">[ICorProfilerCallback8 インターフェイス](icorprofilercallback9-interface.md) </span><span class="sxs-lookup"><span data-stu-id="534d2-116">[ICorProfilerCallback8 Interface](icorprofilercallback9-interface.md) </span></span>  
<span data-ttu-id="534d2-117">[ICorProfilerCallback8.DynamicMethodJITCompilationStarted メソッド](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md) </span><span class="sxs-lookup"><span data-stu-id="534d2-117">[ICorProfilerCallback8.DynamicMethodJITCompilationStarted method](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md) </span></span>  
[<span data-ttu-id="534d2-118">ICorProfilerCallback8.DynamicMethodJITCompilationFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="534d2-118">ICorProfilerCallback8.DynamicMethodJITCompilationFinished method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)   
