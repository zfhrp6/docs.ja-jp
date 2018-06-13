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
# <a name="ceesectionreloctype-enumeration"></a><span data-ttu-id="a320a-102">CeeSectionRelocType 列挙型</span><span class="sxs-lookup"><span data-stu-id="a320a-102">CeeSectionRelocType Enumeration</span></span>
<span data-ttu-id="a320a-103">種類に影響する値を提供`reloc`への呼び出しで出力される命令[iceegen::addsectionreloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="a320a-103">Provides values to influence the type of `reloc` instruction emitted in a call to [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a320a-104">構文</span><span class="sxs-lookup"><span data-stu-id="a320a-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="a320a-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="a320a-105">Members</span></span>  
  
|<span data-ttu-id="a320a-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="a320a-106">Member</span></span>|<span data-ttu-id="a320a-107">説明</span><span class="sxs-lookup"><span data-stu-id="a320a-107">Description</span></span>|  
|------------|-----------------|  
|`srRelocAbsolute`|<span data-ttu-id="a320a-108">のみセクションの相対パスを生成`reloc`、.reloc セクションに何も送信します。</span><span class="sxs-lookup"><span data-stu-id="a320a-108">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span>|  
|`srRelocHighLow`|<span data-ttu-id="a320a-109">生成、`reloc`のポインター-サイズの場所。</span><span class="sxs-lookup"><span data-stu-id="a320a-109">Generates a `reloc` for a pointer-sized location.</span></span> <span data-ttu-id="a320a-110">これは、プラットフォームによっては、BASED_HIGHLOW または BASED_DIR64 に変換されます。</span><span class="sxs-lookup"><span data-stu-id="a320a-110">This is transformed into BASED_HIGHLOW or BASED_DIR64 depending on the platform.</span></span>|  
|`srRelocHighAdj`|<span data-ttu-id="a320a-111">生成、`reloc`上部、下部にある 16 ビットが .reloc テーブル内の次の単語に含まれている、32 ビットの番号の 16 ビットのです。</span><span class="sxs-lookup"><span data-stu-id="a320a-111">Generates a `reloc` for the top 16 bits of a 32-bit number, where the bottom 16 bits are included in the next word in the .reloc table.</span></span>|  
|`srRelocMapToken`|<span data-ttu-id="a320a-112">.Reloc セクションに何も送信トークン マップ再配置を生成します。</span><span class="sxs-lookup"><span data-stu-id="a320a-112">Generates a token map relocation, sending nothing into a .reloc section.</span></span>|  
|`srRelocRelative`|<span data-ttu-id="a320a-113">値が相対アドレス fixup であることを示します。</span><span class="sxs-lookup"><span data-stu-id="a320a-113">Indicates that the value is a relative address fixup.</span></span>|  
|`srRelocFilePos`|<span data-ttu-id="a320a-114">のみセクションの相対パスを生成`reloc`、.reloc セクションに何も送信します。</span><span class="sxs-lookup"><span data-stu-id="a320a-114">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span> <span data-ttu-id="a320a-115">これは、`reloc`セクションの仮想アドレスではなくセクションのファイル位置に対する相対パスです。</span><span class="sxs-lookup"><span data-stu-id="a320a-115">This `reloc` is relative to the file position of the section, not the section's virtual address.</span></span>|  
|`srRelocCodeRelative`|<span data-ttu-id="a320a-116">コードの相対アドレスのフィックス アップを指定します。</span><span class="sxs-lookup"><span data-stu-id="a320a-116">Specifies a code-relative address fixup.</span></span>|  
|`srRelocIA64Imm64`|<span data-ttu-id="a320a-117">生成、`reloc`内、ia64 64 ビットのアドレスに対して`movl`命令します。</span><span class="sxs-lookup"><span data-stu-id="a320a-117">Generates a `reloc` for a 64 bit address in an ia64 `movl` instruction.</span></span>|  
|`srRelocDir64`|<span data-ttu-id="a320a-118">生成、`reloc`の 64 ビットのアドレス。</span><span class="sxs-lookup"><span data-stu-id="a320a-118">Generates a `reloc` for a 64-bit address.</span></span>|  
|`srRelocIA64PcRel25`|<span data-ttu-id="a320a-119">生成、 `reloc` ia64 で 25 ビット PC の相対アドレスの`br.call`命令します。</span><span class="sxs-lookup"><span data-stu-id="a320a-119">Generate a `reloc` for a 25-bit PC-relative address in an ia64 `br.call` instruction.</span></span>|  
|`srRelocIA64PcRel64`|<span data-ttu-id="a320a-120">生成、 `reloc` ia64 で 64 ビット コンピューターの相対アドレスの`brl.call`命令します。</span><span class="sxs-lookup"><span data-stu-id="a320a-120">Generates a `reloc` for a 64-bit PC-relative address in an ia64 `brl.call` instruction.</span></span>|  
|`srRelocAbsoluteTagged`|<span data-ttu-id="a320a-121">30 ビット セクションの相対パスを生成`reloc`, タグが付けられたポインター値で使用されます。</span><span class="sxs-lookup"><span data-stu-id="a320a-121">Generates a 30-bit section-relative `reloc`, used for tagged pointer values.</span></span>|  
|`srRelocSentinel`|<span data-ttu-id="a320a-122">この列挙型に追加されたものを確実に sentinel 値は、内部に反映される`reloc`名の配列。</span><span class="sxs-lookup"><span data-stu-id="a320a-122">A sentinel value to help ensure any additions to this enum are reflected to the internal `reloc` name array.</span></span>|  
|`srNoBaseReloc`|<span data-ttu-id="a320a-123">ベースの出力をしないように指定`reloc`です。</span><span class="sxs-lookup"><span data-stu-id="a320a-123">Specifies not to emit a base `reloc`.</span></span>|  
|`srRelocPtr`|<span data-ttu-id="a320a-124">メモリの事前修正内容のセクションではなく、ポインターを示す値のオフセット。</span><span class="sxs-lookup"><span data-stu-id="a320a-124">A value indicating that the pre-fixup contents of memory are a pointer rather than a section offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a320a-125">要件</span><span class="sxs-lookup"><span data-stu-id="a320a-125">Requirements</span></span>  
 <span data-ttu-id="a320a-126">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a320a-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a320a-127">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a320a-127">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a320a-128">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="a320a-128">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a320a-129">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a320a-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a320a-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="a320a-130">See Also</span></span>  
 [<span data-ttu-id="a320a-131">メタデータ列挙型</span><span class="sxs-lookup"><span data-stu-id="a320a-131">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [<span data-ttu-id="a320a-132">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a320a-132">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)  
 [<span data-ttu-id="a320a-133">AddSectionReloc メソッド</span><span class="sxs-lookup"><span data-stu-id="a320a-133">AddSectionReloc Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
