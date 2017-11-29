---
title: ICorDebugHandleValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHandleValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHandleValue
helpviewer_keywords: ICorDebugHandleValue interface [.NET Framework debugging]
ms.assetid: 66fcd2b8-ac66-414b-83a8-75a925e17772
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b56c23caaaed2bc63c724769db1198fd088f7f1a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebughandlevalue-interface1"></a>ICorDebugHandleValue Interface1
デバッガーにガベージ コレクションのハンドルが作成の参照値を表す ICorDebugReferenceValue のサブクラスです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Dispose メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|これによって参照されるハンドルを解放`ICorDebugHandleValue`せず、インターフェイス ポインターを明示的に解放するオブジェクト。|  
|[GetHandleType メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|これによって参照されるハンドルの種類を記述する CorDebugHandleType 値を取得`ICorDebugHandleValue`です。|  
  
## <a name="remarks"></a>コメント  
 `ICorDebugReferenceValue`オブジェクトがデバッグ対象のコードの実行の中断によって無効にします。 `ICorDebugHandleValue`が明示的に解放されるまで、改ページして、継続は、その参照を維持します。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグのインターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
