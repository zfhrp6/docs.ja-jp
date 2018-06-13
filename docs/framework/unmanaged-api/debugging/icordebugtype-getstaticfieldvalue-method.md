---
title: ICorDebugType::GetStaticFieldValue メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 62eb5d55-53ee-4fb3-8d47-7b6c96808f9e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b136f30b0c1ce9f83228f340ac5e147cc02002b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422030"
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a>ICorDebugType::GetStaticFieldValue メソッド
指定したスタック フレームでトークンを指定したフィールドによって参照される静的フィールドの値を格納している ICorDebugValue オブジェクト インターフェイス ポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `fieldDef`  
 [in]`mdFieldDef`静的フィールドを指定するトークン。  
  
 `pFrame`  
 [in]スタック フレームを表す ICorDebugFrame へのポインター。  
  
 `ppValue`  
 [out]アドレスへのポインター、`ICorDebugValue`静的フィールドの値を格納します。  
  
## <a name="remarks"></a>コメント  
 `GetStaticFieldValue`メソッドとして使用できる型が ELEMENT_TYPE_CLASS または ELEMENT_TYPE_VALUETYPE 場合に、のみによって示される、 [icordebugtype::gettype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)メソッドです。  
  
 非ジェネリック型の場合、操作を実行して`GetStaticFieldValue`を呼び出すことと同じ[icordebugclass::getstaticfieldvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md) ICorDebugClass オブジェクトによって返される[icordebugtype::getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md).  
  
 ジェネリック型の静的フィールドの値を特定のインスタンス化の基準としたされます。 また、静的フィールドは、スレッド、コンテキスト、またはアプリケーション ドメインを基準とした可能性ありますでした、スタック フレームは適切な値を決定するデバッガーを提供します。  
  
## <a name="remarks"></a>コメント  
 `GetStaticFieldValue` 呼び出すときにのみ使用できます`ICorDebugType::GetType`ELEMENT_TYPE_CLASS または ELEMENT_TYPE_VALUETYPE の値を返します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
