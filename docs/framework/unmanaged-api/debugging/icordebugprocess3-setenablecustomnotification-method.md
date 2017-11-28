---
title: "ICorDebugProcess3::SetEnableCustomNotification メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess3.SetEnableCustomNotification Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess3::SetEnableCustomNotification
helpviewer_keywords:
- ICorDebugProcess3::SetEnableCustomNotification method [.NET Framework debugging]
- SetEnableCustomNotification method [.NET Framework debugging]
ms.assetid: afd88ee9-2589-4461-a75a-9b6fe55a2525
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6d4c6604d57b28cca33007b9d72d4b4c06e6d062
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a>ICorDebugProcess3::SetEnableCustomNotification メソッド
有効にし、指定した型のカスタムのデバッガー通知を無効にします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pClass`  
 [in]カスタムのデバッガー通知を指定する型。  
  
 `fEnable`  
 [in]`true` ; カスタムのデバッガー通知を有効にするには`false`通知を無効にします。 既定値は `false` です。  
  
## <a name="remarks"></a>コメント  
 ときに`fEnable`に設定されている`true`への呼び出し、<xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType>メソッド トリガー、 [icordebugmanagedcallback 3::customnotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)コールバック。 既定では通知が無効になっていますしたがって、デバッガーは、通知の種類が認識しを処理する必要があるを指定する必要があります。 [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)クラスのスコープのアプリケーション ドメインで、デバッガーを呼び出す必要があります`SetEnableCustomNotification`プロセス全体で通知を受信する必要がある場合、プロセスでのアプリケーション ドメインごとにします。  
  
 以降で、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]では、サポートされている通知は、スレッド間の依存関係の通知のみです。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorDebugProcess3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)  
 [デバッグのインターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
