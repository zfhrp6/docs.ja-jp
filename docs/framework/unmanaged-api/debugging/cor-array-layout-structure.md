---
title: COR_ARRAY_LAYOUT 構造体
ms.date: 03/30/2017
api_name:
- COR_ARRAY_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ARRAY_LAYOUT
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: aa20ac3d-6f60-4aa2-91c5-f3a86f82eba8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a96542ab5113311bba79cc552afd7f29e6eafa2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406397"
---
# <a name="corarraylayout-structure"></a>COR_ARRAY_LAYOUT 構造体
メモリ内の配列オブジェクトのレイアウトに関する情報が提供されます。  
  
## <a name="syntax"></a>構文  
  
```  
typedef struct COR_ARRAY_LAYOUT {  
    COR_TYPEID componentID;  
    CorElementType componentType;  
    ULONG32 firstElementOffset;  
    ULONG32 elementSize;  
    ULONG32 countOffset;   
    ULONG32 rankSize;   
    ULONG32 numRanks;   
    ULONG32 rankOffset;   
} COR_ARRAY_LAYOUT;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`componentID`|配列が含まれているオブジェクトの種類の識別子。|  
|`componentType`|コンポーネントがガベージ コレクションの参照、値クラス、またはプリミティブであるかどうかを示す CorElementType 列挙型値。|  
|`firstElementOffset`|配列の最初の要素のオフセット。|  
|`elementSize`|各要素のサイズ。|  
|`countOffset`|配列内の要素の数をオフセットします。|  
|`rankSize`|(バイト単位)、ランクのサイズ。|  
|`numRanks`|配列のランクの数。|  
|`rankOffset`|ランクを開始するオフセットです。|  
  
## <a name="remarks"></a>コメント  
 `rankSize`フィールドは、多次元配列のランクのサイズを指定します。 これは、1 次元の配列も正確です。  
  
 値`numRanks`は 1 次元配列の場合は 1 と`N`の多次元配列を`N`ディメンションです。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグ構造体](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
