---
title: "ICorDebugManagedCallback3::CustomNotification メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback3.CustomNotification Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback3::CustomNotification
helpviewer_keywords:
- ICorDebugManagedCallback3::CustomNotification method [.NET Framework debugging]
- CustomNotification method [.NET Framework debugging]
ms.assetid: 5e5422ac-afa1-403d-a894-2d7348673e38
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9c42443b0d1e355d4233909357c341763298160e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback3customnotification-method"></a>ICorDebugManagedCallback3::CustomNotification メソッド
カスタムのデバッガー通知が発生したことを示します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CustomNotification(ICorDebugThread *    pThread,  
                           ICorDebugAppDomain * pAppDomain);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pThread`  
 [in]通知を発生させたスレッドへのポインター。  
  
 `pAppDomain`  
 [in]通知を発生させた、スレッドがあるアプリケーション ドメインへのポインター。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>コメント  
 後続の呼び出し、 [icordebugthread 4::getcurrentcustomdebuggernotification](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md)メソッドに渡されたスレッド オブジェクトを取得、<xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType>メソッドです。 スレッド オブジェクトの種類あります以前有効になっているを呼び出して、 [icordebugprocess 3::setenablecustomnotification](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md)メソッドです。 デバッガーは、スレッド オブジェクトのフィールドを型固有のパラメーターを読み取ることができ、フィールドに応答を格納することができます。  
  
 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)インターフェイスは、通知またはその内容の種類のポリシーはありませんし、通知のセマンティクスは、デバッガー、アプリケーション、および .NET Framework 間のコントラクトでは厳密にします。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICorDebugManagedCallback3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
