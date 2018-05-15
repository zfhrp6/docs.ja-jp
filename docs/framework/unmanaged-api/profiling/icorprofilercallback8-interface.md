---
title: ICorProfilerCallback8 インターフェイス
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b92120cc5948efca696d922448da215601f9e6b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback8-interface"></a><span data-ttu-id="e082a-102">ICorProfilerCallback8 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e082a-102">ICorProfilerCallback8 Interface</span></span>
<span data-ttu-id="e082a-103">[.NET Framework 4.7 以降のバージョンでサポート]</span><span class="sxs-lookup"><span data-stu-id="e082a-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  

 <span data-ttu-id="e082a-104">サブクラス[ICorProfilerCallback7](icorprofilercallback7-interface.md)動的メソッドの JIT コンパイルが開始して完了したことをプロファイラーに通知する、共通言語ランタイムによって使用されるコールバック メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="e082a-104">A subclass of [ICorProfilerCallback7](icorprofilercallback7-interface.md) that provides callback methods used by the common language runtime to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span> 
  
## <a name="methods"></a><span data-ttu-id="e082a-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="e082a-105">Methods</span></span>  
  
|<span data-ttu-id="e082a-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="e082a-106">Method</span></span>|<span data-ttu-id="e082a-107">説明</span><span class="sxs-lookup"><span data-stu-id="e082a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e082a-108">DynamicMethodJITCompilationStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="e082a-108">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|<span data-ttu-id="e082a-109">動的メソッドの JIT コンパイルが開始されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e082a-109">Notifies the profiler that JIT compilation of a dynamic method has started.</span></span>|  
|[<span data-ttu-id="e082a-110">DynamicMethodJITCompilationFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="e082a-110">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|<span data-ttu-id="e082a-111">動的メソッドの JIT コンパイルが完了したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e082a-111">Notifies the profiler that JIT compilation of a dynamic method has finished.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e082a-112">要件</span><span class="sxs-lookup"><span data-stu-id="e082a-112">Requirements</span></span>  
 <span data-ttu-id="e082a-113">**プラットフォーム:** を参照してください[システム要件](../../get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e082a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e082a-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e082a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="e082a-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e082a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="e082a-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="e082a-116">See Also</span></span>  
<span data-ttu-id="e082a-117">[プロファイリングのインターフェイス](profiling-interfaces.md) </span><span class="sxs-lookup"><span data-stu-id="e082a-117">[Profiling Interfaces](profiling-interfaces.md) </span></span>  
[<span data-ttu-id="e082a-118">ICorProfilerCallback9 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e082a-118">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
