---
title: "COR_PRF_JIT_CACHE 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_JIT_CACHE
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_JIT_CACHE
helpviewer_keywords: COR_PRF_JIT_CACHE enumeration [.NET Framework profiling]
ms.assetid: e7b8f6b4-95bc-4ba5-b9eb-f5590a7326a4
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 08fe81321e958d61c1aae86ae366077b563dba3e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="corprfjitcache-enumeration"></a><span data-ttu-id="0d14d-102">COR_PRF_JIT_CACHE 列挙型</span><span class="sxs-lookup"><span data-stu-id="0d14d-102">COR_PRF_JIT_CACHE Enumeration</span></span>
<span data-ttu-id="0d14d-103">キャッシュされている関数検索の結果を示します。</span><span class="sxs-lookup"><span data-stu-id="0d14d-103">Indicates the result of a cached function search.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0d14d-104">`COR_PRF_CACHED_FUNCTION_FOUND`ゼロの値があり、その`COR_PRF_JIT_CACHE`ブール サロゲートとして使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="0d14d-104">`COR_PRF_CACHED_FUNCTION_FOUND` has a value of zero, so `COR_PRF_JIT_CACHE` cannot be used as a Boolean surrogate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d14d-105">構文</span><span class="sxs-lookup"><span data-stu-id="0d14d-105">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_CACHED_FUNCTION_FOUND,  
    COR_PRF_CACHED_FUNCTION_NOT_FOUND  
} COR_PRF_JIT_CACHE;  
```  
  
## <a name="members"></a><span data-ttu-id="0d14d-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="0d14d-106">Members</span></span>  
  
|<span data-ttu-id="0d14d-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="0d14d-107">Member</span></span>|<span data-ttu-id="0d14d-108">説明</span><span class="sxs-lookup"><span data-stu-id="0d14d-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FUNCTION_FOUND`|<span data-ttu-id="0d14d-109">検索では、関数が見つかりました。</span><span class="sxs-lookup"><span data-stu-id="0d14d-109">The search found the function.</span></span>|  
|`COR_PRF_FUNCTION_NOT_FOUND`|<span data-ttu-id="0d14d-110">検索は、関数を検出しませんでした。</span><span class="sxs-lookup"><span data-stu-id="0d14d-110">The search did not find the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0d14d-111">要件</span><span class="sxs-lookup"><span data-stu-id="0d14d-111">Requirements</span></span>  
 <span data-ttu-id="0d14d-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0d14d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d14d-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0d14d-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0d14d-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d14d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d14d-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d14d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d14d-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="0d14d-116">See Also</span></span>  
 [<span data-ttu-id="0d14d-117">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="0d14d-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
