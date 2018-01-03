---
title: "ICorDebugEval::CreateValue メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.CreateValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::CreateValue
helpviewer_keywords:
- ICorDebugEval::CreateValue method [.NET Framework debugging]
- CreateValue method [.NET Framework debugging]
ms.assetid: 9a1c0b47-6f10-4fcb-844a-4ab2d7990140
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 64d55a951795cc5efc1bfc624dbe07575be153aa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugevalcreatevalue-method"></a>ICorDebugEval::CreateValue メソッド
0 または null の初期値を指定した型の値を作成します。  
  
 このメソッドは、.NET Framework version 2.0 廃止されています。 使用して[icordebugeval 2::createvaluefortype](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)代わりにします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateValue (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `elementType`  
 [in]値、 [CorElementType](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md)列挙値の型を指定します。  
  
 `pElementClass`  
 [in]ポインター、 [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)型がプリミティブ型ではない場合、値のクラスを指定するオブジェクト。  
  
 `ppValue`  
 [out]値を表す"ICorDebugValue"オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>コメント  
 `CreateValue`作成、`ICorDebugValue`関数の評価に使用する際の目的で指定された型のオブジェクト。 パラメーターとしてユーザー定数を渡すには、この値のオブジェクトを使用できます。  
  
 値の型がプリミティブ型の場合は、その初期値は、0 または null。 使用して[icordebuggenericvalue::setvalue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)プリミティブ型の値を設定します。  
  
 場合の値`elementType`ELEMENT_TYPE_CLASS は、"ICorDebugReferenceValue"を取得する (で返される`ppValue`) null オブジェクト参照を表すです。 このオブジェクトを使用して、オブジェクト参照のパラメーターを持つ関数の評価に null を渡すことができます。 設定することはできません、`ICorDebugValue`ものがデータ ソースに、常に null です。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** 1.1、1.0  
  
## <a name="see-also"></a>参照  
    
 [CreateValueForType メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)  
 ICorDebugValue
