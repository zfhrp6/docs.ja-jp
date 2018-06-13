---
title: ICorDebugGenericValue Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue
helpviewer_keywords:
- ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: bc14f408-b359-4c8c-ade2-888ccdf7261b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0081f020da673023e2c35f9599e9682215e2c9d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415065"
---
# <a name="icordebuggenericvalue-interface1"></a>ICorDebugGenericValue Interface1
すべての値に適用される"ICorDebugValue"のサブクラスです。 このインターフェイスは、値に対して Get メソッドと Set メソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-getvalue-method.md)|値が指定されたバッファーにコピーします。|  
|[SetValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)|指定されたバッファーから新しい値をコピーします。|  
  
## <a name="remarks"></a>コメント  
 `ICorDebugGenericValue` 非リモート化可能になっているために、サブ インターフェイスです。  
  
 参照型の値は、参照の内容ではなく、参照です。  
  
 このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
    
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
