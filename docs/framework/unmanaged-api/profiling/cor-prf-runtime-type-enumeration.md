---
title: "COR_PRF_RUNTIME_TYPE 列挙体"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 154773e76046656e4286f4ba12717b6b45e9b069
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="corprfruntimetype-enumeration"></a><span data-ttu-id="4e6bd-102">COR_PRF_RUNTIME_TYPE 列挙体</span><span class="sxs-lookup"><span data-stu-id="4e6bd-102">COR_PRF_RUNTIME_TYPE Enumeration</span></span>
<span data-ttu-id="4e6bd-103">共通言語ランタイム (CLR) のバージョンを示す値が含まれています。 デスクトップまたは Silverlight で使用されている CoreCLR です。</span><span class="sxs-lookup"><span data-stu-id="4e6bd-103">Contains values that indicate the version of the common language runtime (CLR): desktop or CoreCLR, which is used in Silverlight.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e6bd-104">構文</span><span class="sxs-lookup"><span data-stu-id="4e6bd-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    COR_PRF_DESKTOP_CLR = 0x1,  
    COR_PRF_CORE_CLR    = 0x2,  
} COR_PRF_RUNTIME_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="4e6bd-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="4e6bd-105">Members</span></span>  
  
|<span data-ttu-id="4e6bd-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="4e6bd-106">Member</span></span>|<span data-ttu-id="4e6bd-107">説明</span><span class="sxs-lookup"><span data-stu-id="4e6bd-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DESKTOP_CLR`|<span data-ttu-id="4e6bd-108">CLR のデスクトップ バージョン。</span><span class="sxs-lookup"><span data-stu-id="4e6bd-108">The desktop version of the CLR.</span></span>|  
|`COR_PRF_CORE_CLR`|<span data-ttu-id="4e6bd-109">Silverlight で使用される、CLR のコア バージョン。</span><span class="sxs-lookup"><span data-stu-id="4e6bd-109">The core version of the CLR, used in Silverlight.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e6bd-110">コメント</span><span class="sxs-lookup"><span data-stu-id="4e6bd-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e6bd-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="4e6bd-111">Requirements</span></span>  
 <span data-ttu-id="4e6bd-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4e6bd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e6bd-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4e6bd-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4e6bd-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e6bd-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e6bd-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e6bd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e6bd-116">参照</span><span class="sxs-lookup"><span data-stu-id="4e6bd-116">See Also</span></span>  
 [<span data-ttu-id="4e6bd-117">列挙型のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="4e6bd-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
