---
title: "GetCachePath 関数"
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
- GetCachePath
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- GetCachePath
helpviewer_keywords:
- GetCachePath function [.NET Framework fusion]
ms.assetid: d977ad29-6619-42e1-b0be-bc25ea950e80
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 371dab83d7441681b9d6bd5723bcd8c3caadb50e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getcachepath-function"></a><span data-ttu-id="bb85b-102">GetCachePath 関数</span><span class="sxs-lookup"><span data-stu-id="bb85b-102">GetCachePath Function</span></span>
<span data-ttu-id="bb85b-103">指定したフラグを使用して、キャッシュされたアセンブリへのパスを取得します。</span><span class="sxs-lookup"><span data-stu-id="bb85b-103">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb85b-104">構文</span><span class="sxs-lookup"><span data-stu-id="bb85b-104">Syntax</span></span>  
  
```  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bb85b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bb85b-105">Parameters</span></span>  
 `dwCacheFlags`  
 <span data-ttu-id="bb85b-106">[in][ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md)キャッシュされたアセンブリのソースを示す値。</span><span class="sxs-lookup"><span data-stu-id="bb85b-106">[in] An [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) value that indicates the source of the cached assembly.</span></span>  
  
 `pwzCachePath`  
 <span data-ttu-id="bb85b-107">[out]パスに返されたポインター。</span><span class="sxs-lookup"><span data-stu-id="bb85b-107">[out] The returned pointer to the path.</span></span>  
  
 `pcchPath`  
 <span data-ttu-id="bb85b-108">[入力、出力].要求の最大長`pwzCachePath`、関数が戻るとき、実際の長さと`pwzCachePath`です。</span><span class="sxs-lookup"><span data-stu-id="bb85b-108">[in, out] The requested maximum length of `pwzCachePath`, and upon return, the actual length of `pwzCachePath`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb85b-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="bb85b-109">Requirements</span></span>  
 <span data-ttu-id="bb85b-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="bb85b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb85b-111">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="bb85b-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="bb85b-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb85b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb85b-113">参照</span><span class="sxs-lookup"><span data-stu-id="bb85b-113">See Also</span></span>  
 [<span data-ttu-id="bb85b-114">ASM_CACHE_FLAGS 列挙型</span><span class="sxs-lookup"><span data-stu-id="bb85b-114">ASM_CACHE_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md)  
 [<span data-ttu-id="bb85b-115">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="bb85b-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
