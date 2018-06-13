---
title: ICorDebugDebugEvent インターフェイス
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a2543a9629c60fde2b2f14c11898ba3e9df3c82
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419313"
---
# <a name="icordebugdebugevent-interface"></a>ICorDebugDebugEvent インターフェイス
すべての `ICorDebug` デバッグ イベントを派生させる基本インターフェイスを定義します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetEventKind メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|この `ICorDebugDebugEvent` オブジェクトが表すイベントの種類を示します。|  
|[GetThread メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|イベントが発生したスレッドを取得します。|  
  
## <a name="remarks"></a>コメント  
 次のインターフェイスは、`ICorDebugDebugEvent` インターフェイスから派生したものです。  
  
-   [ICorDebugExceptionDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
-   [ICorDebugModuleDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
>  このインターフェイスは .NET ネイティブでのみ使用可能です。 インターフェイス ポインターを取得するために `QueryInterface` を呼び出そうとすると、.NET ネイティブ外の ICorDebug シナリオに対して `E_NOINTERFACE` が返されます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
