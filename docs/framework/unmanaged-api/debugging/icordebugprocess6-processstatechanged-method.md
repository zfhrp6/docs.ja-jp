---
title: "ICorDebugProcess6::ProcessStateChanged メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 22fe068af577c3c3eb056acae388747f88d3f8df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess6processstatechanged-method"></a>ICorDebugProcess6::ProcessStateChanged メソッド
通知[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)プロセスを実行しています。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `change`  
 [in]メンバー、 [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)列挙型  
  
## <a name="remarks"></a>コメント  
 デバッガーに通知するには、このメソッドを呼び出して[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)プロセスを実行しています。  
  
> [!NOTE]
>  このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorDebugProcess6 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [デバッグのインターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
