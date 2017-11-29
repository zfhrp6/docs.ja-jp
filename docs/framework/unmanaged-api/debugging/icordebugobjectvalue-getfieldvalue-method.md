---
title: "ICorDebugObjectValue::GetFieldValue メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugObjectValue.GetFieldValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugObjectValue::GetFieldValue
helpviewer_keywords:
- ICorDebugObjectValue::GetFieldValue method [.NET Framework debugging]
- GetFieldValue method [.NET Framework debugging]
ms.assetid: c96770b0-3e09-47bb-bd29-20353b043459
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 33c3f368d9b78b899f54c989427ea1f660346487
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a>ICorDebugObjectValue::GetFieldValue メソッド
このオブジェクトの値の指定したクラスの指定したフィールドの値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pClass`  
 [in]フィールドの値を取得する対象のクラスを表す"ICorDebugClass"オブジェクトへのポインター。  
  
 `fieldDef`  
 [in]`mdFieldDef`フィールドを記述するメタデータを参照するトークン。  
  
 `ppValue`  
 [out]指定したフィールドの値を表す"ICorDebugValue"オブジェクトへのポインター。  
  
## <a name="remarks"></a>コメント  
 指定された、クラス、`pClass`パラメーター、オブジェクトの値のクラスの階層では、あるフィールドは、そのクラスのフィールドをする必要があります。  
  
 `GetFieldValue`汎用オブジェクトおよびジェネリック クラスのメソッドは成功します。 たとえば場合、MyDictionary\<V > ディクショナリから継承\<文字列、V > とオブジェクトの値型 MyDictionary\<int32 > を渡して、`ICorDebugClass`ディクショナリのオブジェクト\<K, V > はディクショナリのフィールドを正常に取得\<文字列、int32 > です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
    
 
