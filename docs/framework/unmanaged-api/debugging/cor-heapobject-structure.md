---
title: "COR_HEAPOBJECT 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_HEAPOBJECT
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_HEAPOBJECT
helpviewer_keywords: COR_HEAPOBJECT structure [.NET Framework debugging]
ms.assetid: a92fdf95-492b-49ae-a741-2186e5c1d7c5
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bcd971853707349bf0d60459cb46b0fea1e8a97b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="corheapobject-structure"></a>COR_HEAPOBJECT 構造体
マネージ ヒープ上のオブジェクトに関する情報が提供されます。  
  
## <a name="syntax"></a>構文  
  
```  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;    
    ULONG64 size;             
    COR_TYPEID type;          
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`address`|メモリ内のオブジェクトのアドレス。|  
|`size`|(バイト単位)、オブジェクトの合計サイズ。|  
|`type`|A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)オブジェクトの型を表すトークンです。|  
  
## <a name="remarks"></a>コメント  
 `COR_HEAPOBJECT`インスタンスを列挙することによって取得できる、 [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)インターフェイス オブジェクトの呼び出しによって設定される、 [icordebugprocess 5::enumerateheap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)メソッドです。  
  
 A`COR_HEAPOBJECT`インスタンスは、いずれか、マネージ ヒープ上のライブ オブジェクトまたはオブジェクトでルートが指定されていませんが、ガベージ コレクターによって収集されていないオブジェクトに関する情報を提供します。  
  
 パフォーマンス向上のため、`COR_HEAPOBJECT.address`フィールドは、 `CORDB_ADDRESS` ICorDebugValue ではなく、値のインターフェイス デバッグ API の多くで使用される値。 指定したオブジェクトのアドレスの ICorDebugValue オブジェクトを取得するを渡すことができます、`CORDB_ADDRESS`値を[icordebugprocess 5::getobject](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)メソッドです。  
  
 パフォーマンス向上のため、`COR_HEAPOBJECT.type`フィールドは、 `COR_TYPEID` ICorDebugType ではなく、値のインターフェイス デバッグ API の多くで使用される値。 指定された型の ID で ICorDebugType オブジェクトを取得することができますを渡します、`COR_TYPEID`値を[icordebugprocess 5::gettypefortypeid](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)メソッドです。  
  
 `COR_HEAPOBJECT`構造体には、参照カウントの COM インターフェイスが含まれています。 取得する場合、`COR_HEAPOBJECT`を呼び出して列挙子からのインスタンス、 [icordebugheapenum::next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)メソッドを後で参照を解放する必要があります。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグ構造体](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
