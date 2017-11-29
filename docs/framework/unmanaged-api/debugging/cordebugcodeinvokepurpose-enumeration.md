---
title: "CorDebugCodeInvokePurpose 列挙体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugInvokePurpose
api_location: mscordbi.dll
api_type: COM
ms.assetid: 31833a2d-a0d6-48a1-b05f-995ca307a08f
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 41938a11d7d92fd728772aa45bd8e97f137e5d69
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a>CorDebugCodeInvokePurpose 列挙体
エクスポートされた関数がマネージ コードを呼び出す理由を示します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum CorDebugCodeInvokePurpose  
{  
    CODE_INVOKE_PURPOSE_NONE,  
    CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION,    
    CODE_INVOKE_PURPOSE_CLASS_INIT,  
    CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH,  
} CorDebugCodeInvokePurpose;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`CODE_INVOKE_PURPOSE_NONE`|None または不明です。|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|マネージ コードは、逆 p-invoke などのすべてのマネージ エントリ ポイントを実行します。 より詳細な目的は、ランタイムによって認識されません。|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|マネージ コードは、静的コンストラクターを実行します。|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|マネージ コードは、呼び出されたいくつかのインターフェイス メソッドの実装を実行します。|  
  
## <a name="remarks"></a>コメント  
 この列挙体を使って、 [icordebugprocess 6::getexportstepinfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md)マネージ コードをステップ実行に関する情報を提供するメソッド。  
  
> [!NOTE]
>  この列挙体は .NET ネイティブのデバッグ シナリオのみで使用することを目的としています。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [列挙体のデバッグ](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
