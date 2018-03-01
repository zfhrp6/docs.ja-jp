---
title: "ICorProfilerCallback::ExceptionCatcherEnter メソッド"
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
- ICorProfilerCallback.ExceptionCatcherEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter method [.NET Framework profiling]
- ExceptionCatcherEnter method [.NET Framework profiling]
ms.assetid: 41462329-a648-46f0-ae6d-728b94c31aa9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a72b2e75ee622bab357046ff29fac4aa9223d7a0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a>ICorProfilerCallback::ExceptionCatcherEnter メソッド
適切な制御が渡されることをプロファイラーに通知`catch`ブロックします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `functionId`  
 [in]含む関数の識別子、`catch`ブロックします。  
  
 `objectId`  
 [in]処理中の例外の識別子。  
  
## <a name="remarks"></a>コメント  
 `ExceptionCatcherEnter` ・ イン タイム (JIT) コンパイラでコンパイルされたコードでキャッチ ポイントがある場合にのみ、メソッドが呼び出されます。 アンマネージ コードで、またはランタイムの内部のコードにキャッチされる例外には、この通知は呼び出しません。 `objectId`値は再度、ガベージ コレクションからオブジェクトが移動した可能性がありますので、`ExceptionThrown`通知します。  
  
 プロファイラーでは、スタックは、ガベージ コレクションが実行できる状態ではない可能性がありますので、このメソッドの実装でブロックしないでください、プリエンプティブなガベージ コレクションを有効にできないためです。 ここで、プロファイラーを拒む場合、ガベージ コレクションが試行されると、ランタイムがこのコールバックが戻るまでブロックされます。  
  
 このメソッドのプロファイラーの実装にはマネージ コードへ、または任意の方法で管理されているメモリ割り当てが発生でを呼び出す必要はありません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ExceptionCatcherLeave メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)
