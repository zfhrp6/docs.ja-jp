---
title: "CorManifestResourceFlags 列挙型"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7a1ad2aa505ba77f136a28b2cfa9f1fa357c37ab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="cormanifestresourceflags-enumeration"></a><span data-ttu-id="7379b-102">CorManifestResourceFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="7379b-102">CorManifestResourceFlags Enumeration</span></span>
<span data-ttu-id="7379b-103">アセンブリ マニフェストでエンコードされているリソースの可視性を示します。</span><span class="sxs-lookup"><span data-stu-id="7379b-103">Indicates the visibility of resources encoded in an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7379b-104">構文</span><span class="sxs-lookup"><span data-stu-id="7379b-104">Syntax</span></span>  
  
```  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="7379b-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="7379b-105">Members</span></span>  
  
|<span data-ttu-id="7379b-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="7379b-106">Member</span></span>|<span data-ttu-id="7379b-107">説明</span><span class="sxs-lookup"><span data-stu-id="7379b-107">Description</span></span>|  
|------------|-----------------|  
|`mrVisibilityMask`|<span data-ttu-id="7379b-108">予約済み。</span><span class="sxs-lookup"><span data-stu-id="7379b-108">Reserved.</span></span>|  
|`mrPublic`|<span data-ttu-id="7379b-109">リソースはパブリックです。</span><span class="sxs-lookup"><span data-stu-id="7379b-109">The resources are public.</span></span>|  
|`mrPrivate`|<span data-ttu-id="7379b-110">リソースはプライベートです。</span><span class="sxs-lookup"><span data-stu-id="7379b-110">The resources are private.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7379b-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="7379b-111">Requirements</span></span>  
 <span data-ttu-id="7379b-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7379b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7379b-113">**ヘッダー:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="7379b-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="7379b-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7379b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7379b-115">参照</span><span class="sxs-lookup"><span data-stu-id="7379b-115">See Also</span></span>  
 [<span data-ttu-id="7379b-116">メタデータ列挙型</span><span class="sxs-lookup"><span data-stu-id="7379b-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
