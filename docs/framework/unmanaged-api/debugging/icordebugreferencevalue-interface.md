---
title: ICorDebugReferenceValue Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue
helpviewer_keywords:
- ICorDebugReferenceValue interface [.NET Framework debugging]
ms.assetid: 2040e2be-119a-4cfb-ae52-b0b6f052665c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b6cdfa9f3717e4025ff6f4fe6da3c1457cdebf7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422332"
---
# <a name="icordebugreferencevalue-interface1"></a>ICorDebugReferenceValue Interface1
オブジェクトへの参照である値を管理するメソッドを提供します。 (つまり、このインターフェイスはポインターを管理する方法を提供します。)このインターフェイスは、"ICorDebugValue"を実装します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Dereference メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|参照されているオブジェクトを取得します。|  
|[DereferenceStrong メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|実装されていません。 このメソッドを呼び出さないでください。|  
|[GetValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|参照先オブジェクトの現在のメモリ アドレスを取得します。|  
|[IsNull メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|示す値を取得するかどうかこの`ICorDebugReferenceValue`、null 値をその場合は、`ICorDebugReferenceValue`がオブジェクトを指していません。|  
|[SetValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|現在のメモリ アドレスを設定します。 つまり、このメソッドはこの設定`ICorDebugReferenceValue`にオブジェクトをポイントします。|  
  
## <a name="remarks"></a>コメント  
 共通言語ランタイム (CLR) は、デバッグ対象のプロセスが続行されたときに、オブジェクトのガベージ コレクションを行うことができます。 ガベージ コレクションは、メモリ内の周囲オブジェクトを移動可能性があります。 `ICorDebugReferenceValue`はいずれかの連携して、ガベージ コレクションを使用して、ガベージ コレクションの後の情報が更新されるか、ガベージ コレクションの前に暗黙的に無効化できるようにします。  
  
 `ICorDebugReferenceValue`デバッグ対象のプロセスが続行されてした後にオブジェクトが暗黙的に検証されたにする可能性があります。 明示的に解放されるか公開されるまでは、派生"ICorDebugHandleValue"は無効化されません。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
    
    
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
