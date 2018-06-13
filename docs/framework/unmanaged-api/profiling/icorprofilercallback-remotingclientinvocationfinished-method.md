---
title: ICorProfilerCallback::RemotingClientInvocationFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientInvocationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientInvocationFinished
helpviewer_keywords:
- RemotingClientInvocationFinished method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientInvocationFinished method [.NET Framework profiling]
ms.assetid: ea4b283b-1210-4f41-a7a2-c398b1adde4e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ec45b73b496efdbe6328985b5f77f731d8a78cc7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453406"
---
# <a name="icorprofilercallbackremotingclientinvocationfinished-method"></a>ICorProfilerCallback::RemotingClientInvocationFinished メソッド
クライアントで、リモート処理の呼び出しが完了するまで実行をプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT RemotingClientInvocationFinished();  
```  
  
## <a name="remarks"></a>コメント  
 リモート処理の呼び出しが同期すると場合に、も実行が完了、サーバーにします。 リモート処理の呼び出しが非同期で呼び出しを処理するとき、応答可能性があります予想されます。 呼び出しとして発生し、応答が予想される場合は[icorprofilercallback::remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)と呼び出しを`RemotingClientInvocationFinished`を必要なセカンダリの処理の非同期呼び出しを示します。  
  
 同じスレッドでコールバックの組み合わせにより、次のようになります。  
  
-   `RemotingClientInvocationStarted` および[icorprofilercallback::remotingclientsendingmessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)  
  
-   [Icorprofilercallback::remotingclientreceivingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)と[icorprofilercallback::remotingclientinvocationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)  
  
-   [Icorprofilercallback::remotingserverinvocationreturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md)と[icorprofilercallback::remotingserversendingreply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)  
  
 リモート処理のコールバックで次の問題に注意する必要があります。  
  
-   クライアントから呼び出され、サーバー上で実行される関数の通知が正しく受信されていないために、リモート処理関数の実行がプロファイラー API によって反映されません。 プロキシ オブジェクトによって行われ、実際の呼び出し、プロファイラーには、特定の関数は、JIT コンパイルしますが、使用されていないことが表示されます。  
  
-   プロファイラーは、非同期のリモート処理イベントの正確な通知を受信しません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
