---
title: "CorSymAddrKind 列挙体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorSymAddrKind
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSymAddrKind
helpviewer_keywords: CorSymAddrKind enumeration [.NET Framework debugging]
ms.assetid: 3ef841c2-cade-42ee-ba34-2ef91d6d0879
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 56bb55d9c9f85ae8f8112f16dcf552295699826d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="corsymaddrkind-enumeration"></a><span data-ttu-id="ce0ab-102">CorSymAddrKind 列挙体</span><span class="sxs-lookup"><span data-stu-id="ce0ab-102">CorSymAddrKind Enumeration</span></span>
<span data-ttu-id="ce0ab-103">メモリ アドレスの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="ce0ab-103">Indicates the type of memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce0ab-104">構文</span><span class="sxs-lookup"><span data-stu-id="ce0ab-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="ce0ab-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="ce0ab-105">Members</span></span>  
  
|<span data-ttu-id="ce0ab-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="ce0ab-106">Member</span></span>|<span data-ttu-id="ce0ab-107">説明</span><span class="sxs-lookup"><span data-stu-id="ce0ab-107">Description</span></span>|  
|------------|-----------------|  
|`ADDR_IL_OFFSET`|<span data-ttu-id="ce0ab-108">Microsoft intermediate language (MSIL) ローカル変数またはパラメーター インデックスを示します。</span><span class="sxs-lookup"><span data-stu-id="ce0ab-108">Indicates a Microsoft intermediate language (MSIL) local variable or parameter index.</span></span>|  
|`ADDR_NATIVE_RVA`|<span data-ttu-id="ce0ab-109">モジュールへの相対仮想アドレスを示します。</span><span class="sxs-lookup"><span data-stu-id="ce0ab-109">Indicates a relative virtual address into a module.</span></span>|  
|`ADDR_NATIVE_REGISTER`|<span data-ttu-id="ce0ab-110">CPU レジスタを示します。</span><span class="sxs-lookup"><span data-stu-id="ce0ab-110">Indicates a CPU register.</span></span>|  
|`ADDR_NATIVE_REGREL`|<span data-ttu-id="ce0ab-111">最初のアドレスは、レジスタと 2 番目のアドレスは、オフセットを示します。</span><span class="sxs-lookup"><span data-stu-id="ce0ab-111">Indicates that the first address is a register and the second address is an offset.</span></span>|  
|`ADDR_NATIVE_OFFSET`|<span data-ttu-id="ce0ab-112">ベース アドレスからのオフセットを示します。</span><span class="sxs-lookup"><span data-stu-id="ce0ab-112">Indicates an offset from a base address.</span></span>|  
|`ADDR_NATIVE_REGREG`|<span data-ttu-id="ce0ab-113">最初のアドレスは、レジスタの低部、2 つ目は高い部分を示します。</span><span class="sxs-lookup"><span data-stu-id="ce0ab-113">Indicates that the first address is the low portion of a register, and the second address is the high portion.</span></span>|  
|`ADDR_NATIVE_REGSTK`|<span data-ttu-id="ce0ab-114">ことを示します最初のアドレスは、レジスタの不足部分であり、2 つ目は、高の部分では、3 番目のオフセット。</span><span class="sxs-lookup"><span data-stu-id="ce0ab-114">Indicates that the first address is the low portion of a register, the second is the high portion, and the third is an offset.</span></span>|  
|`ADDR_NATIVE_STKREG`|<span data-ttu-id="ce0ab-115">最初のアドレスは、レジスタ、2 番目のオフセット、そのが、3 番目のレジスタの高い部分を示します。</span><span class="sxs-lookup"><span data-stu-id="ce0ab-115">Indicates that the first address is a register, the second is an offset, and the third is the high portion of the register.</span></span>|  
|`ADDR_BITFIELD`|<span data-ttu-id="ce0ab-116">最初のアドレスは、フィールドの開始、2 番目のアドレスは、フィールド長を示します。</span><span class="sxs-lookup"><span data-stu-id="ce0ab-116">Indicates that the first address is the start of a field and the second address is the field length.</span></span>|  
|`ADDR_NATIVE_ISECTOFFSET`|<span data-ttu-id="ce0ab-117">最初のアドレスは、セクションと 2 番目のアドレスは、オフセットを示します。</span><span class="sxs-lookup"><span data-stu-id="ce0ab-117">Indicates that the first address is the section and the second address is an offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ce0ab-118">要件</span><span class="sxs-lookup"><span data-stu-id="ce0ab-118">Requirements</span></span>  
 <span data-ttu-id="ce0ab-119">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ce0ab-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce0ab-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="ce0ab-120">See Also</span></span>  
 [<span data-ttu-id="ce0ab-121">シンボル ストア診断列挙体</span><span class="sxs-lookup"><span data-stu-id="ce0ab-121">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
