---
title: "ICorDebugHeapEnum::Next メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapEnum::Next
helpviewer_keywords:
- ICorDebugHeapEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 2221fd06-9e27-4113-972e-2530db8c3594
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e9869542b04b26fdf343b4112c2f84a26a3061c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapenumnext-method"></a>ICorDebugHeapEnum::Next メソッド
指定した数を取得[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)マネージ ヒープ オブジェクトに関する情報を格納するインスタンス。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],   
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 celt  
 [in] 取得するオブジェクトの数。  
  
 オブジェクト  
 [out]それぞれが指すポインターの配列、 [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)マネージ ヒープのオブジェクトに関する情報を提供するオブジェクト。  
  
 pceltFetched  
 [out]数へのポインター [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)で実際に返されたオブジェクト`objects`です。 `celt` が 1 の場合、この値は`null` になることがあります。  
  
## <a name="remarks"></a>コメント  
 `COR_HEAPOBJECT.type` フィールドは、入れ子になった参照カウントの COM インターフェイスの識別子です。 この参照は、`ICorDebugHeapEnum::Next` の呼び出し元によって解放される必要があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICorDebugHeapEnum インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
