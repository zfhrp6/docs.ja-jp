---
title: ICorDebugStackWalk::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::Next
helpviewer_keywords:
- ICorDebugStackWalk::Next method [.NET Framework debugging]
- Next method, ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 189c36be-028c-4fba-a002-5edfb8fcd07f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 367c43dc08722288dc3b32b5133f7770ffc3a27c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423105"
---
# <a name="icordebugstackwalknext-method"></a>ICorDebugStackWalk::Next メソッド
移動、 [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)次のフレームにオブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Next();  
```  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|ランタイムが正常に次のフレームをアンワインド (「解説」を参照してください)。|  
|E_FAIL|`ICorDebugStackWalk`オブジェクトを advanced されませんでした。|  
|CORDBG_S_AT_END_OF_STACK|このアンワインドの結果として、スタックの終わりに達しました。|  
|CORDBG_E_PAST_END_OF_STACK|フレーム ポインターはスタックの最後に、既にそのため、追加のフレームにはアクセスできません。|  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>コメント  
 `Next`強化され、メソッド、`ICorDebugStackWalk`オブジェクト呼び出し元のフレームにのみ、ランタイムは、現在のフレームをアンワインドできます。 それ以外の場合、オブジェクトは、ランタイムはアンワインドすることが次のフレームを進めます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorDebugStackWalk インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
