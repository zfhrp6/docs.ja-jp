---
title: "ICorDebugComObjectValue::GetCachedInterfacePointers メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugComObjectValue::GetCachedInterfacePointers
api_location: mscordbi.dll
f1_keywords: ICorDebugComObjectValue::GetCachedInterfacePointers
helpviewer_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers method [.NET Framework debugging]
- GetCachedInterfacePointers method, ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 08dbd558-bd39-4263-94c2-71e70687aaf0
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2b47395235ce21c7d40e4413702e6c655493a739
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a>ICorDebugComObjectValue::GetCachedInterfacePointers メソッド
現在のランタイム呼び出し可能ラッパー (RCW) 上にキャッシュされた生のインターフェイス ポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `bIInspectableOnly`  
 [in]メソッドはのみ返すかどうかを示す値[!INCLUDE[wrt](../../../../includes/wrt-md.md)]インターフェイス (`IInspectable`インターフェイス) またはランタイム呼び出し可能ラッパー (RCW) によってキャッシュされているすべての COM インターフェイスです。  
  
 `celt`  
 [in]アドレスを持つを取得するオブジェクトの数。  
  
 `pceltFetched`  
 [out]数へのポインター`CORDB_ADDRESS`で実際に返される値`ptrs`です。  
  
 `ptrs`  
 配列の開始アドレスへのポインター`CORDB_ADDRESS`のアドレスを格納した値は、インターフェイス オブジェクトをキャッシュします。  
  
## <a name="remarks"></a>コメント  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICorDebugComObjectValue のインターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
