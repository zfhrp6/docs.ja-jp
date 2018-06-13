---
title: ICorDebugVariableHome::GetRegister メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetRegister
helpviewer_keywords:
- ICorDebugVariableHome::GetRegister method [.NET Framework debugging]
- GetRegister method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: a5eecd7b-b04c-4266-bff2-7c8771d519a8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e06c98067fea9368ac8f750d9187636d2ca9a8c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420109"
---
# <a name="icordebugvariablehomegetregister-method"></a>ICorDebugVariableHome::GetRegister メソッド
場所の種類を持つ変数を格納するレジスタを取得`VLT_REGISTER`、およびロケーションの型の変数のベース レジスタ`VLT_REGISTER_RELATIVE`です。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRegister`  
 [out]CorDebugRegister 列挙値の場所の種類を持つ変数のレジスタを示す`VLT_REGISTER`、およびロケーションの型の変数のベース レジスタ`VLT_REGISTER_RELATIVE`です。  
  
## <a name="return-value"></a>戻り値  
 メソッドは、次の値を返します。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|によって示されるレジスタには、変数、`pRegister`引数。|  
|`E_FAIL`|変数は、レジスタまたはレジスタの相対位置ではありません。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [VariableLocationType 列挙型](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 [ICorDebugVariableHome インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
