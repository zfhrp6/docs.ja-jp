---
title: CorMethodAttr 列挙型
ms.date: 03/30/2017
api_name:
- CorMethodAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodAttr
helpviewer_keywords:
- CorMethodAttr enumeration [.NET Framework metadata]
ms.assetid: 4e0c3521-e54d-43c1-9857-cc76b49b8ffc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f144426996583d5058f70daed99d8a37cfb6bfb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="cormethodattr-enumeration"></a>CorMethodAttr 列挙型
メソッドの機能を記述する値が含まれています。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum CorMethodAttr {  
  
    mdMemberAccessMask          =   0x0007,  
    mdPrivateScope              =   0x0000,  
    mdPrivate                   =   0x0001,  
    mdFamANDAssem               =   0x0002,  
    mdAssem                     =   0x0003,  
    mdFamily                    =   0x0004,  
    mdFamORAssem                =   0x0005,  
    mdPublic                    =   0x0006,  
  
    mdStatic                    =   0x0010,  
    mdFinal                     =   0x0020,  
    mdVirtual                   =   0x0040,  
    mdHideBySig                 =   0x0080,  
  
    mdVtableLayoutMask          =   0x0100,  
    mdReuseSlot                 =   0x0000,  
    mdNewSlot                   =   0x0100,  
  
    mdCheckAccessOnOverride     =   0x0200,  
    mdAbstract                  =   0x0400,  
    mdSpecialName               =   0x0800,  
  
    mdPinvokeImpl               =   0x2000,  
    mdUnmanagedExport           =   0x0008,  
  
    mdReservedMask              =   0xd000,  
    mdRTSpecialName             =   0x1000,  
    mdHasSecurity               =   0x4000,  
    mdRequireSecObject          =   0x8000,  
  
} CorMethodAttr;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`mdMemberAccessMask`|メンバーへのアクセスを指定します。|  
|`mdPrivateScope`|メンバーを参照できないことを指定します。|  
|`mdPrivate`|メンバーが、親の型によってのみアクセスできることを指定します。|  
|`mdFamANDAssem`|メンバーにのみこのアセンブリのサブタイプでアクセスできることを指定します。|  
|`mdAssem`|アセンブリ内の誰でもアクセスできます。 のメンバーを指定します。|  
|`mdFamily`|メンバーに型とサブタイプによってのみアクセスできることを指定します。|  
|`mdFamORAssem`|メンバーがそのアセンブリ内の他の型と派生クラスによってアクセスできることを指定します。|  
|`mdPublic`|メンバーがスコープにアクセス権を持つすべての型にアクセスできることを指定します。|  
|`mdStatic`|インスタンスのメンバーではなく、型の一部として、メンバーが定義されていることを指定します。|  
|`mdFinal`|メソッドをオーバーライドできないことを指定します。|  
|`mdVirtual`|メソッドをオーバーライドできることを指定します。|  
|`mdHideBySig`|メソッドには、名前だけではなく、名前とシグネチャで非表示にするかを指定します。|  
|`mdVtableLayoutMask`|仮想テーブル レイアウトを指定します。|  
|`mdReuseSlot`|仮想テーブルでは、このメソッドの使用、スロットが再利用することを指定します。 既定値です。|  
|`mdNewSlot`|メソッドは、仮想テーブルの新しいスロットを常に取得を指定します。|  
|`mdCheckAccessOnOverride`|表示は同じ型でメソッドをオーバーライドできることを指定します。|  
|`mdAbstract`|メソッドが実装されないように指定します。|  
|`mdSpecialName`|メソッドが、特別なであると、その名前が記述されているを指定する方法です。|  
|`mdPinvokeImpl`|PInvoke を使用して、メソッドの実装が転送されることを指定します。|  
|`mdUnmanagedExport`|メソッドがアンマネージ コードにエクスポートするマネージ メソッドを指定します。|  
|`mdReservedMask`|共通言語ランタイムでは、内部使用に予約されています。|  
|`mdRTSpecialName`|共通言語ランタイムがメソッド名のエンコードを確認する必要がありますを指定します。|  
|`mdHasSecurity`|メソッドに関連付けられているセキュリティを指定します。|  
|`mdRequireSecObject`|メソッドがセキュリティ コードを含む他のメソッドを呼び出すことを指定します。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorHdr.h  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
