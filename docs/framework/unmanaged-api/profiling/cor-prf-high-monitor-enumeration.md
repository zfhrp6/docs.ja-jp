---
title: "COR_PRF_HIGH_MONITOR 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1df931796b32b6bea49e8b69da02d39e6a4803e3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="corprfhighmonitor-enumeration"></a><span data-ttu-id="17b0a-102">COR_PRF_HIGH_MONITOR 列挙型</span><span class="sxs-lookup"><span data-stu-id="17b0a-102">COR_PRF_HIGH_MONITOR Enumeration</span></span>
<span data-ttu-id="17b0a-103">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="17b0a-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="17b0a-104">:Seteventmask2 フラグを提供、 [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)ために、プロファイラーが指定する列挙体、 [icorprofilerinfo 5::seteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)メソッドの読み込み時にします。</span><span class="sxs-lookup"><span data-stu-id="17b0a-104">Provides flags in addition to those found in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17b0a-105">構文</span><span class="sxs-lookup"><span data-stu-id="17b0a-105">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_HIGH_MONITOR_NONE                = 0x00000000,  
    COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES     = 0x00000001,  
    COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED     = 0x00000002,     
    COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE       = 0,  
    COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH      = COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED,  
    COR_PRF_HIGH_MONITOR_IMMUTABLE           = 0  
} COR_PRF_HIGH_MONITOR;  
```  
  
## <a name="members"></a><span data-ttu-id="17b0a-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="17b0a-106">Members</span></span>  
  
|<span data-ttu-id="17b0a-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="17b0a-107">Member</span></span>|<span data-ttu-id="17b0a-108">説明</span><span class="sxs-lookup"><span data-stu-id="17b0a-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|<span data-ttu-id="17b0a-109">フラグが設定されていません。</span><span class="sxs-lookup"><span data-stu-id="17b0a-109">No flags are set.</span></span>|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|<span data-ttu-id="17b0a-110">コントロール、 [icorprofilercallback 6::getassemblyreference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) CLR アセンブリ参照クロージャのウォーク中にアセンブリ参照を追加するためのコールバック。</span><span class="sxs-lookup"><span data-stu-id="17b0a-110">Controls the [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback for adding assembly references during the CLR assembly reference closure walk.</span></span>|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|<span data-ttu-id="17b0a-111">コントロール、 [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)メモリ内のモジュールに関連付けられているシンボルのストリームへの更新のコールバック。</span><span class="sxs-lookup"><span data-stu-id="17b0a-111">Controls the [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) callback for updates to the symbol stream associated with an in-memory module.</span></span>|  
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="17b0a-112">プロファイルが拡張したイメージを必要とする、`COR_PRF_HIGH_MONITOR` のすべてのフラグを表します。</span><span class="sxs-lookup"><span data-stu-id="17b0a-112">Represents all `COR_PRF_HIGH_MONITOR` flags that require profile-enhanced images.</span></span> <span data-ttu-id="17b0a-113">対応して、`COR_PRF_REQUIRE_PROFILE_IMAGE`フラグ、 [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列挙します。</span><span class="sxs-lookup"><span data-stu-id="17b0a-113">It corresponds to the `COR_PRF_REQUIRE_PROFILE_IMAGE` flag in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="17b0a-114">プロファイラーが実行中のアプリケーションに割り当てられた後に設定することが可能な、`COR_PRF_HIGH_MONITOR` のすべてのフラグを表します。</span><span class="sxs-lookup"><span data-stu-id="17b0a-114">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span>|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|<span data-ttu-id="17b0a-115">初期化の最中にのみ設定できるすべての `COR_PRF_HIGH_MONITOR` フラグを表しています。</span><span class="sxs-lookup"><span data-stu-id="17b0a-115">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="17b0a-116">他の場所でこれらのフラグを変更しようとすると、エラーを表す `HRESULT` 値が生じます。</span><span class="sxs-lookup"><span data-stu-id="17b0a-116">Trying to change any of these flags elsewhere results in an `HRESULT` value that indicates failure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17b0a-117">コメント</span><span class="sxs-lookup"><span data-stu-id="17b0a-117">Remarks</span></span>  
 <span data-ttu-id="17b0a-118">`COR_PRF_HIGH_MONITOR`でフラグを使用して、`pdwEventsHigh`のパラメーター、 [icorprofilerinfo 5::geteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)と[icorprofilerinfo 5::seteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="17b0a-118">The `COR_PRF_HIGH_MONITOR` flags are used with the `pdwEventsHigh` parameter of the [ICorProfilerInfo5::GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) and [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) methods.</span></span>  
  
 <span data-ttu-id="17b0a-119">以降で、[!INCLUDE[net_v461](../../../../includes/net-v461-md.md)]の値、`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`する場合は 0 から変更`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`(0x00000002)。</span><span class="sxs-lookup"><span data-stu-id="17b0a-119">Starting with the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)], the value of the `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` changed from 0 to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17b0a-120">要件</span><span class="sxs-lookup"><span data-stu-id="17b0a-120">Requirements</span></span>  
 <span data-ttu-id="17b0a-121">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="17b0a-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17b0a-122">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="17b0a-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="17b0a-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17b0a-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17b0a-124">**.NET framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17b0a-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17b0a-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="17b0a-125">See Also</span></span>  
 [<span data-ttu-id="17b0a-126">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="17b0a-126">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
 [<span data-ttu-id="17b0a-127">COR_PRF_MONITOR 列挙型</span><span class="sxs-lookup"><span data-stu-id="17b0a-127">COR_PRF_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 [<span data-ttu-id="17b0a-128">ICorProfilerInfo5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="17b0a-128">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
