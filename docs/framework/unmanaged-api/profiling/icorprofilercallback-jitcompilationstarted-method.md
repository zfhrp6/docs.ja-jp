---
title: ICorProfilerCallback::JITCompilationStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationStarted
helpviewer_keywords:
- JITCompilationStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationStarted method [.NET Framework profiling]
ms.assetid: 31782b36-d311-4518-8f45-25f65385af5b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1fa1081afc77c8116d8858c187401555409b4dcd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453982"
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a>ICorProfilerCallback::JITCompilationStarted メソッド
関数をコンパイル ・ イン タイム (JIT) コンパイラが開始されたことをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `functionId`  
 [in]コンパイルの開始を関数の ID。  
  
 `fIsSafeToBlock`  
 [in]プロファイラーをブロックするかどうかを示す値は、ランタイムの動作に影響されます。 値が`true`ブロックにより、ランタイムでこのコールバックから戻るには、呼び出し元のスレッドを待機する場合は、それ以外の場合、`false`です。  
  
 値が`true`は妨げられませんが、ランタイム、プロファイルの結果の傾斜を実行できます。  
  
## <a name="remarks"></a>コメント  
 2 つ以上のペアを受信することは`JITCompilationStarted`と[icorprofilercallback::jitcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)各関数の方法により、ランタイム ハンドル クラス コンス トラクターを呼び出します。 たとえば、ランタイム JIT コンパイル メソッド A を開始がクラス B のクラス コンス トラクターを実行する必要があります。 したがって、ランタイム JIT コンパイル クラス B のコンス トラクターおよびそれを実行します。 コンス トラクターが実行されている、メソッド、メソッドを JIT コンパイルもう一度 A A への呼び出しになります。 このシナリオでは、メソッド A の最初の JIT コンパイルは中断されます。 ただし、JIT コンパイル メソッド A に両方の試行は、JIT コンパイル イベントで報告されます。 プロファイラーを呼び出してメソッド A の Microsoft intermediate language (MSIL) コードを交換する場合は、 [icorprofilerinfo::setilfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)メソッド、両方のようにする必要があります`JITCompilationStarted`可能性があります、同じ MSIL ブロックを使用して、イベントが、両方です。  
  
 プロファイラーは、場合は、2 つのスレッドでは、コールバックを行う同時に JIT コールバックのシーケンスをサポートする必要があります。 たとえば、スレッド A が`JITCompilationStarted`です。 ただし、スレッド A 呼び出し前に`JITCompilationFinished`、スレッド B 呼び出し[icorprofilercallback::exceptionsearchfunctionenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) A のスレッドから関数の ID を持つ`JITCompilationStarted`コールバック。 関数の ID がないまだ有効であることが表示されるためへの呼び出し`JITCompilationFinished`がまだ受信されていません、プロファイラーによってです。 ただし、このような場合は、関数の ID は有効です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [JITCompilationFinished メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
