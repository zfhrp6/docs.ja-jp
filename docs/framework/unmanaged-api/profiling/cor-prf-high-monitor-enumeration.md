---
title: COR_PRF_HIGH_MONITOR 列挙型
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c92ba2b5eac5eb1368a7d7ccf3b666886f4ca92a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454715"
---
# <a name="corprfhighmonitor-enumeration"></a><span data-ttu-id="19643-102">COR_PRF_HIGH_MONITOR 列挙型</span><span class="sxs-lookup"><span data-stu-id="19643-102">COR_PRF_HIGH_MONITOR Enumeration</span></span>
<span data-ttu-id="19643-103">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="19643-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="19643-104">:Seteventmask2 フラグを提供、 [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)ために、プロファイラーが指定する列挙体、 [icorprofilerinfo 5::seteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)メソッドの読み込み時にします。</span><span class="sxs-lookup"><span data-stu-id="19643-104">Provides flags in addition to those found in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19643-105">構文</span><span class="sxs-lookup"><span data-stu-id="19643-105">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_HIGH_MONITOR_NONE                     = 0x00000000,  
    COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES          = 0x00000001,  
    COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED        = 0x00000002,     
    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS = 0x00000004,    
    COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE            = 0,  
    COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH           = COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | 
                                                    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS,  
    COR_PRF_HIGH_MONITOR_IMMUTABLE                = 0  
} COR_PRF_HIGH_MONITOR;  
```  
  
## <a name="members"></a><span data-ttu-id="19643-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="19643-106">Members</span></span>  
  
|<span data-ttu-id="19643-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="19643-107">Member</span></span>|<span data-ttu-id="19643-108">説明</span><span class="sxs-lookup"><span data-stu-id="19643-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|<span data-ttu-id="19643-109">フラグが設定されていません。</span><span class="sxs-lookup"><span data-stu-id="19643-109">No flags are set.</span></span>|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|<span data-ttu-id="19643-110">コントロール、 [icorprofilercallback 6::getassemblyreference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) CLR アセンブリ参照クロージャのウォーク中にアセンブリ参照を追加するためのコールバック。</span><span class="sxs-lookup"><span data-stu-id="19643-110">Controls the [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback for adding assembly references during the CLR assembly reference closure walk.</span></span>|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|<span data-ttu-id="19643-111">コントロール、 [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)メモリ内のモジュールに関連付けられているシンボルのストリームへの更新のコールバック。</span><span class="sxs-lookup"><span data-stu-id="19643-111">Controls the [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) callback for updates to the symbol stream associated with an in-memory module.</span></span>|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|<span data-ttu-id="19643-112">コントロール、 [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md)が動的メソッドのガベージされたを示すためのコールバックが収集され、アンロードされます。</span><span class="sxs-lookup"><span data-stu-id="19643-112">Controls the [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) callback for indicating when a dynamic method has been garbage collected and unloaded.</span></span> <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|   
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="19643-113">プロファイルが強化されたイメージを必要とするすべての `COR_PRF_HIGH_MONITOR` フラグを表しています。</span><span class="sxs-lookup"><span data-stu-id="19643-113">Represents all `COR_PRF_HIGH_MONITOR` flags that require profile-enhanced images.</span></span> <span data-ttu-id="19643-114">対応して、`COR_PRF_REQUIRE_PROFILE_IMAGE`フラグ、 [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列挙します。</span><span class="sxs-lookup"><span data-stu-id="19643-114">It corresponds to the `COR_PRF_REQUIRE_PROFILE_IMAGE` flag in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="19643-115">プロファイラーが実行しているアプリケーションにアタッチされた後に設定できるすべての `COR_PRF_HIGH_MONITOR` フラグを表しています。</span><span class="sxs-lookup"><span data-stu-id="19643-115">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span>|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|<span data-ttu-id="19643-116">初期化の最中にのみ設定できるすべての `COR_PRF_HIGH_MONITOR` フラグを表しています。</span><span class="sxs-lookup"><span data-stu-id="19643-116">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="19643-117">他の場所でこれらのフラグを変更しようとすると、エラーを表す `HRESULT` 値が生じます。</span><span class="sxs-lookup"><span data-stu-id="19643-117">Trying to change any of these flags elsewhere results in an `HRESULT` value that indicates failure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19643-118">コメント</span><span class="sxs-lookup"><span data-stu-id="19643-118">Remarks</span></span>  
 <span data-ttu-id="19643-119">`COR_PRF_HIGH_MONITOR`でフラグを使用して、`pdwEventsHigh`のパラメーター、 [icorprofilerinfo 5::geteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)と[icorprofilerinfo 5::seteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="19643-119">The `COR_PRF_HIGH_MONITOR` flags are used with the `pdwEventsHigh` parameter of the [ICorProfilerInfo5::GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) and [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) methods.</span></span>  
  
<span data-ttu-id="19643-120">以降で、[!INCLUDE[net_v461](../../../../includes/net-v461-md.md)]の値、`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`する場合は 0 から変更`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`(0x00000002)。</span><span class="sxs-lookup"><span data-stu-id="19643-120">Starting with the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)], the value of the `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` changed from 0 to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span></span> <span data-ttu-id="19643-121">.NET Framework 4.7.2 から始めて、その値がから変更`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`に`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`です。</span><span class="sxs-lookup"><span data-stu-id="19643-121">Starting with the .NET Framework 4.7.2, its value changed from `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span></span>   

<span data-ttu-id="19643-122">`COR_PRF_HIGH_MONITOR_IMMUTABLE` 初期化中にのみ設定可能なすべてのフラグを表すビットマスクを指定するためのものがします。</span><span class="sxs-lookup"><span data-stu-id="19643-122">`COR_PRF_HIGH_MONITOR_IMMUTABLE` is intended to be a bitmask that represents all flags that can only be set during initialization.</span></span> <span data-ttu-id="19643-123">別の場所での結果、失敗したこれらのフラグのいずれかを変更しようとしています。`HRESULT`です。</span><span class="sxs-lookup"><span data-stu-id="19643-123">Trying to change any of these flags elsewhere results in a failed `HRESULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="19643-124">要件</span><span class="sxs-lookup"><span data-stu-id="19643-124">Requirements</span></span>  
 <span data-ttu-id="19643-125">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="19643-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19643-126">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="19643-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="19643-127">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19643-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19643-128">**.NET framework のバージョン:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19643-128">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19643-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="19643-129">See Also</span></span>  
 [<span data-ttu-id="19643-130">列挙型のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="19643-130">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
 [<span data-ttu-id="19643-131">COR_PRF_MONITOR 列挙型</span><span class="sxs-lookup"><span data-stu-id="19643-131">COR_PRF_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 [<span data-ttu-id="19643-132">ICorProfilerInfo5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="19643-132">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
