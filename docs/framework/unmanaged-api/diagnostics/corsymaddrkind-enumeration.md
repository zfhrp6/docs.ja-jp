---
title: "CorSymAddrKind 列挙体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 300913f9ea89044e425f9f05856d13fa15cdc015
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="corsymaddrkind-enumeration"></a><span data-ttu-id="200e9-102">CorSymAddrKind 列挙体</span><span class="sxs-lookup"><span data-stu-id="200e9-102">CorSymAddrKind Enumeration</span></span>
<span data-ttu-id="200e9-103">メモリ アドレスの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="200e9-103">Indicates the type of memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="200e9-104">構文</span><span class="sxs-lookup"><span data-stu-id="200e9-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="200e9-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="200e9-105">Members</span></span>  
  
|<span data-ttu-id="200e9-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="200e9-106">Member</span></span>|<span data-ttu-id="200e9-107">説明</span><span class="sxs-lookup"><span data-stu-id="200e9-107">Description</span></span>|  
|------------|-----------------|  
|`ADDR_IL_OFFSET`|<span data-ttu-id="200e9-108">Microsoft intermediate language (MSIL) ローカル変数またはパラメーター インデックスを示します。</span><span class="sxs-lookup"><span data-stu-id="200e9-108">Indicates a Microsoft intermediate language (MSIL) local variable or parameter index.</span></span>|  
|`ADDR_NATIVE_RVA`|<span data-ttu-id="200e9-109">モジュールへの相対仮想アドレスを示します。</span><span class="sxs-lookup"><span data-stu-id="200e9-109">Indicates a relative virtual address into a module.</span></span>|  
|`ADDR_NATIVE_REGISTER`|<span data-ttu-id="200e9-110">CPU レジスタを示します。</span><span class="sxs-lookup"><span data-stu-id="200e9-110">Indicates a CPU register.</span></span>|  
|`ADDR_NATIVE_REGREL`|<span data-ttu-id="200e9-111">最初のアドレスは、レジスタと 2 番目のアドレスは、オフセットを示します。</span><span class="sxs-lookup"><span data-stu-id="200e9-111">Indicates that the first address is a register and the second address is an offset.</span></span>|  
|`ADDR_NATIVE_OFFSET`|<span data-ttu-id="200e9-112">ベース アドレスからのオフセットを示します。</span><span class="sxs-lookup"><span data-stu-id="200e9-112">Indicates an offset from a base address.</span></span>|  
|`ADDR_NATIVE_REGREG`|<span data-ttu-id="200e9-113">最初のアドレスは、レジスタの低部、2 つ目は高い部分を示します。</span><span class="sxs-lookup"><span data-stu-id="200e9-113">Indicates that the first address is the low portion of a register, and the second address is the high portion.</span></span>|  
|`ADDR_NATIVE_REGSTK`|<span data-ttu-id="200e9-114">ことを示します最初のアドレスは、レジスタの不足部分であり、2 つ目は、高の部分では、3 番目のオフセット。</span><span class="sxs-lookup"><span data-stu-id="200e9-114">Indicates that the first address is the low portion of a register, the second is the high portion, and the third is an offset.</span></span>|  
|`ADDR_NATIVE_STKREG`|<span data-ttu-id="200e9-115">最初のアドレスは、レジスタ、2 番目のオフセット、そのが、3 番目のレジスタの高い部分を示します。</span><span class="sxs-lookup"><span data-stu-id="200e9-115">Indicates that the first address is a register, the second is an offset, and the third is the high portion of the register.</span></span>|  
|`ADDR_BITFIELD`|<span data-ttu-id="200e9-116">最初のアドレスは、フィールドの開始、2 番目のアドレスは、フィールド長を示します。</span><span class="sxs-lookup"><span data-stu-id="200e9-116">Indicates that the first address is the start of a field and the second address is the field length.</span></span>|  
|`ADDR_NATIVE_ISECTOFFSET`|<span data-ttu-id="200e9-117">最初のアドレスは、セクションと 2 番目のアドレスは、オフセットを示します。</span><span class="sxs-lookup"><span data-stu-id="200e9-117">Indicates that the first address is the section and the second address is an offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="200e9-118">必要条件</span><span class="sxs-lookup"><span data-stu-id="200e9-118">Requirements</span></span>  
 <span data-ttu-id="200e9-119">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="200e9-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="200e9-120">参照</span><span class="sxs-lookup"><span data-stu-id="200e9-120">See Also</span></span>  
 [<span data-ttu-id="200e9-121">シンボル ストア診断列挙型</span><span class="sxs-lookup"><span data-stu-id="200e9-121">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
