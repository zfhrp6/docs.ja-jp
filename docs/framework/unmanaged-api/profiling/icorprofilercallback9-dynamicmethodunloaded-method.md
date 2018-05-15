---
title: ICorProfilerCallback9::DynamicMethodUnloaded メソッド
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9.DynamicMethodUnloaded
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 16b3334647922f845645e6eb58db3146f4c9b936
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="2296a-102">ICorProfilerCallback9::DynamicMethodUnloaded メソッド</span><span class="sxs-lookup"><span data-stu-id="2296a-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>
<span data-ttu-id="2296a-103">[.NET Framework 4.7.2 およびそれ以降のバージョンでサポート]</span><span class="sxs-lookup"><span data-stu-id="2296a-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="2296a-104">動的メソッドは、ガベージ コレクションされ、後でアンロードされるたびに、プロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="2296a-104">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2296a-105">構文</span><span class="sxs-lookup"><span data-stu-id="2296a-105">Syntax</span></span>  
  
```  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2296a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2296a-106">Parameters</span></span>  
<span data-ttu-id="2296a-107">[入力] `functionId`</span><span class="sxs-lookup"><span data-stu-id="2296a-107">[in] `functionId`</span></span>  
<span data-ttu-id="2296a-108">ガベージ コレクションされ、アンロードされているメモリ内の関数の識別子。</span><span class="sxs-lookup"><span data-stu-id="2296a-108">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>   

## <a name="requirements"></a><span data-ttu-id="2296a-109">要件</span><span class="sxs-lookup"><span data-stu-id="2296a-109">Requirements</span></span>  
 <span data-ttu-id="2296a-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2296a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2296a-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2296a-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2296a-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2296a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2296a-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2296a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2296a-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="2296a-114">See Also</span></span>  
[<span data-ttu-id="2296a-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="2296a-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)  
[<span data-ttu-id="2296a-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="2296a-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)  
<span data-ttu-id="2296a-117">[ICorProfilerCallback9 インターフェイス](icorprofilercallback9-interface.md) </span><span class="sxs-lookup"><span data-stu-id="2296a-117">[ICorProfilerCallback9 Interface](icorprofilercallback9-interface.md) </span></span>  
[<span data-ttu-id="2296a-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="2296a-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
