---
title: ICorDebugHeapValue::IsValid メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue.IsValid
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue::IsValid
helpviewer_keywords:
- IsValid method [.NET Framework debugging]
- ICorDebugHeapValue::IsValid method [.NET Framework debugging]
ms.assetid: 68e20e62-203d-46d8-bb91-8d3c61cfacc3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95532d6721467b482b1d79d611f8055b606bb4a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413509"
---
# <a name="icordebugheapvalueisvalid-method"></a>ICorDebugHeapValue::IsValid メソッド
この ICorDebugHeapValue によって表されるオブジェクトが有効かどうかを示す値を取得します。  
  
 .NET Framework version 2.0 では、このメソッドは廃止されました。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pbValid`  
 [out]ヒープでは、この値が有効かどうかを示すブール値へのポインター。  
  
## <a name="remarks"></a>コメント  
 値は、ガベージ コレクターが解放された場合に有効ではありません。  
  
 このメソッドの使用は非推奨とされました。 .NET Framework 2.0 ではすべての値は有効期限[icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)に時間値は、検証が呼び出されます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
