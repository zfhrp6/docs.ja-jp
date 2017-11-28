---
title: "ASM_CACHE_FLAGS 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ASM_CACHE_FLAGS
api_location: fusion.dll
api_type: COM
f1_keywords: ASM_CACHE_FLAGS
helpviewer_keywords: ASM_CACHE_FLAGS enumeration [.NET Framework fusion]
ms.assetid: 82e9a7da-321b-48b8-b239-52eaffda6be8
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 767cae15c37b8c62d47085533ea9fa3ce4957963
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="asmcacheflags-enumeration"></a><span data-ttu-id="a6e81-102">ASM_CACHE_FLAGS 列挙型</span><span class="sxs-lookup"><span data-stu-id="a6e81-102">ASM_CACHE_FLAGS Enumeration</span></span>
<span data-ttu-id="a6e81-103">によって表されるアセンブリのソースを示す[IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)グローバル アセンブリ キャッシュにします。</span><span class="sxs-lookup"><span data-stu-id="a6e81-103">Indicates the source of an assembly that is represented by [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6e81-104">構文</span><span class="sxs-lookup"><span data-stu-id="a6e81-104">Syntax</span></span>  
  
```  
typedef enum {  
    ASM_CACHE_ZAP       = 0x01,  
    ASM_CACHE_GAC       = 0x02,  
    ASM_CACHE_DOWNLOAD  = 0x04,  
    ASM_CACHE_ROOT      = 0x08  
    ASM_CACHE_ROOT_EX   = 0x80  
} ASM_CACHE_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="a6e81-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="a6e81-105">Members</span></span>  
  
|<span data-ttu-id="a6e81-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="a6e81-106">Member</span></span>|<span data-ttu-id="a6e81-107">説明</span><span class="sxs-lookup"><span data-stu-id="a6e81-107">Description</span></span>|  
|------------|-----------------|  
|`ASM_CACHE_ZAP`|<span data-ttu-id="a6e81-108">Ngen.exe を使用して、プリコンパイル済みアセンブリのキャッシュを列挙します。</span><span class="sxs-lookup"><span data-stu-id="a6e81-108">Enumerates the cache of precompiled assemblies by using Ngen.exe.</span></span>|  
|`ASM_CACHE_GAC`|<span data-ttu-id="a6e81-109">グローバル アセンブリ キャッシュを列挙します。</span><span class="sxs-lookup"><span data-stu-id="a6e81-109">Enumerates the global assembly cache.</span></span>|  
|`ASM_CACHE_DOWNLOAD`|<span data-ttu-id="a6e81-110">必要に応じてダウンロードされてまたはシャドウ コピーされているが、アセンブリを列挙します。</span><span class="sxs-lookup"><span data-stu-id="a6e81-110">Enumerates the assemblies that have been downloaded on demand or that have been shadow-copied.</span></span>|  
|`ASM_CACHE_ROOT`|<span data-ttu-id="a6e81-111">示します、 [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)関数は、共通言語ランタイム (CLR) バージョン 2.0 のグローバル アセンブリ キャッシュへのパスを返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6e81-111">Indicates that the [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) function should return the path to the global assembly cache for the common language runtime (CLR) version 2.0.</span></span> <span data-ttu-id="a6e81-112">呼び出しのコンテキストでのみ意味のある[GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)です。</span><span class="sxs-lookup"><span data-stu-id="a6e81-112">Meaningful only in the context of a call to [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span></span>|  
|`ASM_CACHE_ROOT_EX`|<span data-ttu-id="a6e81-113">示します、 [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)関数は CLR バージョン 4 のアセンブリをグローバル アセンブリ キャッシュへのパスを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6e81-113">Indicates that the [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) function should return the path to the global assembly cache for CLR version 4.</span></span> <span data-ttu-id="a6e81-114">呼び出しのコンテキストでのみ意味のある[GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)です。</span><span class="sxs-lookup"><span data-stu-id="a6e81-114">Meaningful only in the context of a call to [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a6e81-115">要件</span><span class="sxs-lookup"><span data-stu-id="a6e81-115">Requirements</span></span>  
 <span data-ttu-id="a6e81-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a6e81-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6e81-117">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="a6e81-117">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a6e81-118">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="a6e81-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a6e81-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6e81-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6e81-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="a6e81-120">See Also</span></span>  
 [<span data-ttu-id="a6e81-121">GetCachePath 関数</span><span class="sxs-lookup"><span data-stu-id="a6e81-121">GetCachePath Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)  
 [<span data-ttu-id="a6e81-122">IAssemblyCacheItem インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6e81-122">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)  
 [<span data-ttu-id="a6e81-123">Fusion 列挙体</span><span class="sxs-lookup"><span data-stu-id="a6e81-123">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
