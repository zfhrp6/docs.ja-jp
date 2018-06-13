---
title: COR_GC_THREAD_STATS_TYPES 列挙体
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS_TYPES
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS_TYPES
helpviewer_keywords:
- COR_GC_THREAD_STATS_TYPES enumeration [.NET Framework hosting]
ms.assetid: aa227704-0ab1-4b08-aee2-1f439762162e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74de8838d7f9ad1995bf7b15699b5589d13a0cab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428838"
---
# <a name="corgcthreadstatstypes-enumeration"></a><span data-ttu-id="f767b-102">COR_GC_THREAD_STATS_TYPES 列挙体</span><span class="sxs-lookup"><span data-stu-id="f767b-102">COR_GC_THREAD_STATS_TYPES Enumeration</span></span>
<span data-ttu-id="f767b-103">スレッドのガベージ コレクションの統計情報を示します。</span><span class="sxs-lookup"><span data-stu-id="f767b-103">Indicates the garbage collection statistics for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f767b-104">構文</span><span class="sxs-lookup"><span data-stu-id="f767b-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_GC_THREAD_HAS_PROMOTED_BYTES  = 0x00000001  
} COR_GC_THREAD_STATS_TYPES;  
```  
  
## <a name="members"></a><span data-ttu-id="f767b-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="f767b-105">Members</span></span>  
  
|<span data-ttu-id="f767b-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="f767b-106">Member</span></span>|<span data-ttu-id="f767b-107">説明</span><span class="sxs-lookup"><span data-stu-id="f767b-107">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_THREAD_HAS_PROMOTED_BYTES`|<span data-ttu-id="f767b-108">スレッドには、最後のガベージ コレクションで昇格されたバイトがあります。</span><span class="sxs-lookup"><span data-stu-id="f767b-108">The thread has bytes that were promoted in the most recent garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f767b-109">要件</span><span class="sxs-lookup"><span data-stu-id="f767b-109">Requirements</span></span>  
 <span data-ttu-id="f767b-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f767b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f767b-111">**ヘッダー:** GCHost.idl、GCHost.h</span><span class="sxs-lookup"><span data-stu-id="f767b-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="f767b-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f767b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f767b-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="f767b-113">See Also</span></span>  
 [<span data-ttu-id="f767b-114">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="f767b-114">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
