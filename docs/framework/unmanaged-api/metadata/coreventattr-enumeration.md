---
title: "CorEventAttr 列挙型"
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
- CorEventAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorEventAttr
helpviewer_keywords:
- CorEventAttr enumeration [.NET Framework metadata]
ms.assetid: dc2b3281-3820-487e-930d-350b66dc6417
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c4302ff7627bf5e06f3c1b1263ec38a31393d411
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="coreventattr-enumeration"></a><span data-ttu-id="1318b-102">CorEventAttr 列挙型</span><span class="sxs-lookup"><span data-stu-id="1318b-102">CorEventAttr Enumeration</span></span>
<span data-ttu-id="1318b-103">イベントのメタデータを記述する値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="1318b-103">Contains values that describe the metadata of an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1318b-104">構文</span><span class="sxs-lookup"><span data-stu-id="1318b-104">Syntax</span></span>  
  
```  
typedef enum CorEventAttr {  
  
    evSpecialName           =   0x0200,  
  
    evReservedMask          =   0x0400,  
    evRTSpecialName         =   0x0400,  
  
} CorEventAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="1318b-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="1318b-105">Members</span></span>  
  
|<span data-ttu-id="1318b-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="1318b-106">Member</span></span>|<span data-ttu-id="1318b-107">説明</span><span class="sxs-lookup"><span data-stu-id="1318b-107">Description</span></span>|  
|------------|-----------------|  
|`evSpecialName`|<span data-ttu-id="1318b-108">イベントは、特別なことと、その名前が記述されているを指定する方法です。</span><span class="sxs-lookup"><span data-stu-id="1318b-108">Specifies that the event is special, and that its name describes how.</span></span>|  
|`evReservedMask`|<span data-ttu-id="1318b-109">共通言語ランタイムでは、内部使用に予約されています。</span><span class="sxs-lookup"><span data-stu-id="1318b-109">Reserved for internal use by the common language runtime.</span></span>|  
|`evRTSpecialName`|<span data-ttu-id="1318b-110">共通言語ランタイムがイベント名のエンコードを確認する必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="1318b-110">Specifies that the common language runtime should check the encoding of the event name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1318b-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="1318b-111">Requirements</span></span>  
 <span data-ttu-id="1318b-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1318b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1318b-113">**ヘッダー:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="1318b-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="1318b-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1318b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1318b-115">参照</span><span class="sxs-lookup"><span data-stu-id="1318b-115">See Also</span></span>  
 [<span data-ttu-id="1318b-116">メタデータ列挙型</span><span class="sxs-lookup"><span data-stu-id="1318b-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
