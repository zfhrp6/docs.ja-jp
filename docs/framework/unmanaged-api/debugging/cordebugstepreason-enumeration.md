---
title: CorDebugStepReason 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugStepReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugStepReason
helpviewer_keywords:
- CorDebugStepReason enumeration [.NET Framework debugging]
ms.assetid: fe248069-b33c-48e1-a777-06ac9b239c54
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71dcc34fd3489fc71cec4050b168548927833082
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404532"
---
# <a name="cordebugstepreason-enumeration"></a>CorDebugStepReason 列挙型
個々のステップの結果を示します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum CorDebugStepReason {  
    STEP_NORMAL,  
    STEP_RETURN,  
    STEP_CALL,  
    STEP_EXCEPTION_FILTER,  
    STEP_EXCEPTION_HANDLER,  
    STEP_INTERCEPT,  
    STEP_EXIT  
} CorDebugStepReason;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`STEP_NORMAL`|同じ関数内で、ステップ実行が通常は、完了しました。|  
|`STEP_RETURN`|ステップ実行は継続通常は、関数が返された後。|  
|`STEP_CALL`|新しく呼び出された関数の先頭には通常、継続のステップします。|  
|`STEP_EXCEPTION_FILTER`|例外が生成され、例外フィルターにコントロールが渡されました。|  
|`STEP_EXCEPTION_HANDLER`|例外が発生しました、制御、例外ハンドラーに渡されました。|  
|`STEP_INTERCEPT`|コントロールは、インターセプターに渡されました。|  
|`STEP_EXIT`|ステップが完了する前に、スレッドが終了しました。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [StepComplete メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)  
 [列挙型のデバッグ](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
