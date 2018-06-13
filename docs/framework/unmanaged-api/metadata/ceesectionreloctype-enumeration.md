---
title: CeeSectionRelocType 列挙型
ms.date: 03/30/2017
api_name:
- CeeSectionRelocType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionRelocType
helpviewer_keywords:
- CeeSectionRelocType enumeration [.NET Framework metadata]
ms.assetid: 124656f6-0dad-4ceb-9043-d3869ab65cde
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: babd7d87f1bb6f238c347d68814a3ecdaef64b40
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442872"
---
# <a name="ceesectionreloctype-enumeration"></a>CeeSectionRelocType 列挙型
種類に影響する値を提供`reloc`への呼び出しで出力される命令[iceegen::addsectionreloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum  {  
    srRelocAbsolute,  
    srRelocHighLow          = 3,  
    srRelocHighAdj,       
    srRelocMapToken,  
    srRelocRelative,  
    srRelocFilePos,  
    srRelocCodeRelative,  
    srRelocIA64Imm64,  
    srRelocDir64,  
    srRelocIA64PcRel25,  
    srRelocIA64PcRel64,    srRelocAbsoluteTagged,    srRelocSentinel,    srNoBaseReloc       = 0x4000,  
    srRelocPtr          = 0x8000,  
    srRelocAbsolutePtr      = srRelocPtr + srRelocAbsolute,  
    srRelocHighLowPtr       = srRelocPtr + srRelocHighLow,  
    srRelocRelativePtr      = srRelocPtr + srRelocRelative,  
    srRelocIA64Imm64Ptr     = srRelocPtr + srRelocIA64Imm64,  
    srRelocDir64Ptr         = srRelocPtr + srRelocDir64  
    } CeeSectionRelocType;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`srRelocAbsolute`|のみセクションの相対パスを生成`reloc`、.reloc セクションに何も送信します。|  
|`srRelocHighLow`|生成、`reloc`のポインター-サイズの場所。 これは、プラットフォームによっては、BASED_HIGHLOW または BASED_DIR64 に変換されます。|  
|`srRelocHighAdj`|生成、`reloc`上部、下部にある 16 ビットが .reloc テーブル内の次の単語に含まれている、32 ビットの番号の 16 ビットのです。|  
|`srRelocMapToken`|.Reloc セクションに何も送信トークン マップ再配置を生成します。|  
|`srRelocRelative`|値が相対アドレス fixup であることを示します。|  
|`srRelocFilePos`|のみセクションの相対パスを生成`reloc`、.reloc セクションに何も送信します。 これは、`reloc`セクションの仮想アドレスではなくセクションのファイル位置に対する相対パスです。|  
|`srRelocCodeRelative`|コードの相対アドレスのフィックス アップを指定します。|  
|`srRelocIA64Imm64`|生成、`reloc`内、ia64 64 ビットのアドレスに対して`movl`命令します。|  
|`srRelocDir64`|生成、`reloc`の 64 ビットのアドレス。|  
|`srRelocIA64PcRel25`|生成、 `reloc` ia64 で 25 ビット PC の相対アドレスの`br.call`命令します。|  
|`srRelocIA64PcRel64`|生成、 `reloc` ia64 で 64 ビット コンピューターの相対アドレスの`brl.call`命令します。|  
|`srRelocAbsoluteTagged`|30 ビット セクションの相対パスを生成`reloc`, タグが付けられたポインター値で使用されます。|  
|`srRelocSentinel`|この列挙型に追加されたものを確実に sentinel 値は、内部に反映される`reloc`名の配列。|  
|`srNoBaseReloc`|ベースの出力をしないように指定`reloc`です。|  
|`srRelocPtr`|メモリの事前修正内容のセクションではなく、ポインターを示す値のオフセット。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [ICeeGen インターフェイス](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)  
 [AddSectionReloc メソッド](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
