---
title: ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5f08f24e16b34d911793b5c8d4a28168f7677b22
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418969"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a>ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode メソッド
[[!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] 以降のバージョンでサポート]  
  
 有効または無効に特定の種類の[ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)例外コールバック。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `enableExceptionsOutsideOfJMC`  
 [入力]  
  
## <a name="remarks"></a>コメント  
 `enableExceptionsOutsideOfJMC` の値が `false` の場合:  
  
-   DEBUG_EXCEPTION_FIRST_CHANCE 例外のコールバックでは、デバッガーにされません。  
  
-   DEBUG_EXCEPTION_CATCH_HANDLER_FOUND 例外は、例外がユーザー コードにエスケープしない場合に、デバッガーにコールバックでは発生しません (つまり、例外の発生から例外ハンドラーへのパスを持たない JustMyCode または JMC とマークされているメソッド)。  
  
 `enableExceptionsOutsideOfJMC` の既定値は `true` です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorDebugProcess8 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
