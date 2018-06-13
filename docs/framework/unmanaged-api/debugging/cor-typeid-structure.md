---
title: COR_TYPEID 構造体
ms.date: 03/30/2017
api_name:
- COR_TYPEID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPEID
helpviewer_keywords:
- COR_TYPEID structure [.NET Framework debugging]
ms.assetid: 1e172b14-ee22-4943-b3b8-3740e7bdcd2e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d4e07fb3d0988838fde662f4bb7d4719cc2d50f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408341"
---
# <a name="cortypeid-structure"></a>COR_TYPEID 構造体
型識別子が含まれます。  
  
## <a name="syntax"></a>構文  
  
```  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`token1`|最初のトークンです。|  
|`token2`|2 番目のトークンです。|  
  
## <a name="remarks"></a>コメント  
 `COR_TYPEID`構造体は、多数のオブジェクトをガベージ コレクションに関する情報を提供するデバッグ メソッドによって返されます。 これは、そのアイテムに関する追加情報を提供するその他のデバッグ方法の引数として渡すことができます。 列挙することによってなど、 [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)オブジェクト、個々 が取得することができます[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)マネージ ヒープ上の個々 のオブジェクトを表すオブジェクト。 パススルーすることができます、`COR_TYPEID`値から、`COR_HEAPOBJECT.type`フィールドを[icordebugprocess 5::gettypefortypeid](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)オブジェクトに関する型情報を提供する ICorDebugType オブジェクトを取得します。  
  
 A`COR_TYPEID`オブジェクトは不透明にするためのものです。 その個々 のフィールドをアクセスまたは操作する必要があります。 として指定されている識別子としてのみ使用することは、`out`さらに、メソッドの呼び出しとそのには、パラメーターが追加情報を提供するその他のメソッドに渡されます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグ構造体](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
