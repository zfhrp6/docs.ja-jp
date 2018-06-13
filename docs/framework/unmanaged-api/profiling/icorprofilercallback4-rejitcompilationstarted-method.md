---
title: ICorProfilerCallback4::ReJITCompilationStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationStarted
helpviewer_keywords:
- ReJITCompilationStarted method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITCompilationStarted method [.NET Framework profiling]
ms.assetid: 512fdd00-262a-4456-a075-365ef4133c4d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d3e21d42340378c576bfc65750fba26a257b82cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33457747"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a>ICorProfilerCallback4::ReJITCompilationStarted メソッド
関数を再コンパイルする・ イン タイム (JIT) コンパイラが開始されたことをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ReJITCompilationStarted(   
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `functionId`  
 [in]JIT コンパイラが再コンパイルを開始したこと、関数の ID。  
  
 `rejitId`  
 [in]関数の新しいバージョンの再コンパイルの ID です。  
  
 `fIsSafeToBlock`  
 [in]`true`ブロックことにより、ランタイムでこのコールバックから戻るには、呼び出し元のスレッドの待機を示すために`false`をブロックしていないに影響すること、ランタイムの動作を示します。 値`true`、実行時に問題が発生しませんが、プロファイルの結果に影響を与えることができます。  
  
## <a name="remarks"></a>コメント  
 2 つ以上のペアを受信することは`ReJITCompilationStarted`と[ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)メソッドの各関数の方法により、ランタイム ハンドル クラス コンス トラクターを呼び出します。 たとえば、ランタイム メソッド A には、再コンパイルを開始が、クラス B のクラス コンス トラクターを実行する必要があります。 そのため、ランタイムは、クラス B のコンス トラクターを再コンパイルし、それを実行します。 コンス トラクターが実行されている、メソッド、もう一度再コンパイルするメソッド A A への呼び出しになります。 このシナリオでは、メソッド A の最初の再コンパイルは中断されます。 ただし、両方は、メソッドの JIT 再コンパイル イベントで報告されるされます再コンパイルを試みます。  
  
 プロファイラーは、場合は、2 つのスレッドでは、コールバックを行う同時に JIT 再コンパイルのコールバックのシーケンスをサポートする必要があります。 たとえば、スレッド A が`ReJITCompilationStarted`ですただし、スレッド A 呼び出し前に[ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)、スレッド B 呼び出し[icorprofilercallback::exceptionsearchfunctionenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)関数の ID を持つ。`ReJITCompilationStarted`スレッド A のコールバック関数の ID がないまだ有効であることが表示されるためへの呼び出し[ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)がまだ受信されていません、プロファイラーによってです。 ただし、この場合、関数の ID は有効です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback4 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 [JITCompilationFinished メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)  
 [ReJITCompilationFinished メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)
