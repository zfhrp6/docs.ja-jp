---
title: ICorProfilerCallback4::ReJITError メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITError
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITError
helpviewer_keywords:
- ReJITError method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITError method [.NET Framework profiling]
ms.assetid: d7888aa9-dfaa-420f-9f99-e06ab35ca482
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ec6472a33c49d9345793d73ac2f78f8896dc218b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454819"
---
# <a name="icorprofilercallback4rejiterror-method"></a>ICorProfilerCallback4::ReJITError メソッド
・ イン タイム (JIT) コンパイラが再コンパイル プロセスでエラーが発生したことをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `moduleID`  
 [in]`ModuleID`再コンパイルが失敗した試行が行われる。  
  
 `methodId`  
 [in]`MethodDef`再コンパイルが失敗した試行が行われたメソッドの。  
  
 `functionId`  
 [in]再コンパイルまたは用にマークの再コンパイルされている関数のインスタンス。 この値は、 `NULL` (たとえば、プロファイラーには、再コンパイルするメソッドを無効なメタデータ トークンが指定された) 場合、インスタンス化ごとにではなくメソッドごとに障害が発生したかどうか。  
  
 `hrStatus`  
 [in]エラーの性質を示す HRESULT。 値の一覧については、状態 HRESULT」を参照してください。  
  
## <a name="return-value"></a>戻り値  
 このコールバックからの戻り値は無視されます。  
  
## <a name="status-hresults"></a>状態 HRESULT  
  
|状態配列 HRESULT|説明|  
|--------------------------|-----------------|  
|E_INVALIDARG|`moduleID`または`methodDef`トークンが`NULL`です。|  
|CORPROF_E_DATAINCOMPLETE|モジュールが完全に読み込まれていないか、またはアンロード中です。|  
|CORPROF_E_MODULE_IS_DYNAMIC|指定されたモジュールが動的に生成された (などによって、 `Reflection.Emit`)、このメソッドでサポートされないためです。|  
|CORPROF_E_FUNCTION_IS_COLLECTIBLE|メソッドは、回収可能アセンブリにインスタンス化であるため再コンパイルすることができません。 型および非リフレクション コンテキストで定義された関数 (たとえば、 `List<MyCollectibleStruct>`) 回収可能アセンブリにインスタンス化することができます。|  
|E_OUTOFMEMORY|CLR は JIT 再コンパイルの指定したメソッドをマークしているときにメモリ不足になりました。|  
|その他|オペレーティング システムは、CLR 制御範囲外のエラーを返しました。 たとえば、メモリのページのアクセスの保護を変更するシステム呼び出しが失敗した場合、オペレーティング システム エラーが表示されます。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback4 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
