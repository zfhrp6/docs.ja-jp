---
title: COR_SEGMENT 構造体
ms.date: 03/30/2017
api_name:
- COR_SEGMENT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_SEGMENT
helpviewer_keywords:
- COR_SEGMENT structure [.NET Framework debugging]
ms.assetid: 93aeecb9-7fef-4545-8daf-f566dfc47084
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b816087f54e652f07dc791b7d66eb1af8f52f55e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406508"
---
# <a name="corsegment-structure"></a>COR_SEGMENT 構造体
マネージ ヒープのメモリ領域に関する情報が含まれます。  
  
## <a name="syntax"></a>構文  
  
```  
typedef struct _COR_SEGMENT {  
    CORDB_ADDRESS start;            
    CORDB_ADDRESS end;              
    CorDebugGenerationTypes gen;    
    ULONG heap;                     
} COR_SEGMENT;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`start`|メモリ領域の開始アドレス。|  
|`end`|メモリ領域の終了アドレス。|  
|`gen`|A [CorDebugGenerationTypes](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md)メモリ領域の生成を示す列挙メンバー。|  
|`heap`|メモリ領域が存在するヒープ数です。 詳細については、次の「解説」を参照してください。|  
  
## <a name="remarks"></a>コメント  
 `COR_SEGMENTS`構造体がマネージ ヒープのメモリ領域を表します。  `COR_SEGMENTS` オブジェクトのメンバーである、 [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)が呼び出すことによって設定されているコレクション オブジェクト、[icordebugprocess 5::enumerateheapregions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)メソッドです。  
  
 `heap`フィールドは、プロセッサ番号、報告されているヒープに対応しています。 ワークステーション ガベージ コレクターでは、その値は常に 0、ワークステーション ガベージ コレクション ヒープの 1 つだけがあるためです。 サーバー ガベージ コレクターでは、その値は、ヒープに接続されているプロセッサに対応します。 ありますまたはより少ないガベージ コレクション ヒープがよりも多いため、ガベージ コレクターの実装の詳細の実際のプロセッサに注意してください。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグ構造体](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
