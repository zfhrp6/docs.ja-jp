---
title: COR_GC_STATS 構造体
ms.date: 03/30/2017
api_name:
- COR_GC_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STATS
helpviewer_keywords:
- COR_GC_STATS structure [.NET Framework hosting]
ms.assetid: 8d4ff73e-739b-40f6-9349-359fbc99c2f9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 009f1482de6e1daea21766300b4fb6a3ab0ffc8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432289"
---
# <a name="corgcstats-structure"></a>COR_GC_STATS 構造体
共通言語ランタイム (CLR) のガベージ コレクションのメカニズムについての統計情報を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef struct _COR_GC_STATS {  
    ULONG   Flags;   
    SIZE_T  ExplicitGCCount;  
    SIZE_T  GenCollectionsTaken[3];  
    SIZE_T  CommittedKBytes;   
    SIZE_T  ReservedKBytes;  
    SIZE_T  Gen0HeapSizeKBytes;  
    SIZE_T  Gen1HeapSizeKBytes;  
    SIZE_T  Gen2HeapSizeKBytes;  
    SIZE_T  LargeObjectHeapSizeKBytes;  
    SIZE_T  KBytesPromotedFromGen0;  
    SIZE_T  KBytesPromotedFromGen1;  
} COR_GC_STATS;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`Flags`|フィールドの値を計算して、返される必要がありますを示します。|  
|`ExplicitGCCount`|外部の要求によって強制的に実行されたガベージ コレクションの数を示します。|  
|`GenCollectionsTaken`|実行の各ジェネレーションのガベージ コレクションの数を示します。|  
|`CommittedKBytes`|すべてのヒープでコミットされたキロバイト単位の合計数。|  
|`ReservedKBytes`|すべてのヒープ内で予約されたキロバイト単位の合計数。|  
|`Gen0HeapSizeKBytes`|ジェネレーション 0 ヒープのサイズ。|  
|`Gen1HeapSizeKBytes`|ジェネレーション 1 ヒープのサイズ。|  
|`Gen2HeapSizeKBytes`|ジェネレーション 2 のヒープのサイズ。|  
|`LargeObjectHeapSizeKBytes`|大きなオブジェクト ヒープのサイズ。|  
|`KBytesPromotedFromGen0`|ジェネレーション 0 からジェネレーション 1 に昇格オブジェクトのサイズ。|  
|`KBytesPromotedFromGen1`|ジェネレーション 1 からジェネレーション 2 に昇格オブジェクトのサイズ。|  
  
## <a name="remarks"></a>コメント  
 [Iclrgcmanager::getstats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)メソッドが必要な`Flags`のフィールド、`COR_GC_STATS`の 1 つまたは複数の値に設定する構造体、 [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)を指定する列挙体統計情報では、設定します。  
  
 次の表は、2 つに、この構造体で提供される統計[COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)列挙値、`COR_GC_COUNTS`と`COR_GC_MEMORYUSAGE`です。  
  
|COR_GC_COUNTS で指定されました。|COR_GC_MEMORYUSAGE で指定されました。|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 使用状況の例は次のとおりです。  
  
```  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** GCHost.idl  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ホスト構造体](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [自動メモリ管理](../../../../docs/standard/automatic-memory-management.md)  
 [ガベージ コレクション](../../../../docs/standard/garbage-collection/index.md)
