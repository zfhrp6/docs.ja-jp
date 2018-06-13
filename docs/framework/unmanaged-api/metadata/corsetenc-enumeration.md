---
title: CorSetENC 列挙型
ms.date: 03/30/2017
api_name:
- CorSetENC
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSetENC
helpviewer_keywords:
- CorSetENC enumeration [.NET Framework metadata]
ms.assetid: fe4150e8-071d-43fb-8e06-c3c616dbeed2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3e09bf424a41445f7e36397775d1578cdf4e7e75
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442788"
---
# <a name="corsetenc-enumeration"></a><span data-ttu-id="b4350-102">CorSetENC 列挙型</span><span class="sxs-lookup"><span data-stu-id="b4350-102">CorSetENC Enumeration</span></span>
<span data-ttu-id="b4350-103">メタデータの生成中の動作を決定する値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="b4350-103">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4350-104">構文</span><span class="sxs-lookup"><span data-stu-id="b4350-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="b4350-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="b4350-105">Members</span></span>  
  
|<span data-ttu-id="b4350-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="b4350-106">Member</span></span>|<span data-ttu-id="b4350-107">説明</span><span class="sxs-lookup"><span data-stu-id="b4350-107">Description</span></span>|  
|------------|-----------------|  
|`MDSetENCOn`|<span data-ttu-id="b4350-108">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="b4350-108">Obsolete.</span></span>|  
|`MDSetENCOff`|<span data-ttu-id="b4350-109">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="b4350-109">Obsolete.</span></span>|  
|`MDUpdateENC`|<span data-ttu-id="b4350-110">あるメタデータを更新できる一方トークンは移動できないことを示します。</span><span class="sxs-lookup"><span data-stu-id="b4350-110">Indicates that whereas metadata can be updated, tokens cannot be moved.</span></span>|  
|`MDUpdateFull`|<span data-ttu-id="b4350-111">トークンを更新中に移動できることを示します。</span><span class="sxs-lookup"><span data-stu-id="b4350-111">Indicates that tokens can be moved during updates.</span></span>|  
|`MDUpdateExtension`|<span data-ttu-id="b4350-112">更新プログラムが追加ののみで構成できることを示します。</span><span class="sxs-lookup"><span data-stu-id="b4350-112">Indicates that updates can consist only of additions.</span></span> <span data-ttu-id="b4350-113">トークンを移動することはできません。</span><span class="sxs-lookup"><span data-stu-id="b4350-113">Tokens cannot be moved.</span></span>|  
|`MDUpdateIncremental`|<span data-ttu-id="b4350-114">コンパイルが増分であることを示します。</span><span class="sxs-lookup"><span data-stu-id="b4350-114">Indicates that compilation is incremental.</span></span>|  
|`MDUpdateDelta`|<span data-ttu-id="b4350-115">変更されたメタデータだけを保存するかを示します。</span><span class="sxs-lookup"><span data-stu-id="b4350-115">Indicates that only changed metadata should be saved.</span></span>|  
|`MDUpdateMask`|<span data-ttu-id="b4350-116">含む`MDUpdateENC`、`MDUpdateFull`と`MDUpdateIncremental`です。</span><span class="sxs-lookup"><span data-stu-id="b4350-116">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b4350-117">要件</span><span class="sxs-lookup"><span data-stu-id="b4350-117">Requirements</span></span>  
 <span data-ttu-id="b4350-118">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b4350-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4350-119">**ヘッダー:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="b4350-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b4350-120">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4350-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4350-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="b4350-121">See Also</span></span>  
 [<span data-ttu-id="b4350-122">メタデータ列挙型</span><span class="sxs-lookup"><span data-stu-id="b4350-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
