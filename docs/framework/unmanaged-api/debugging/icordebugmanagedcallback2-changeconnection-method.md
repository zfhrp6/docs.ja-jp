---
title: "ICorDebugManagedCallback2::ChangeConnection メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugManagedCallback2.ChangeConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ChangeConnection
helpviewer_keywords:
- ICorDebugManagedCallback2::ChangeConnection method [.NET Framework debugging]
- ChangeConnection method [.NET Framework debugging]
ms.assetid: 7263f9a9-4c0b-4d82-a181-288873fb2b18
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2ba7e84c11f2fc8619b7046e222a742ee3298554
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a>ICorDebugManagedCallback2::ChangeConnection メソッド
指定した接続に関連付けられているタスクのセットが変更されたことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pProcess`  
 [in]変更された接続を含むプロセスを表す"ICorDebugProcess"オブジェクトへのポインター。  
  
 `dwConnectionId`  
 [in]変更された接続の ID。  
  
## <a name="remarks"></a>コメント  
 A`ChangeConnection`コールバックは、次の場合のいずれかで発生します。  
  
-   デバッガーがいつ接続を含むプロセスにアタッチします。 ここでは、ランタイムが生成されディスパッチ、 [icordebugmanagedcallback 2::createconnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md)イベントおよび`ChangeConnection`プロセス内の各接続のイベントです。 A`ChangeConnection`イベントが作成されてからその接続の一連のタスクが変更されたかどうかに関係なく、すべての既存の接続を生成します。  
  
-   ホストが呼び出したとき[iclrdebugmanager::setconnectiontasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)で、 [Hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md)です。  
  
 デバッガーは、新しい変更を取得するプロセスのすべてのスレッドをスキャンする必要があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICorDebugManagedCallback2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [ICorDebugManagedCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
