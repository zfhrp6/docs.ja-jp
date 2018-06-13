---
title: CorTypeAttr 列挙型
ms.date: 03/30/2017
api_name:
- CorTypeAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTypeAttr
helpviewer_keywords:
- CorTypeAttr enumeration [.NET Framework metadata]
ms.assetid: 9bede0ec-5fdf-42a2-b5b7-bee64056acb6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0f71e59eb13321517de61315d3ba06b96c5458f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449274"
---
# <a name="cortypeattr-enumeration"></a>CorTypeAttr 列挙型
メタデータ型を示す値が格納されます。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum CorTypeAttr {  
  
    tdVisibilityMask        =   0x00000007,  
    tdNotPublic             =   0x00000000,  
    tdPublic                =   0x00000001,  
    tdNestedPublic          =   0x00000002,  
    tdNestedPrivate         =   0x00000003,  
    tdNestedFamily          =   0x00000004,  
    tdNestedAssembly        =   0x00000005,  
    tdNestedFamANDAssem     =   0x00000006,  
    tdNestedFamORAssem      =   0x00000007,  
  
    tdLayoutMask            =   0x00000018,  
    tdAutoLayout            =   0x00000000,  
    tdSequentialLayout      =   0x00000008,  
    tdExplicitLayout        =   0x00000010,  
  
    tdClassSemanticsMask    =   0x00000020,  
    tdClass                 =   0x00000000,  
    tdInterface             =   0x00000020,  
  
    tdAbstract              =   0x00000080,  
    tdSealed                =   0x00000100,  
    tdSpecialName           =   0x00000400,  
  
    tdImport                =   0x00001000,  
    tdSerializable          =   0x00002000,  
    tdWindowsRuntime        =   0x00004000,  
  
    tdStringFormatMask      =   0x00030000,  
    tdAnsiClass             =   0x00000000,  
    tdUnicodeClass          =   0x00010000,  
    tdAutoClass             =   0x00020000,  
    tdCustomFormatClass     =   0x00030000,  
    tdCustomFormatMask      =   0x00C00000,  
  
    tdBeforeFieldInit       =   0x00100000,  
    tdForwarder             =   0x00200000,  
  
    tdReservedMask          =   0x00040800,  
    tdRTSpecialName         =   0x00000800,  
    tdHasSecurity           =   0x00040000,  
  
} CorTypeAttr;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`tdVisibilityMask`|型の可視性の情報を使用します。|  
|`tdNotPublic`|型がパブリック スコープでないことを指定します。|  
|`tdPublic`|型がパブリックのスコープ内であるを指定します。|  
|`tdNestedPublic`|型がパブリックの可視性を持つ入れ子になったことを指定します。|  
|`tdNestedPrivate`|型がプライベートの可視性を持つ入れ子になったことを指定します。|  
|`tdNestedFamily`|ファミリの可視性を持つ型が入れ子になったことを指定します。|  
|`tdNestedAssembly`|アセンブリの可視性を持つ型が入れ子になったことを指定します。|  
|`tdNestedFamANDAssem`|型が属するファミリとアセンブリの可視性を持つ入れ子になっているを指定します。|  
|`tdNestedFamORAssem`|ファミリまたはアセンブリの可視性を持つ型が入れ子になったことを指定します。|  
|`tdLayoutMask`|型のレイアウト情報を取得します。|  
|`tdAutoLayout`|この型のフィールドが自動的にレイアウトされることを指定します。|  
|`tdSequentialLayout`|この型のフィールドが順番にレイアウトするかを指定します。|  
|`tdExplicitLayout`|そのフィールドのレイアウトが明示的に指定されたを指定します。|  
|`tdClassSemanticsMask`|型のセマンティクス情報を取得します。|  
|`tdClass`|型がクラスであることを示します。|  
|`tdInterface`|型がインターフェイスであることを示します。|  
|`tdAbstract`|型が抽象的であることを示します。|  
|`tdSealed`|型を拡張できないことを指定します。|  
|`tdSpecialName`|クラスの名前が特別なことを指定します。 その名前で記述する方法です。|  
|`tdImport`|型がインポートされることを指定します。|  
|`tdSerializable`|型がシリアル化可能なことを指定します。|  
|`tdWindowsRuntime`|この型があることを指定します、[!INCLUDE[wrt](../../../../includes/wrt-md.md)]型です。|  
|`tdStringFormatMask`|文字列のエンコード方法および書式設定方法に関する情報を取得します。|  
|`tdAnsiClass`|この型が、ANSI として LPTSTR を解釈するように指定します。|  
|`tdUnicodeClass`|この型が Unicode として LPTSTR を解釈するように指定します。|  
|`tdAutoClass`|この型が自動的に LPTSTR を解釈することを指定します。|  
|`tdCustomFormatClass`|型が非標準のエンコーディングを指定して指定されたとおり`CustomFormatMask`です。|  
|`tdCustomFormatMask`|このマスクを使用すると、ネイティブの相互運用機能の非標準のエンコード情報を取得できます。 これらの 2 つのビット値の意味は、指定されていません。|  
|`tdBeforeFieldInit`|静的フィールドにアクセスする最初の試行する前に、型を初期化する必要がありますを指定します。|  
|`tdForwarder`|型がエクスポートになっていることを指定し、型フォワーダーです。|  
|`tdReservedMask`|このフラグは、以下のフラグは、共通言語ランタイムによって内部的に使用されます。|  
|`tdRTSpecialName`|名前のエンコーディングに共通言語ランタイムが確認する必要がありますを指定します。|  
|`tdHasSecurity`|型が関連付けられているセキュリティを指定します。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorHdr.h  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
