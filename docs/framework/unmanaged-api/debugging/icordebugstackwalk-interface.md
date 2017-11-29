---
title: "ICorDebugStackWalk インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStackWalk
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStackWalk
helpviewer_keywords: ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 16d695e8-975d-431b-8421-e9e6c3e3f476
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0c8a4421b716614081368755388bd2ab8d8fe22e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugstackwalk-interface"></a>ICorDebugStackWalk インターフェイス
スレッドのスタック上のマネージ メソッド (フレーム) を取得するメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetContext メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)|現在のフレームのコンテキストを返します、`ICorDebugStackWalk`オブジェクト。|  
|[SetContext メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)|セット、`ICorDebugStackWalk`オブジェクトの現在のコンテキストのスレッドの有効なコンテキストにします。|  
|[Next メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)|移動、`ICorDebugStackWalk`次のフレームにオブジェクト。|  
|[GetFrame メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getframe-method.md)|内の現在のフレームを取得、`ICorDebugStackWalk`オブジェクト。|  
  
## <a name="remarks"></a>コメント  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグのインターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
