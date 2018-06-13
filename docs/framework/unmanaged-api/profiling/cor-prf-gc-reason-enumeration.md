---
title: COR_PRF_GC_REASON 列挙型
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_REASON
helpviewer_keywords:
- COR_PRF_GC_REASON enumeration [.NET Framework profiling]
ms.assetid: 72822b95-a7fb-485e-9d55-1cb016d9a458
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 63f6ea4a348b3035a1f0b1d3e00f61f689915fa2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450100"
---
# <a name="corprfgcreason-enumeration"></a><span data-ttu-id="1406e-102">COR_PRF_GC_REASON 列挙型</span><span class="sxs-lookup"><span data-stu-id="1406e-102">COR_PRF_GC_REASON Enumeration</span></span>
<span data-ttu-id="1406e-103">ガベージ コレクションが発生している理由を示します。</span><span class="sxs-lookup"><span data-stu-id="1406e-103">Indicates the reason that garbage collection is occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1406e-104">構文</span><span class="sxs-lookup"><span data-stu-id="1406e-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_INDUCED = 1,  
    COR_PRF_GC_OTHER = 0  
} COR_PRF_GC_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="1406e-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="1406e-105">Members</span></span>  
  
|<span data-ttu-id="1406e-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="1406e-106">Member</span></span>|<span data-ttu-id="1406e-107">説明</span><span class="sxs-lookup"><span data-stu-id="1406e-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_INDUCED`|<span data-ttu-id="1406e-108">ガベージ コレクションが発生しました。 によって、<xref:System.GC.Collect%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="1406e-108">The garbage collection was induced by a <xref:System.GC.Collect%2A> method.</span></span>|  
|`COR_PRF_GC_OTHER`|<span data-ttu-id="1406e-109">その理由は、指定されていません。</span><span class="sxs-lookup"><span data-stu-id="1406e-109">The reason is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1406e-110">要件</span><span class="sxs-lookup"><span data-stu-id="1406e-110">Requirements</span></span>  
 <span data-ttu-id="1406e-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1406e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1406e-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1406e-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1406e-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1406e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1406e-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1406e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1406e-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="1406e-115">See Also</span></span>  
 [<span data-ttu-id="1406e-116">列挙型のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="1406e-116">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
