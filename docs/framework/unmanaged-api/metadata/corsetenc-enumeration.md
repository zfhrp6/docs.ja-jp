---
title: "CorSetENC 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorSetENC
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSetENC
helpviewer_keywords: CorSetENC enumeration [.NET Framework metadata]
ms.assetid: fe4150e8-071d-43fb-8e06-c3c616dbeed2
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 85a909d92be8bfdb9ada709b54cf252183ff411e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="corsetenc-enumeration"></a><span data-ttu-id="1108e-102">CorSetENC 列挙型</span><span class="sxs-lookup"><span data-stu-id="1108e-102">CorSetENC Enumeration</span></span>
<span data-ttu-id="1108e-103">メタデータの生成中の動作を決定する値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="1108e-103">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1108e-104">構文</span><span class="sxs-lookup"><span data-stu-id="1108e-104">Syntax</span></span>  
  
```  
typedef enum CorSetENC {  
  
    MDSetENCOn                  = 0x00000001,  
    MDSetENCOff                 = 0x00000002,  
  
    MDUpdateENC                 = 0x00000001,  
    MDUpdateFull                = 0x00000002,  
    MDUpdateExtension           = 0x00000003,  
    MDUpdateIncremental         = 0x00000004,  
    MDUpdateDelta               = 0x00000005,  
    MDUpdateMask                = 0x00000007  
  
} CorSetENC;  
```  
  
## <a name="members"></a><span data-ttu-id="1108e-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="1108e-105">Members</span></span>  
  
|<span data-ttu-id="1108e-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="1108e-106">Member</span></span>|<span data-ttu-id="1108e-107">説明</span><span class="sxs-lookup"><span data-stu-id="1108e-107">Description</span></span>|  
|------------|-----------------|  
|`MDSetENCOn`|<span data-ttu-id="1108e-108">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="1108e-108">Obsolete.</span></span>|  
|`MDSetENCOff`|<span data-ttu-id="1108e-109">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="1108e-109">Obsolete.</span></span>|  
|`MDUpdateENC`|<span data-ttu-id="1108e-110">あるメタデータを更新できる一方トークンは移動できないことを示します。</span><span class="sxs-lookup"><span data-stu-id="1108e-110">Indicates that whereas metadata can be updated, tokens cannot be moved.</span></span>|  
|`MDUpdateFull`|<span data-ttu-id="1108e-111">トークンを更新中に移動できることを示します。</span><span class="sxs-lookup"><span data-stu-id="1108e-111">Indicates that tokens can be moved during updates.</span></span>|  
|`MDUpdateExtension`|<span data-ttu-id="1108e-112">更新プログラムが追加ののみで構成できることを示します。</span><span class="sxs-lookup"><span data-stu-id="1108e-112">Indicates that updates can consist only of additions.</span></span> <span data-ttu-id="1108e-113">トークンを移動することはできません。</span><span class="sxs-lookup"><span data-stu-id="1108e-113">Tokens cannot be moved.</span></span>|  
|`MDUpdateIncremental`|<span data-ttu-id="1108e-114">コンパイルが増分であることを示します。</span><span class="sxs-lookup"><span data-stu-id="1108e-114">Indicates that compilation is incremental.</span></span>|  
|`MDUpdateDelta`|<span data-ttu-id="1108e-115">変更されたメタデータだけを保存するかを示します。</span><span class="sxs-lookup"><span data-stu-id="1108e-115">Indicates that only changed metadata should be saved.</span></span>|  
|`MDUpdateMask`|<span data-ttu-id="1108e-116">含む`MDUpdateENC`、`MDUpdateFull`と`MDUpdateIncremental`です。</span><span class="sxs-lookup"><span data-stu-id="1108e-116">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1108e-117">要件</span><span class="sxs-lookup"><span data-stu-id="1108e-117">Requirements</span></span>  
 <span data-ttu-id="1108e-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1108e-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1108e-119">**ヘッダー:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="1108e-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="1108e-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1108e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1108e-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="1108e-121">See Also</span></span>  
 [<span data-ttu-id="1108e-122">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="1108e-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
