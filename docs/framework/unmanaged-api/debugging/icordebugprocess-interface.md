---
title: ICorDebugProcess Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess
helpviewer_keywords: ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: be86f4b5-418a-4c5c-a67c-97148c65ed8c
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d6fa95d17e7ff6f857765ea2dd48f61b047a47b1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess-interface1"></a>ICorDebugProcess Interface1
マネージ コードを実行しているプロセスを表します。 このインターフェイスは、ICorDebugController のサブクラスです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ClearCurrentException メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|特定のスレッドで現在のアンマネージ例外をクリアします。|  
|[EnableLogMessages メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|有効にし、デバッガーへのログ メッセージの送信を無効にします。|  
|[EnumerateAppDomains メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|すべてのプロセスのアプリケーション ドメインを列挙します。|  
|[EnumerateObjects メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|実装されていません。|  
|[GetHandle メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|プロセスへのハンドルを取得します。|  
|[GetHelperThreadID メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|デバッガーの内部ヘルパー スレッドのオペレーティング システム (OS) のスレッド ID を取得します。|  
|[GetID メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|プロセスのオペレーティング システム (OS) の ID を取得します。|  
|[GetObject メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|実装されていません。|  
|[GetThread メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|取得しますが、指定された OS スレッドをある ICorDebugThread インスタンスの id。|  
|[GetThreadContext メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|特定のスレッドのコンテキストを取得します。|  
|[IsOSSuspended メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|デバッガーがプロセスを停止したため、スレッドが中断されたかどうかを判断します。|  
|[IsTransitionStub メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|マネージ コードへの遷移を発生させるスタブ内にアドレスがあるかどうかを判断します。|  
|[ModifyLogSwitch メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|指定したログ スイッチの重大度レベルを設定します。|  
|[ReadMemory メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|プロセスからメモリを読み取ります。|  
|[SetThreadContext メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|特定のスレッドのコンテキストを設定します。|  
|[ThreadForFiberCookie メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|使用しないでください。|  
|[WriteMemory メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|プロセスのメモリの領域にデータを書き込みます。|  
  
## <a name="remarks"></a>コメント  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
