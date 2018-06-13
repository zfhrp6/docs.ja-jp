---
title: ICorProfilerCallback8::DynamicMethodJITCompilationStarted メソッド
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad74eeb4deeae73be40b3a0bc0f6a18ec2299780
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454751"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a>ICorProfilerCallback8::DynamicMethodJITCompilationStarted メソッド
[.NET Framework 4.7 以降のバージョンでサポート]  
  
動的メソッドの JIT コンパイルが開始されるたびに、プロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        fIsSafeToBlock,   
     [in]  LPCBYTE     pILHeader,   
     [in]  LONG        cbILHeader   
);  
```  
  
#### <a name="parameters"></a>パラメーター  
[入力] `functionId`  
どの JIT のコンパイルが開始したメモリ内の関数の識別子です。   

[in] `fIsSafeToBlock`   
`true` そのブロックを示すためにランタイムになるこのコールバックから戻るには、呼び出し元のスレッドを待機するには`false`をブロックしていないに影響すること、ランタイムの動作を示します。  

[in] `pILHeader`    
メソッドの IL ヘッダーの最初のバイトへのポインター。   

[in] `cbILHeader`    
IL ヘッダー内のバイト数。 

## <a name="remarks"></a>コメント  

動的メソッドが JIT でコンパイルされるたびに、このコールバックがトリガーされます。 これには、さまざまな IL スタブと LCG メソッドが含まれます。 その目標は、ユーザーにコンパイルされたメソッドを識別するための十分な情報を含むプロファイラー ライターを提供します。

> [!NOTE]
> `functionId` 値は、動的メソッドのメタデータがあるないため、メタデータ トークンを解決するのには使用できません。

`pILHeader`ポインターは、コールバック中にのみ有効です。

## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>関連項目  
 [DynamicMethodJITCompilationFinished メソッド](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)  
 [ICorProfilerCallback8 インターフェイス](icorprofilercallback8-interface.md)
