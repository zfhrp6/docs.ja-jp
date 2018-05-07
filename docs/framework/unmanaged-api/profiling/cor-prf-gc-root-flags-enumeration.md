---
title: COR_PRF_GC_ROOT_FLAGS 列挙型
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_ROOT_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_FLAGS
helpviewer_keywords:
- COR_PRF_GC_ROOT_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 4611ee6f-0f05-4d84-91e1-e83d5e7dd7e4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2d5dcb089074b52fc87a0bb83c7e062e7ef07b46
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="corprfgcrootflags-enumeration"></a>COR_PRF_GC_ROOT_FLAGS 列挙型
ガーベッジ コレクション ルートのプロパティを示します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum {  
    COR_PRF_GC_ROOT_PINNING = 0x1,  
    COR_PRF_GC_ROOT_WEAKREF = 0x2,  
    COR_PRF_GC_ROOT_INTERIOR = 0x4,  
    COR_PRF_GC_ROOT_REFCOUNTED = 0x8,  
} COR_PRF_GC_ROOT_FLAGS;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_PINNING`|ルートでは、ガベージ コレクション オブジェクトを移動できないようにします。|  
|`COR_PRF_GC_ROOT_WEAKREF`|ルートは、ガベージ コレクションを阻止されません。|  
|`COR_PRF_GC_ROOT_INTERIOR`|ルートは、オブジェクト自体ではなく、オブジェクトのフィールドを参照します。|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|ルートは、オブジェクトの参照カウントが特定の値である場合に、ガベージ コレクションを回避します。|  
  
## <a name="remarks"></a>コメント  
 `COR_PRF_GC_ROOT_FLAGS` 特殊なルートに関する追加情報を提供できるビットマスクであります。 ただし、すべてのルートは特殊です。 たとえば、一部のルートは、弱い参照を内部ポインター、ピン留めされた、または参照カウントではありません。 このようなルートを伝えるためにフラグがありません。 したがってなど、この列挙を使用するメソッド、 [icorprofilercallback 2::rootreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)メソッド、送信 0 すべてフラグを設定するかを示す、フラグ ビットがオフになっています。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [列挙型のプロファイリング](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
