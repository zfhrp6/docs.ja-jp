---
title: CorDebugUnmappedStop 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugUnmappedStop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUnmappedStop
helpviewer_keywords:
- CorDebugUnmappedStop enumeration [.NET Framework debugging]
ms.assetid: a684f7d7-d0c2-4690-b721-639e613f11f8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d812a452910913f169d4377bafa82e823c533d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404418"
---
# <a name="cordebugunmappedstop-enumeration"></a>CorDebugUnmappedStop 列挙型
ステッパによるコード実行の停止をトリガーする可能性のあるマップ解除したコードの型を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum CorDebugUnmappedStop {  
    STOP_NONE               = 0x0,  
    STOP_PROLOG             = 0x01,  
    STOP_EPILOG             = 0x02,  
    STOP_NO_MAPPING_INFO    = 0x04,  
    STOP_OTHER_UNMAPPED     = 0x08,  
    STOP_UNMANAGED          = 0x10,  
    STOP_ALL                = 0xffff,  
} CorDebugUnmappedStop;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`STOP_NONE`|マップされていないコードの種類では停止されません。|  
|`STOP_PROLOG`|プロローグ コードで停止します。|  
|`STOP_EPILOG`|エピローグ コードで停止します。|  
|`STOP_NO_MAPPING_INFO`|マッピング情報のないコードで停止します。|  
|`STOP_OTHER_UNMAPPED`|プロローグ、エピローグ、いいえ-マッピング情報、またはアンマネージ カテゴリに入らないマップされていないコードで停止します。|  
|`STOP_UNMANAGED`|アンマネージ コードで停止します。 この値は、相互運用機能デバッグでのみ有効です。|  
|`STOP_ALL`|すべての種類のマップされていないコードで停止します。|  
  
## <a name="remarks"></a>コメント  
 使用して、 [icordebugstepper::setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)ステッパは停止する、マップ解除したコードを指定するフラグを設定します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [列挙型のデバッグ](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
