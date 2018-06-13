---
title: ICorDebugModule::GetName メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetName
helpviewer_keywords:
- ICorDebugModule::GetName method [.NET Framework debugging]
- GetName method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: db499637-7ba9-421e-b8b1-35856995e80b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bebee019595143d25e950719ad62d9e10b76a3e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418907"
---
# <a name="icordebugmodulegetname-method"></a>ICorDebugModule::GetName メソッド
モジュールのファイル名を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `cchname`  
 [in] `szName` 配列のサイズ。  
  
 `pcchName`  
 [in]返される名前の長さへのポインター。  
  
 `szName`  
 [out]返される名前を格納する配列。  
  
## <a name="remarks"></a>コメント  
 `GetName`メソッドは、モジュールのファイル名には、ディスク上の名前が一致する場合は S_OK HRESULT を返します。 `GetName` 場合は、名前は、用意された、動的またはメモリ内のモジュールの場合のように、S_FALSE HRESULT を返します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
    
 
