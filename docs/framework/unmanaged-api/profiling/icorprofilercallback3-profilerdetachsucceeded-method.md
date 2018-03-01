---
title: "ICorProfilerCallback3::ProfilerDetachSucceeded メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback3.ProfilerDetachSucceeded Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerDetachSucceeded
helpviewer_keywords:
- ProfilerDetachSucceeded method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerDetachSucceeded method [.NET Framework profiling]
ms.assetid: 05164966-16ce-4cc9-a530-43a640c00711
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d06671917094752287836800ebc492d5f0a5b595
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a>ICorProfilerCallback3::ProfilerDetachSucceeded メソッド
共通言語ランタイム (CLR: Common Language Runtime) がプロファイラー DLL をアンロードしようとしていることをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a>戻り値  
 このコールバックからの戻り値は無視されます。  
  
## <a name="remarks"></a>コメント  
 `ProfilerDetachSucceeded` コールバックは、すべてのスレッドでプロファイラーのコードが終了した後に発行されます。 このメソッドが呼び出された場合、プロファイラーは、そのデストラクターに適さない最後の段階のタスク (その UI またはログ コンポーネントの通知など) を実行する必要があります。 ただし、プロファイラーを呼び出してはならない関数、CLR によってこのコールバック中に用意されているインターフェイスで (など、 [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)または`IMetaData*`インターフェイス)。  
  
 CLR は Windows アプリケーション イベント ログに、デタッチ操作が成功したことを示すエントリを作成します。  
  
 プロファイラーがこのコールバックから戻ると、CLR はプロファイラー オブジェクトを解放し、プロファイラー DLL をアンロードします。 したがって、プロファイラーは、コールバックから戻った後にプロファイラー DLL 内での実行を発生させるアクションを実行することはできません。 たとえば、プロファイラーは、スレッドを作成することも、タイマー コールバックを登録することもできません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [メタデータ インターフェイス](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [ICorProfilerInfo3 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [プロファイル](../../../../docs/framework/unmanaged-api/profiling/index.md)
