---
title: ICorProfilerCallback2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2
helpviewer_keywords:
- ICorProfilerCallback2 interface [.NET Framework profiling]
ms.assetid: 4a261dba-450d-4f1f-8d98-865b58bfc992
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c6a218b58ed2ab40505204768f7d6071dea6db5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461051"
---
# <a name="icorprofilercallback2-interface"></a>ICorProfilerCallback2 インターフェイス
プロファイラーがサブスクライブしているイベントが発生したときに、コード プロファイラーに通知を共通言語ランタイム (CLR) によって使用されるメソッドを提供します。 `ICorProfilerCallback2`インターフェイスの拡張機能は、 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)インターフェイスです。 つまり、.NET Framework version 2.0 で導入された新しいコールバックを提供します。  
  
> [!NOTE]
>  各メソッドの実装では、S_OK の失敗した場合に成功した場合、または E_FAIL 上の値を持つ HRESULT を返す必要があります。 現時点では、CLR を除く各コールバックによって返される HRESULT を無視[icorprofilercallback::objectreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)です。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[FinalizeableObjectQueued メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md)|コード プロファイラーに通知を実行するため、ファイナライザー スレッドにファイナライザーを持つオブジェクトがキューに格納されていること、`Finalize`メソッドです。|  
|[GarbageCollectionFinished メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|ガベージ コレクションが完了し、それに対してガベージ コレクションのすべてのコールバックが発行されたことをプロファイラーに通知します。|  
|[GarbageCollectionStarted メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)|ガベージ コレクションが開始されたことをコード プロファイラーに通知します。|  
|[HandleCreated メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)|ガベージ コレクション ハンドルが作成されているコード プロファイラーに通知します。|  
|[HandleDestroyed メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)|ガベージ コレクション ハンドルが破棄されたことをコード プロファイラーに通知します。|  
|[RootReferences2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)|ガベージ コレクションが発生した後は、ルート参照について、プロファイラーを通知します。 このメソッドは、の拡張機能、 [icorprofilercallback::rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)メソッドです。|  
|[SurvivingReferences メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md)|オブジェクト参照はガベージ コレクションで残ったをプロファイラーに通知します。|  
|[ThreadNameChanged メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-threadnamechanged-method.md)|スレッドの名前が変更されたことをコード プロファイラーに通知します。|  
  
## <a name="remarks"></a>コメント  
 CLR のメソッドを呼び出す、 `ICorProfilerCallback` (または`ICorProfilerCallback2`) インターフェイスをプロファイラーがサブスクライブされる、イベント プロファイラーに通知が発生します。 これは、CLR が、コード プロファイラーとの通信に使用するプライマリのコールバック インターフェイスです。  
  
 コード プロファイラーでのメソッドを実装する必要があります、`ICorProfilerCallback`インターフェイスです。 .NET Framework 2.0 とそれ以降のバージョンでは、プロファイラーを実装する必要がありますも、`ICorProfilerCallback2`メソッドです。 各メソッドの実装では、S_OK の失敗した場合に成功した場合、または E_FAIL 上の値を持つ HRESULT を返す必要があります。 現時点では、CLR を除く各コールバックによって返される HRESULT を無視[icorprofilercallback::objectreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)です。  
  
 コード プロファイラーを実装する COM オブジェクトは、Microsoft Windows レジストリに登録する必要があります、`ICorProfilerCallback`と`ICorProfilerCallback2`インターフェイスです。 呼び出して通知を受信するか、イベントをサブスクライブしているコード プロファイラー [icorprofilerinfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)です。 プロファイラーの実装ではこれは、通常[icorprofilercallback::initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)です。 このプロファイラーは、イベントの発生前にまたはが実行中のランタイム プロセスにだけ発生したときに、ランタイムから通知を受信すること。  
  
> [!NOTE]
>  プロファイラーは、1 つの COM オブジェクトを登録します。 その COM オブジェクトが必要がありますのメソッドを実装のみ場合は、プロファイラーは、.NET Framework version 1.0 または 1.1 でのターゲット、`ICorProfilerCallback`です。 .NET Framework version 2.0 がターゲットとすると、後で、COM オブジェクトである必要がありますのメソッドを実装も`ICorProfilerCallback2`します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback3 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 [ICorProfilerCallback4 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
