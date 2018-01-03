---
title: ICorDebugFrame Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame
helpviewer_keywords: ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 0c48f764-3c64-4602-b2f4-4ffc60eb2c65
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: caa3ef9cd52cc872d4ebc96376c104a7b90fb4f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugframe-interface1"></a>ICorDebugFrame Interface1
現在のスタックのフレームを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CreateStepper メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|この基準としたステップ実行の操作を実行する、ICorDebugStepper を取得`ICorDebugFrame`です。|  
|[GetCallee メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|ポインターを取得、`ICorDebugFrame`このフレームと呼ばれる、またはこの場合、null を返しますが、チェーン内の最も内側のフレームを現在のチェーンにします。|  
|[GetCaller メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|ポインターを取得、`ICorDebugFrame`このフレームと呼ばれる現在のチェーン内またはチェーン内の最も外側のフレームは、この場合、null を返します。|  
|[GetChain メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|これで、ICorDebugChain へのポインターを取得`ICorDebugFrame`の一部です。|  
|[GetCode メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|このスタック フレームに関連付けられている ICorDebugCode へのポインターを取得します。|  
|[GetFunction メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|このスタック フレームに関連付けられているコードを含む ICorDebugFunction へのポインターを取得します。|  
|[GetFunctionToken メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|このスタック フレームに関連付けられているコードを含む関数のメタデータ トークンを取得します。|  
|[GetStackRange メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|これによって表されるスタック フレームの絶対アドレス範囲を取得`ICorDebugFrame`です。|  
  
## <a name="remarks"></a>コメント  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
