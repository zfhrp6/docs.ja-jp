---
title: CorImportOptions 列挙型
ms.date: 03/30/2017
api_name:
- CorImportOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorImportOptions
helpviewer_keywords:
- CorImportOptions enumeration [.NET Framework metadata]
ms.assetid: 4e5d03cb-97c9-4ff4-8dbd-17d94ee374d3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7078b2eb98c15b7229132076da8af4691032bb08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441793"
---
# <a name="corimportoptions-enumeration"></a>CorImportOptions 列挙型
現在のスコープ外のアセンブリのインポート中の動作を制御するフラグ値が格納されます。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum CorImportOptions {  
  
    MDImportOptionDefault                = 0x00000000,  
    MDImportOptionAll                    = 0xFFFFFFFF,  
    MDImportOptionAllTypeDefs            = 0x00000001,  
    MDImportOptionAllMethodDefs          = 0x00000002,  
    MDImportOptionAllFieldDefs           = 0x00000004,  
    MDImportOptionAllProperties          = 0x00000008,  
    MDImportOptionAllEvents              = 0x00000010,  
    MDImportOptionAllCustomAttributes    = 0x00000020,  
    MDImportOptionAllExportedTypes       = 0x00000040  
  
} CorImportOptions;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`MDImportOptionDefault`|削除されたレコードをスキップするには既定の動作を示します。|  
|`MDImportOptionAll`|すべてのメタデータを列挙することを示します。|  
|`MDImportOptionAllTypeDefs`|削除されたものも含めて、すべての Typedef が列挙されることを示します。|  
|`MDImportOptionAllMethodDefs`|削除されたものも含めて、すべての MethodDefs が列挙されることを示します。|  
|`MDImportOptionAllFieldDefs`|削除されたものも含めて、すべての FieldDefs が列挙されることを示します。|  
|`MDImportOptionAllProperties`|削除されたものも含めて、すべての PropertyDefs が列挙されることを示します。|  
|`MDImportOptionAllEvents`|削除されたものも含めて、すべての EventDefs が列挙されることを示します。|  
|`MDImportOptionAllCustomAttributes`|削除されたものも含めて、すべてのカスタム属性を列挙することを示します。|  
|`MDImportOptionAllExportedTypes`|削除されたものも含めて、すべてのエクスポートされた型が列挙されることを示します。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorHdr.h  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
