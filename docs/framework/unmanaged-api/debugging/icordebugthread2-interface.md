---
title: ICorDebugThread2 Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugThread2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2
helpviewer_keywords:
- ICorDebugThread2 interface [.NET Framework debugging]
ms.assetid: 678f89f9-cce7-46d1-af87-5e989abaa93c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c348cf28a6330523d1a490c136a3214e37d13f4c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423050"
---
# <a name="icordebugthread2-interface1"></a>ICorDebugThread2 Interface1
ICorDebugThread インターフェイスを論理的に拡張として機能します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetActiveFunctions メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|スレッドのフレームでアクティブな関数に関するデータを含む COR_ACTIVE_FUNCTION インスタンスの配列を取得します。|  
|[GetConnectionID メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|この接続の識別子を取得`ICorDebugThread2`です。|  
|[GetTaskID メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|このタスクの識別子を取得`ICorDebugThread2`です。|  
|[GetVolatileOSThreadID メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|このオペレーティング システムのスレッド識別子を取得`ICorDebugThread2`です。|  
|[InterceptCurrentException メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|スレッドで現在の例外をインターセプトするデバッガーを使用します。|  
  
## <a name="remarks"></a>コメント  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
