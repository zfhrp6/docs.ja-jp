---
title: CorSymAddrKind 列挙体
ms.date: 03/30/2017
api_name:
- CorSymAddrKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymAddrKind
helpviewer_keywords:
- CorSymAddrKind enumeration [.NET Framework debugging]
ms.assetid: 3ef841c2-cade-42ee-ba34-2ef91d6d0879
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98cf49714829b4b2f80e0240c2ebde7fa6c280e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425406"
---
# <a name="corsymaddrkind-enumeration"></a>CorSymAddrKind 列挙体
メモリ アドレスの種類を示します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum CorSymAddrKind  
{  
    ADDR_IL_OFFSET          = 1,  
    ADDR_NATIVE_RVA         = 2,  
    ADDR_NATIVE_REGISTER    = 3,  
    ADDR_NATIVE_REGREL      = 4,  
    ADDR_NATIVE_OFFSET      = 5,  
    ADDR_NATIVE_REGREG      = 6,  
    ADDR_NATIVE_REGSTK      = 7,  
    ADDR_NATIVE_STKREG      = 8,  
    ADDR_BITFIELD           = 9,  
    ADDR_NATIVE_ISECTOFFSET = 10  
} CorSymAddrKind;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`ADDR_IL_OFFSET`|Microsoft intermediate language (MSIL) ローカル変数またはパラメーター インデックスを示します。|  
|`ADDR_NATIVE_RVA`|モジュールへの相対仮想アドレスを示します。|  
|`ADDR_NATIVE_REGISTER`|CPU レジスタを示します。|  
|`ADDR_NATIVE_REGREL`|最初のアドレスは、レジスタと 2 番目のアドレスは、オフセットを示します。|  
|`ADDR_NATIVE_OFFSET`|ベース アドレスからのオフセットを示します。|  
|`ADDR_NATIVE_REGREG`|最初のアドレスは、レジスタの低部、2 つ目は高い部分を示します。|  
|`ADDR_NATIVE_REGSTK`|ことを示します最初のアドレスは、レジスタの不足部分であり、2 つ目は、高の部分では、3 番目のオフセット。|  
|`ADDR_NATIVE_STKREG`|最初のアドレスは、レジスタ、2 番目のオフセット、そのが、3 番目のレジスタの高い部分を示します。|  
|`ADDR_BITFIELD`|最初のアドレスは、フィールドの開始、2 番目のアドレスは、フィールド長を示します。|  
|`ADDR_NATIVE_ISECTOFFSET`|最初のアドレスは、セクションと 2 番目のアドレスは、オフセットを示します。|  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** CorSym.idl、CorSym.h  
  
## <a name="see-also"></a>関連項目  
 [シンボル ストア診断列挙型](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
