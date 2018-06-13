---
title: ICorDebug インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebug
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug
helpviewer_keywords:
- ICorDebug interface [.NET Framework debugging]
ms.assetid: 33f431d7-ab1a-494d-8af2-20ab15aba194
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74c5036bdc8a4a75e5711c6dc1d34d8f2c21128f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408672"
---
# <a name="icordebug-interface"></a>ICorDebug インターフェイス
開発者は、共通言語ランタイム (CLR) 環境でアプリケーションをデバッグできるようにするメソッドを提供します。  
  
> [!NOTE]
>  Windows 95、Windows 98 または Windows ME、または (IA64、AMD64 など) と x86 以外のプラットフォームでは、混合モード (マネージとネイティブ コード) デバッグはサポートされていません。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CanLaunchOrAttach メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebug-canlaunchorattach-method.md)|現在のコンピューターおよびランタイムの構成のコンテキスト内で、新しいプロセスの起動または特定のプロセスへのアタッチを実行するかどうかを判断します。|  
|[CreateProcess メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)|プロセスと、デバッガーの制御下で、プライマリ スレッドが起動します。|  
|[DebugActiveProcess メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md)|既存のプロセスにデバッガーをアタッチします。|  
|[EnumerateProcesses メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebug-enumerateprocesses-method.md)|デバッグ中のプロセスの列挙子を取得します。|  
|[GetProcess メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebug-getprocess-method.md)|特定のプロセス ID に置き換えます。"ICorDebugProcess"オブジェクトを返します|  
|[Initialize メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)|初期化、`ICorDebug`オブジェクト。|  
|[SetManagedHandler メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)|マネージ イベントのイベント ハンドラー オブジェクトを指定します。|  
|[SetUnmanagedHandler メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebug-setunmanagedhandler-method.md)|管理されていないイベントのイベント ハンドラー オブジェクトを指定します。|  
|[Terminate メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)|終了、`ICorDebug`オブジェクト。|  
  
## <a name="remarks"></a>コメント  
 `ICorDebug` デバッガー プロセスのイベントの処理ループを表します。 デバッガーが待つ必要があります、 [icordebugmanagedcallback::exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)このインターフェイスを解放する前に、デバッグ中のすべてのプロセスからのコールバック。  
  
 `ICorDebug`オブジェクトは、初期のオブジェクトをさらに管理されているすべてのデバッグを制御します。 .NET Framework version 1.0 および 1.1 では、このオブジェクトは、 `CoClass` COM から作成されたオブジェクト .NET Framework version 2.0 では、このオブジェクトが不要になった、`CoClass`オブジェクト。 作成する必要があります、 [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md)は複数のバージョンに対応する関数。 この新しい作成関数により、クライアントの特定の実装を取得する`ICorDebug`もに、デバッグ API の特定のバージョンをエミュレートします。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
