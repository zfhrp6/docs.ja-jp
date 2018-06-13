---
title: ICorProfilerCallback::ExceptionUnwindFinallyEnter メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFinallyEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyEnter method [.NET Framework profiling]
- ExceptionUnwindFinallyEnter method [.NET Framework profiling]
ms.assetid: c7fab986-b69f-4ec8-b7b7-91dcfc239cd0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a9bd144717decd16a84d2f005d84a22b4ef824d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452232"
---
# <a name="icorprofilercallbackexceptionunwindfinallyenter-method"></a>ICorProfilerCallback::ExceptionUnwindFinallyEnter メソッド
例外のアンワインド フェーズの処理が入ることをプロファイラーに通知、`finally`句が指定された関数に含まれています。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ExceptionUnwindFinallyEnter(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `functionId`  
 [in]含む関数の ID、`finally`句。  
  
## <a name="remarks"></a>コメント  
 プロファイラーでは、スタックは、ガベージ コレクションが実行できる状態ではない可能性がありますので、このメソッドの実装でブロックしないでください、プリエンプティブなガベージ コレクションを有効にできないためです。 ここで、プロファイラーを拒む場合、ガベージ コレクションが試行されると、ランタイムがこのコールバックが戻るまでブロックされます。  
  
 このメソッドのプロファイラーの実装にはマネージ コードへ、または任意の方法で管理されているメモリ割り当てが発生でを呼び出す必要はありません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [GetNotifiedExceptionClauseInfo メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)  
 [ExceptionUnwindFinallyLeave メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)
