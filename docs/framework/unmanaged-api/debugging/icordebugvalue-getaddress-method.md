---
title: ICorDebugValue::GetAddress メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetAddress
helpviewer_keywords:
- ICorDebugValue::GetAddress method [.NET Framework debugging]
- GetAddress method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: a247c792-45e1-4538-9e1f-b46acca4a463
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c0fa19841580c7cfe8902577c3f756712a35893
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420660"
---
# <a name="icordebugvaluegetaddress-method"></a>ICorDebugValue::GetAddress メソッド
デバッグ対象プロセスでは、この"ICorDebugValue"オブジェクトのアドレスを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pAddress`  
 [out]ポインター、`CORDB_ADDRESS`この値のオブジェクトのアドレスを指定するオブジェクト。  
  
## <a name="remarks"></a>コメント  
 値が使用できない場合は 0 (ゼロ) が返されます。 これは、値は、少なくとも一部レジスタ場合に発生する可能性がありますか、ガベージ コレクター ハンドルに格納されている (`GCHandle`)。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 
