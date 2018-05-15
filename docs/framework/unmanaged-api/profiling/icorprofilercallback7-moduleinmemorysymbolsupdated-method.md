---
title: ICorProfilerCallback7::ModuleInMemorySymbolsUpdated Method
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7.ModuleInMemorySymbolsUpdated
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: f362a896-3247-4894-9727-e48dbbcd2c78
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9aa690378a32ffee2def672f02dc8b5582647a5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a><span data-ttu-id="05db2-102">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated Method</span><span class="sxs-lookup"><span data-stu-id="05db2-102">ICorProfilerCallback7::ModuleInMemorySymbolsUpdated Method</span></span>
<span data-ttu-id="05db2-103">[.NET Framework 4.6.1 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="05db2-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="05db2-104">メモリ内のモジュールに関連付けられているシンボルのストリームが更新されるたびに、プロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="05db2-104">Notifies the profiler whenever the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05db2-105">構文</span><span class="sxs-lookup"><span data-stu-id="05db2-105">Syntax</span></span>  
  
```  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="05db2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="05db2-106">Parameters</span></span>  
 <span data-ttu-id="05db2-107">[入力] `moduleId`</span><span class="sxs-lookup"><span data-stu-id="05db2-107">[in] `moduleId`</span></span>  
 <span data-ttu-id="05db2-108">メモリ内のモジュールのシンボルのストリームの更新の識別子。</span><span class="sxs-lookup"><span data-stu-id="05db2-108">The identifier of the in-memory module whose symbol stream is updated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05db2-109">コメント</span><span class="sxs-lookup"><span data-stu-id="05db2-109">Remarks</span></span>  
 <span data-ttu-id="05db2-110">このコールバックは、設定によって制御されます、 [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)イベント マスク フラグを呼び出すときに、 [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="05db2-110">This callback is controlled by setting the [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05db2-111">このイベントは、現在のシンボルに暗黙的に作成または使用して変更は発生しません<xref:System.Reflection.Emit>Api です。</span><span class="sxs-lookup"><span data-stu-id="05db2-111">This event is not currently raised for symbols implicitly created or modified via <xref:System.Reflection.Emit> APIs.</span></span>  
  
 <span data-ttu-id="05db2-112">でもシンボルが指定されたときに前もってマネージのオーバー ロードのいずれかへの呼び出しで<xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType>メソッドを含む、 `rawSymbolStore` runtime、アセンブリのシンボルを指定する引数可能性があります実際には関連付けられませんシンボリック データ モジュールまで後、 [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)コールバックが発生しました。</span><span class="sxs-lookup"><span data-stu-id="05db2-112">Even when symbols are provided up front in a call to one of the overloads of the managed <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> methods that includes a `rawSymbolStore` argument to specify the symbols for the assembly, the runtime may not actually associate the symbolic data with the module until after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback has occurred.</span></span> <span data-ttu-id="05db2-113">このイベントは、このようなモジュールのシンボルを収集する以降の機会を提供します。</span><span class="sxs-lookup"><span data-stu-id="05db2-113">This event provides a later opportunity to collect symbols for such modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05db2-114">要件</span><span class="sxs-lookup"><span data-stu-id="05db2-114">Requirements</span></span>  
 <span data-ttu-id="05db2-115">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="05db2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05db2-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="05db2-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="05db2-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05db2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05db2-118">**.NET Framework のバージョン:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05db2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05db2-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="05db2-119">See Also</span></span>  
 [<span data-ttu-id="05db2-120">ModuleLoadFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="05db2-120">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)  
 [<span data-ttu-id="05db2-121">SetEventMask2 メソッド</span><span class="sxs-lookup"><span data-stu-id="05db2-121">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)  
 [<span data-ttu-id="05db2-122">ICorProfilerCallback7 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="05db2-122">ICorProfilerCallback7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
