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
ms.workload: dotnet
ms.openlocfilehash: b8df7b46bf22fa1a3a8633cbad7ad1a6582b4860
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
