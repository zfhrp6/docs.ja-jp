---
title: "CLSID_RESOLUTION_FLAGS 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLSID_RESOLUTION_FLAGS
api_location: mscoree.dll
api_type: COM
f1_keywords: CLSID_RESOLUTION_FLAGS
helpviewer_keywords: CLSID_RESOLUTION_FLAGS enumeration [.NET Framework hosting]
ms.assetid: cd8b9879-962a-4811-aa46-2e2b6bae0d84
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 17e74e8b39ff9079973063f4ea703607411ab93d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="clsidresolutionflags-enumeration"></a><span data-ttu-id="571af-102">CLSID_RESOLUTION_FLAGS 列挙型</span><span class="sxs-lookup"><span data-stu-id="571af-102">CLSID_RESOLUTION_FLAGS Enumeration</span></span>
<span data-ttu-id="571af-103">共通言語ランタイム (CLR) を解決する方法を示す値を含む、`CLSID`です。</span><span class="sxs-lookup"><span data-stu-id="571af-103">Contains values that indicate how the common language runtime (CLR) should resolve a `CLSID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="571af-104">構文</span><span class="sxs-lookup"><span data-stu-id="571af-104">Syntax</span></span>  
  
```  
typedef enum {  
    CLSID_RESOLUTION_DEFAULT      = 0x0,  
    CLSID_RESOLUTION_REGISTERED   = 0x1  
} CLSID_RESOLUTION_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="571af-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="571af-105">Members</span></span>  
  
|<span data-ttu-id="571af-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="571af-106">Member</span></span>|<span data-ttu-id="571af-107">説明</span><span class="sxs-lookup"><span data-stu-id="571af-107">Description</span></span>|  
|------------|-----------------|  
|`CLSID_RESOLUTION_DEFAULT`|<span data-ttu-id="571af-108">既定の動作を示します。</span><span class="sxs-lookup"><span data-stu-id="571af-108">Indicates the default behavior.</span></span>|  
|`CLSID_RESOLUTION_REGISTERED`|<span data-ttu-id="571af-109">ランタイムは、レジストリ内で検索し、shim のポリシー適用を示します。</span><span class="sxs-lookup"><span data-stu-id="571af-109">Indicates that the runtime searches the registry and applies shim policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="571af-110">要件</span><span class="sxs-lookup"><span data-stu-id="571af-110">Requirements</span></span>  
 <span data-ttu-id="571af-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="571af-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="571af-112">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="571af-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="571af-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="571af-113">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="571af-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="571af-114">See Also</span></span>  
 [<span data-ttu-id="571af-115">ホスティングの列挙体</span><span class="sxs-lookup"><span data-stu-id="571af-115">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
