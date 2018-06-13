---
title: ASM_CACHE_FLAGS 列挙型
ms.date: 03/30/2017
api_name:
- ASM_CACHE_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_CACHE_FLAGS
helpviewer_keywords:
- ASM_CACHE_FLAGS enumeration [.NET Framework fusion]
ms.assetid: 82e9a7da-321b-48b8-b239-52eaffda6be8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ddf0f01db73a873d2dd823e1f754b970ae8aa056
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430474"
---
# <a name="asmcacheflags-enumeration"></a><span data-ttu-id="6f65b-102">ASM_CACHE_FLAGS 列挙型</span><span class="sxs-lookup"><span data-stu-id="6f65b-102">ASM_CACHE_FLAGS Enumeration</span></span>
<span data-ttu-id="6f65b-103">によって表されるアセンブリのソースを示す[IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)グローバル アセンブリ キャッシュにします。</span><span class="sxs-lookup"><span data-stu-id="6f65b-103">Indicates the source of an assembly that is represented by [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f65b-104">構文</span><span class="sxs-lookup"><span data-stu-id="6f65b-104">Syntax</span></span>  
  
```  
typedef enum {  
    ASM_CACHE_ZAP       = 0x01,  
    ASM_CACHE_GAC       = 0x02,  
    ASM_CACHE_DOWNLOAD  = 0x04,  
    ASM_CACHE_ROOT      = 0x08  
    ASM_CACHE_ROOT_EX   = 0x80  
} ASM_CACHE_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="6f65b-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="6f65b-105">Members</span></span>  
  
|<span data-ttu-id="6f65b-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="6f65b-106">Member</span></span>|<span data-ttu-id="6f65b-107">説明</span><span class="sxs-lookup"><span data-stu-id="6f65b-107">Description</span></span>|  
|------------|-----------------|  
|`ASM_CACHE_ZAP`|<span data-ttu-id="6f65b-108">Ngen.exe を使用して、プリコンパイル済みアセンブリのキャッシュを列挙します。</span><span class="sxs-lookup"><span data-stu-id="6f65b-108">Enumerates the cache of precompiled assemblies by using Ngen.exe.</span></span>|  
|`ASM_CACHE_GAC`|<span data-ttu-id="6f65b-109">グローバル アセンブリ キャッシュを列挙します。</span><span class="sxs-lookup"><span data-stu-id="6f65b-109">Enumerates the global assembly cache.</span></span>|  
|`ASM_CACHE_DOWNLOAD`|<span data-ttu-id="6f65b-110">必要に応じてダウンロードされてまたはシャドウ コピーされているが、アセンブリを列挙します。</span><span class="sxs-lookup"><span data-stu-id="6f65b-110">Enumerates the assemblies that have been downloaded on demand or that have been shadow-copied.</span></span>|  
|`ASM_CACHE_ROOT`|<span data-ttu-id="6f65b-111">示します、 [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)関数は、共通言語ランタイム (CLR) バージョン 2.0 のグローバル アセンブリ キャッシュへのパスを返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f65b-111">Indicates that the [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) function should return the path to the global assembly cache for the common language runtime (CLR) version 2.0.</span></span> <span data-ttu-id="6f65b-112">呼び出しのコンテキストでのみ意味のある[GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)です。</span><span class="sxs-lookup"><span data-stu-id="6f65b-112">Meaningful only in the context of a call to [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span></span>|  
|`ASM_CACHE_ROOT_EX`|<span data-ttu-id="6f65b-113">示します、 [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)関数は CLR バージョン 4 のアセンブリをグローバル アセンブリ キャッシュへのパスを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f65b-113">Indicates that the [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) function should return the path to the global assembly cache for CLR version 4.</span></span> <span data-ttu-id="6f65b-114">呼び出しのコンテキストでのみ意味のある[GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)です。</span><span class="sxs-lookup"><span data-stu-id="6f65b-114">Meaningful only in the context of a call to [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6f65b-115">要件</span><span class="sxs-lookup"><span data-stu-id="6f65b-115">Requirements</span></span>  
 <span data-ttu-id="6f65b-116">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6f65b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f65b-117">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="6f65b-117">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="6f65b-118">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="6f65b-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6f65b-119">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f65b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f65b-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="6f65b-120">See Also</span></span>  
 [<span data-ttu-id="6f65b-121">GetCachePath 関数</span><span class="sxs-lookup"><span data-stu-id="6f65b-121">GetCachePath Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)  
 [<span data-ttu-id="6f65b-122">IAssemblyCacheItem インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6f65b-122">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)  
 [<span data-ttu-id="6f65b-123">Fusion 列挙型</span><span class="sxs-lookup"><span data-stu-id="6f65b-123">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
