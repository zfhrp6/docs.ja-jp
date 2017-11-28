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
# <a name="corprfhighmonitor-enumeration"></a>COR_PRF_HIGH_MONITOR 列挙型
[.NET Framework 4.5.2 以降のバージョンでのみでサポート]  
  
 :Seteventmask2 フラグを提供、 [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)ために、プロファイラーが指定する列挙体、 [icorprofilerinfo 5::seteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)メソッドの読み込み時にします。  
  
## <a name="syntax"></a>構文  
  
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
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|フラグが設定されていません。|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|コントロール、 [icorprofilercallback 6::getassemblyreference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) CLR アセンブリ参照クロージャのウォーク中にアセンブリ参照を追加するためのコールバック。|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|コントロール、 [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)メモリ内のモジュールに関連付けられているシンボルのストリームへの更新のコールバック。|  
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|プロファイルが拡張したイメージを必要とする、`COR_PRF_HIGH_MONITOR` のすべてのフラグを表します。 対応して、`COR_PRF_REQUIRE_PROFILE_IMAGE`フラグ、 [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列挙します。|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|プロファイラーが実行中のアプリケーションに割り当てられた後に設定することが可能な、`COR_PRF_HIGH_MONITOR` のすべてのフラグを表します。|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|初期化の最中にのみ設定できるすべての `COR_PRF_HIGH_MONITOR` フラグを表しています。 他の場所でこれらのフラグを変更しようとすると、エラーを表す `HRESULT` 値が生じます。|  
  
## <a name="remarks"></a>コメント  
 `COR_PRF_HIGH_MONITOR`でフラグを使用して、`pdwEventsHigh`のパラメーター、 [icorprofilerinfo 5::geteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)と[icorprofilerinfo 5::seteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)メソッドです。  
  
 以降で、[!INCLUDE[net_v461](../../../../includes/net-v461-md.md)]の値、`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`する場合は 0 から変更`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`(0x00000002)。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [列挙体のプロファイリング](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
 [COR_PRF_MONITOR 列挙型](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 [ICorProfilerInfo5 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
