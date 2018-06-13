---
title: GetCachePath 関数
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 42bae646b0b1cdd451e01d55ed5b218f3660bb5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429479"
---
# <a name="getcachepath-function"></a><span data-ttu-id="0a705-102">GetCachePath 関数</span><span class="sxs-lookup"><span data-stu-id="0a705-102">GetCachePath Function</span></span>
<span data-ttu-id="0a705-103">指定したフラグを使用して、キャッシュされたアセンブリへのパスを取得します。</span><span class="sxs-lookup"><span data-stu-id="0a705-103">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a705-104">構文</span><span class="sxs-lookup"><span data-stu-id="0a705-104">Syntax</span></span>  
  
```  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0a705-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a705-105">Parameters</span></span>  
 `dwCacheFlags`  
 <span data-ttu-id="0a705-106">[in][ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md)キャッシュされたアセンブリのソースを示す値。</span><span class="sxs-lookup"><span data-stu-id="0a705-106">[in] An [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) value that indicates the source of the cached assembly.</span></span>  
  
 `pwzCachePath`  
 <span data-ttu-id="0a705-107">[out]パスに返されたポインター。</span><span class="sxs-lookup"><span data-stu-id="0a705-107">[out] The returned pointer to the path.</span></span>  
  
 `pcchPath`  
 <span data-ttu-id="0a705-108">[入力、出力].要求の最大長`pwzCachePath`、関数が戻るとき、実際の長さと`pwzCachePath`です。</span><span class="sxs-lookup"><span data-stu-id="0a705-108">[in, out] The requested maximum length of `pwzCachePath`, and upon return, the actual length of `pwzCachePath`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a705-109">要件</span><span class="sxs-lookup"><span data-stu-id="0a705-109">Requirements</span></span>  
 <span data-ttu-id="0a705-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0a705-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a705-111">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="0a705-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="0a705-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a705-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a705-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="0a705-113">See Also</span></span>  
 [<span data-ttu-id="0a705-114">ASM_CACHE_FLAGS 列挙型</span><span class="sxs-lookup"><span data-stu-id="0a705-114">ASM_CACHE_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md)  
 [<span data-ttu-id="0a705-115">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="0a705-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
