---
title: ICorProfilerCallback8::DynamicMethodJITCompilationFinished メソッド
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49b5ead8b5428d855b7dab81dced1de6325fd07b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454998"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a>ICorProfilerCallback8::DynamicMethodJITCompilationFinished メソッド
[.NET Framework 4.7 以降のバージョンでサポート]  
  
動的メソッドの JIT コンパイルが完了したときに、プロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
#### <a name="parameters"></a>パラメーター  
[入力] `functionId`  
どの JIT のコンパイルが開始したメモリ内の関数の識別子です。   

[in] `hrStatus`   
JIT コンパイルが成功したかどうかを示す値。

[in] `fIsSafeToBlock`   
`true` そのブロックを示すためにランタイムになるこのコールバックから戻るには、呼び出し元のスレッドを待機するには`false`をブロックしていないに影響すること、ランタイムの動作を示します。  

## <a name="remarks"></a>コメント  

動的メソッドの JIT コンパイルが完了するたびに、このコールバックがトリガーされます。 これには、さまざまな IL スタブと LCG メソッドが含まれます。 その目標は、ユーザーにコンパイルされたメソッドを識別するための十分な情報を含むプロファイラー ライターを提供します。

> [!NOTE]
> `functionId` 値は、動的メソッドのメタデータがあるないため、メタデータ トークンを解決するのには使用できません。

## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>関連項目  
 [DynamicMethodJITCompilationStarted メソッド](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)  
 [ICorProfilerCallback8 インターフェイス](icorprofilercallback8-interface.md)
