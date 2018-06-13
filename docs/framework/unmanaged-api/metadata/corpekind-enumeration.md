---
title: CorPEKind 列挙型
ms.date: 03/30/2017
api_name:
- CorPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPEKind
helpviewer_keywords:
- CorPEKind enumeration [.NET Framework metadata]
ms.assetid: 22dc6dea-b1b9-4982-a730-a022d586b117
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b5869eb16bd768d58a6f27a83f2d8d51914a8aed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443116"
---
# <a name="corpekind-enumeration"></a>CorPEKind 列挙型
呼び出しから返されるよう、ポータブル実行可能 (PE) ファイルを記述する値を含む[imetadataimport 2::getpekind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum CorPEKind {  
  
    peNot           = 0x00000000,  
    peILonly        = 0x00000001,  
    pe32BitRequired = 0x00000002,  
    pe32Plus        = 0x00000004,  
    pe32Unmanaged   = 0x00000008,  
    pe32BitPreferred= 0x00000010  
  
} CorPEKind;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`peNot`|PE ファイルではないことを示します。|  
|`peILOnly`|この PE ファイルには、マネージ コードだけが含まれていることを示します。|  
|`pe32BitRequired`|この PE ファイルが Win32 呼び出しを行うことを示します。|  
|`pe32Plus`|この PE ファイルが 64 ビット プラットフォームで実行されることを示します。|  
|`pe32Unmanaged`|この PE ファイルがネイティブ コードであることを示します。|  
|pe32BitPreferred|この PE ファイルがプラットフォームに依存しない、優先的に 32 ビット環境で読み込まれることを示します。|  
  
## <a name="remarks"></a>コメント  
 これらの値は、ビットごとの組み合わせで使用できます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorHdr.h  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
