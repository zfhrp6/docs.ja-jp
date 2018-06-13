---
title: COR_PRF_GC_GENERATION 列挙型
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_GENERATION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_GENERATION
helpviewer_keywords:
- COR_GC_GENERATION_FLAGS enumeration [.NET Framework profiling]
ms.assetid: d6ece160-26ad-4d39-abd7-05acd6f78c48
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8283139566050b1858a003316dc46581822a9bbb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450155"
---
# <a name="corprfgcgeneration-enumeration"></a>COR_PRF_GC_GENERATION 列挙型
ガベージ コレクション ジェネレーションを識別します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3  
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|オブジェクトは、ジェネレーション 0 として格納されます。|  
|`COR_PRF_GC_GEN_1`|オブジェクトは、第 1 世代として格納されます。|  
|`COR_PRF_GC_GEN_2`|オブジェクトは、第 2 世代として格納されます。|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|オブジェクトは、大きなオブジェクト ヒープに格納されます。|  
  
## <a name="remarks"></a>コメント  
 ガベージ コレクターには、年齢に基づいてジェネレーションに分割オブジェクトによってメモリ管理のパフォーマンスが向上します。 現在、ガベージ コレクターは、0、1、2、およびラージ オブジェクトに使用される特殊なヒープ セグメントの番号、3 つの世代を使用します。 サイズが特定の値より大きいオブジェクトは、大きなオブジェクト ヒープに格納されます。 割り当てられたその他のオブジェクトは、ジェネレーション 0 に属しているを開始します。 ジェネレーション 0 のガベージ コレクションの発生後に存在するすべてのオブジェクトは、ジェネレーション 1 に昇格されます。 ジェネレーション 1 のガベージ コレクションが発生した後に存在するオブジェクトは、ジェネレーション 2 に移動します。  
  
 ジェネレーションの使用は、ガベージ コレクターは任意の時点で割り当てられたオブジェクトのサブセットのみを使用することを意味します。  
  
 `COR_PRF_GC_GENERATION`列挙型を使用して、 [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md)構造体。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [列挙型のプロファイリング](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
