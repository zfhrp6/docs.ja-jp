---
title: "ICorProfilerCallback7::ModuleInMemorySymbolsUpdated メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name:
- ICorProfiler7.ModuleInMemorySymbolsUpdated
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: f362a896-3247-4894-9727-e48dbbcd2c78
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 898adf043e425c00d6e311e2f67c53ed65cacb33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a>ICorProfilerCallback7::ModuleInMemorySymbolsUpdated メソッド
[.NET Framework 4.6.1 以降のバージョンでのみでサポート]  
  
 メモリ内のモジュールに関連付けられているシンボルのストリームが更新されるたびに、プロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `moduleId`  
 メモリ内のモジュールのシンボルのストリームの更新の識別子。  
  
## <a name="remarks"></a>コメント  
 このコールバックは、設定によって制御されます、 [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)イベント マスク フラグを呼び出すときに、 [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)メソッドです。  
  
> [!NOTE]
>  このイベントは、現在のシンボルに暗黙的に作成または使用して変更は発生しません<xref:System.Reflection.Emit>Api です。  
  
 でもシンボルが指定されたときに前もってマネージのオーバー ロードのいずれかへの呼び出しで<xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType>メソッドを含む、 `rawSymbolStore` runtime、アセンブリのシンボルを指定する引数可能性があります実際には関連付けられませんシンボリック データ モジュールまで後、 [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)コールバックが発生しました。 このイベントは、このようなモジュールのシンボルを収集する以降の機会を提供します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ModuleLoadFinished メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)  
 [SetEventMask2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)  
 [ICorProfilerCallback7 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
