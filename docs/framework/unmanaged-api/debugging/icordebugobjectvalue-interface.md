---
title: ICorDebugObjectValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugObjectValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugObjectValue
helpviewer_keywords: ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 937de6a0-6fbf-4ddc-80ea-a6217b73e62b
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: acbfbbb8f7374b1ab783371d318bd3bcf89963fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugobjectvalue-interface1"></a>ICorDebugObjectValue Interface1
オブジェクトを格納する値を表す"ICorDebugValue"のサブクラスです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetClass メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|共通言語ランタイム (CLR) へのインターフェイス ポインターを取得<xref:System.Type>オブジェクトのこの`ICorDebugObjectValue`参照します。|  
|[GetContext メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|実装されていません。|  
|[GetFieldValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|インターフェイス ポインターを取得、 [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md)を表す、指定したクラスの指定したフィールドの値。|  
|[GetManagedCopy メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|互換性のために残されています。 このメソッドを呼び出さないでください。|  
|[GetVirtualMethod メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|実装されていません。|  
|[IsValueClass メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|これによって、オブジェクトが参照されるかどうかを示す値を取得`ICorDebugObjectValue`は値型です。|  
|[SetFromManagedCopy メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|互換性のために残されています。 このメソッドを呼び出さないでください。|  
  
## <a name="remarks"></a>コメント  
 `ICorDebugObjectValue`デバッグ中のプロセスの続行まで有効のままです。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグのインターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 
