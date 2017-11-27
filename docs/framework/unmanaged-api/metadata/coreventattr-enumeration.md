---
title: "CorEventAttr 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorEventAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CorEventAttr
helpviewer_keywords: CorEventAttr enumeration [.NET Framework metadata]
ms.assetid: dc2b3281-3820-487e-930d-350b66dc6417
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1a725a40e4c3a447c6cbcacfba311051e781f176
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="coreventattr-enumeration"></a><span data-ttu-id="e61ab-102">CorEventAttr 列挙型</span><span class="sxs-lookup"><span data-stu-id="e61ab-102">CorEventAttr Enumeration</span></span>
<span data-ttu-id="e61ab-103">イベントのメタデータを記述する値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="e61ab-103">Contains values that describe the metadata of an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e61ab-104">構文</span><span class="sxs-lookup"><span data-stu-id="e61ab-104">Syntax</span></span>  
  
```  
typedef enum CorEventAttr {  
  
    evSpecialName           =   0x0200,  
  
    evReservedMask          =   0x0400,  
    evRTSpecialName         =   0x0400,  
  
} CorEventAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="e61ab-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="e61ab-105">Members</span></span>  
  
|<span data-ttu-id="e61ab-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="e61ab-106">Member</span></span>|<span data-ttu-id="e61ab-107">説明</span><span class="sxs-lookup"><span data-stu-id="e61ab-107">Description</span></span>|  
|------------|-----------------|  
|`evSpecialName`|<span data-ttu-id="e61ab-108">イベントは、特別なことと、その名前が記述されているを指定する方法です。</span><span class="sxs-lookup"><span data-stu-id="e61ab-108">Specifies that the event is special, and that its name describes how.</span></span>|  
|`evReservedMask`|<span data-ttu-id="e61ab-109">共通言語ランタイムでは、内部使用に予約されています。</span><span class="sxs-lookup"><span data-stu-id="e61ab-109">Reserved for internal use by the common language runtime.</span></span>|  
|`evRTSpecialName`|<span data-ttu-id="e61ab-110">共通言語ランタイムがイベント名のエンコードを確認する必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="e61ab-110">Specifies that the common language runtime should check the encoding of the event name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e61ab-111">要件</span><span class="sxs-lookup"><span data-stu-id="e61ab-111">Requirements</span></span>  
 <span data-ttu-id="e61ab-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e61ab-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e61ab-113">**ヘッダー:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="e61ab-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="e61ab-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e61ab-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e61ab-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="e61ab-115">See Also</span></span>  
 [<span data-ttu-id="e61ab-116">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="e61ab-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
