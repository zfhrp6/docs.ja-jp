---
title: "ICorDebugValue::GetSize メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValue.GetSize
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValue::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugValue interface [.NET Framework debugging]
- ICorDebugValue::GetSize method [.NET Framework debugging]
ms.assetid: 445a9ee3-e050-4f3a-931a-96b0efb00110
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5cf99b35d45c1dda8f187e0206e068c128f347d1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvaluegetsize-method"></a>ICorDebugValue::GetSize メソッド
この"ICorDebugValue"オブジェクトのバイト単位のサイズを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pSize`  
 [out]この値のオブジェクトのバイト単位のサイズ。  
  
## <a name="remarks"></a>コメント  
 値の型が参照型の場合は、このメソッドは、オブジェクトのサイズではなく、ポインターのサイズを返します。  
  
 `ICorDebugValue::GetSize`メソッドを返します。`COR_E_OVERFLOW`は 64 ビット プラットフォームで 4 GB より大きいオブジェクト。 使用して、 [icordebugvalue 3::getsize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)メソッド代わりにオブジェクトにある 4 GB より大きい。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
    
 [GetSize64 メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)
