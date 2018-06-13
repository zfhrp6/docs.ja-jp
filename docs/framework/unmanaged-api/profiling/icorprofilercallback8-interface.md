---
title: ICorProfilerCallback8 インターフェイス
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b92120cc5948efca696d922448da215601f9e6b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455284"
---
# <a name="icorprofilercallback8-interface"></a>ICorProfilerCallback8 インターフェイス
[.NET Framework 4.7 以降のバージョンでサポート]  

 サブクラス[ICorProfilerCallback7](icorprofilercallback7-interface.md)動的メソッドの JIT コンパイルが開始して完了したことをプロファイラーに通知する、共通言語ランタイムによって使用されるコールバック メソッドを提供します。 
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[DynamicMethodJITCompilationStarted メソッド](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|動的メソッドの JIT コンパイルが開始されたことをプロファイラーに通知します。|  
|[DynamicMethodJITCompilationFinished メソッド](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|動的メソッドの JIT コンパイルが完了したことをプロファイラーに通知します。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
**.NET framework のバージョン:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>関連項目  
[プロファイリングのインターフェイス](profiling-interfaces.md)   
[ICorProfilerCallback9 インターフェイス](icorprofilercallback9-interface.md)
