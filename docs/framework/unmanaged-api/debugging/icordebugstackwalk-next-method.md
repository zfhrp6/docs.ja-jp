---
title: "ICorDebugStackWalk::Next メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStackWalk.Next Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStackWalk::Next
helpviewer_keywords:
- ICorDebugStackWalk::Next method [.NET Framework debugging]
- Next method, ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 189c36be-028c-4fba-a002-5edfb8fcd07f
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5a776f215d67c381a1c08416927cabd3ccb40afa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICorDebugStackWalk インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
