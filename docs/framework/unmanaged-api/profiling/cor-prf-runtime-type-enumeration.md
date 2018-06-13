---
title: COR_PRF_RUNTIME_TYPE 列挙体
ms.date: 03/30/2017
api_name:
- COR_PRF_RUNTIME_TYPE Enumeration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_RUNTIME_TYPE
helpviewer_keywords:
- COR_PRF_RUNTIME_TYPE enumeration [.NET Framework profiling]
ms.assetid: 35449514-333f-4918-9c60-7aa198d655d2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 28e6e95bbcca35ad39f30adcf100519748c02838
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449999"
---
# <a name="corprfruntimetype-enumeration"></a><span data-ttu-id="9d606-102">COR_PRF_RUNTIME_TYPE 列挙体</span><span class="sxs-lookup"><span data-stu-id="9d606-102">COR_PRF_RUNTIME_TYPE Enumeration</span></span>
<span data-ttu-id="9d606-103">共通言語ランタイム (CLR) のバージョンを示す値が含まれています。 デスクトップまたは Silverlight で使用されている CoreCLR です。</span><span class="sxs-lookup"><span data-stu-id="9d606-103">Contains values that indicate the version of the common language runtime (CLR): desktop or CoreCLR, which is used in Silverlight.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d606-104">構文</span><span class="sxs-lookup"><span data-stu-id="9d606-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    COR_PRF_DESKTOP_CLR = 0x1,  
    COR_PRF_CORE_CLR    = 0x2,  
} COR_PRF_RUNTIME_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="9d606-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="9d606-105">Members</span></span>  
  
|<span data-ttu-id="9d606-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="9d606-106">Member</span></span>|<span data-ttu-id="9d606-107">説明</span><span class="sxs-lookup"><span data-stu-id="9d606-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DESKTOP_CLR`|<span data-ttu-id="9d606-108">CLR のデスクトップ バージョン。</span><span class="sxs-lookup"><span data-stu-id="9d606-108">The desktop version of the CLR.</span></span>|  
|`COR_PRF_CORE_CLR`|<span data-ttu-id="9d606-109">Silverlight で使用される、CLR のコア バージョン。</span><span class="sxs-lookup"><span data-stu-id="9d606-109">The core version of the CLR, used in Silverlight.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d606-110">コメント</span><span class="sxs-lookup"><span data-stu-id="9d606-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d606-111">要件</span><span class="sxs-lookup"><span data-stu-id="9d606-111">Requirements</span></span>  
 <span data-ttu-id="9d606-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9d606-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d606-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9d606-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9d606-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d606-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d606-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d606-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d606-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="9d606-116">See Also</span></span>  
 [<span data-ttu-id="9d606-117">列挙型のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="9d606-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
