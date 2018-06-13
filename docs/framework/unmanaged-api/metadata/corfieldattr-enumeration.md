---
title: CorFieldAttr 列挙型
ms.date: 03/30/2017
api_name:
- CorFieldAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFieldAttr
helpviewer_keywords:
- CorFieldAttr enumeration [.NET Framework metadata]
ms.assetid: 6ae2c4be-212c-4e74-9288-40a11dc26522
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a57318103fd875d6f2f2fe4ca54c776da86c0e53
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446621"
---
# <a name="corfieldattr-enumeration"></a>CorFieldAttr 列挙型
フィールドについてのメタデータを記述する値が格納されます。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum CorFieldAttr {  
  
    fdFieldAccessMask           =   0x0007,  
    fdPrivateScope              =   0x0000,  
    fdPrivate                   =   0x0001,  
    fdFamANDAssem               =   0x0002,  
    fdAssembly                  =   0x0003,  
    fdFamily                    =   0x0004,  
    fdFamORAssem                =   0x0005,  
    fdPublic                    =   0x0006,  
  
    fdStatic                    =   0x0010,  
    fdInitOnly                  =   0x0020,  
    fdLiteral                   =   0x0040,  
    fdNotSerialized             =   0x0080,  
  
    fdSpecialName               =   0x0200,  
  
    fdPinvokeImpl               =   0x2000,  
  
    fdReservedMask              =   0x9500,  
    fdRTSpecialName             =   0x0400,  
    fdHasFieldMarshal           =   0x1000,  
    fdHasDefault                =   0x8000,  
    fdHasFieldRVA               =   0x0100  
  
} CorFieldAttr;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`fdFieldAccessMask`|ユーザー補助に関する情報を指定します。|  
|`fdPrivateScope`|フィールドを参照できないことを指定します。|  
|`fdPrivate`|フィールドが親の型からのみアクセスできることを指定します。|  
|`fdFamANDAssem`|フィールドにそれが属するアセンブリ内の派生クラスでアクセスできることを指定します。|  
|`fdAssembly`|フィールドにそれが属するアセンブリ内のすべての型によってアクセスできることを指定します。|  
|`fdFamily`|フィールドがその型によってのみアクセスできますが、派生クラスを指定します。|  
|`fdFamORAssem`|フィールドがそのアセンブリ内のすべての型と派生クラスによってアクセスできることを指定します。|  
|`fdPublic`|フィールドにこのスコープの可視性を持つすべての型からアクセスできることを指定します。|  
|`fdStatic`|フィールドがインスタンス メンバーではなく、その型のメンバーであることを指定します。|  
|`fdInitOnly`|初期化された後に、フィールドを変更できないことを指定します。|  
|`fdLiteral`|フィールドの値が、コンパイル時定数であることを指定します。|  
|`fdNotSerialized`|その型は、リモート処理は実行時に、フィールドはシリアル化されませんを指定します。|  
|`fdSpecialName`|フィールドが、特別なことと、その名前が記述されているを指定する方法です。|  
|`fdPinvokeImpl`|PInvoke によってフィールドの実装が転送されることを指定します。|  
|`fdReservedMask`|共通言語ランタイムでは、内部使用に予約されています。|  
|`fdRTSpecialName`|共通言語ランタイム メタデータの内部 Api が名のエンコードを確認する必要がありますを指定します。|  
|`fdHasFieldMarshal`|フィールドにマーシャ リング情報が含まれることを指定します。|  
|`fdHasDefault`|フィールドが既定値を持つことを指定します。|  
|`fdHasFieldRVA`|フィールドの相対仮想アドレスを持つことを指定します。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorHdr.h  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
