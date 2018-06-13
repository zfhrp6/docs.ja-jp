---
title: CorManifestResourceFlags 列挙型
ms.date: 03/30/2017
api_name:
- CorManifestResourceFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorManifestResourceFlags
helpviewer_keywords:
- CorManifestResourceFlags enumeration [.NET Framework metadata]
ms.assetid: 1b0306b7-622b-4b57-8edc-3c713bb147ae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 21cce26c94d26f6c079fca644a31bf83cd1a6432
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440711"
---
# <a name="cormanifestresourceflags-enumeration"></a><span data-ttu-id="c8c63-102">CorManifestResourceFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="c8c63-102">CorManifestResourceFlags Enumeration</span></span>
<span data-ttu-id="c8c63-103">アセンブリ マニフェストでエンコードされているリソースの可視性を示します。</span><span class="sxs-lookup"><span data-stu-id="c8c63-103">Indicates the visibility of resources encoded in an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8c63-104">構文</span><span class="sxs-lookup"><span data-stu-id="c8c63-104">Syntax</span></span>  
  
```  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="c8c63-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="c8c63-105">Members</span></span>  
  
|<span data-ttu-id="c8c63-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="c8c63-106">Member</span></span>|<span data-ttu-id="c8c63-107">説明</span><span class="sxs-lookup"><span data-stu-id="c8c63-107">Description</span></span>|  
|------------|-----------------|  
|`mrVisibilityMask`|<span data-ttu-id="c8c63-108">予約済み。</span><span class="sxs-lookup"><span data-stu-id="c8c63-108">Reserved.</span></span>|  
|`mrPublic`|<span data-ttu-id="c8c63-109">リソースはパブリックです。</span><span class="sxs-lookup"><span data-stu-id="c8c63-109">The resources are public.</span></span>|  
|`mrPrivate`|<span data-ttu-id="c8c63-110">リソースはプライベートです。</span><span class="sxs-lookup"><span data-stu-id="c8c63-110">The resources are private.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c8c63-111">要件</span><span class="sxs-lookup"><span data-stu-id="c8c63-111">Requirements</span></span>  
 <span data-ttu-id="c8c63-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c8c63-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8c63-113">**ヘッダー:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="c8c63-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="c8c63-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8c63-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8c63-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="c8c63-115">See Also</span></span>  
 [<span data-ttu-id="c8c63-116">メタデータ列挙型</span><span class="sxs-lookup"><span data-stu-id="c8c63-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
