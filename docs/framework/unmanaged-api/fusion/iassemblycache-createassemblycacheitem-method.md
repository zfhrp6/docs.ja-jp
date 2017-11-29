---
title: "IAssemblyCache::CreateAssemblyCacheItem メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyCache.CreateAssemblyCacheItem
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyCache::CreateAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCache::CreateAssemblyCacheItem method [.NET Framework fusion]
- CreateAssemblyCacheItem method [.NET Framework fusion]
ms.assetid: 017a7ba5-aaaf-44e2-9cbe-ceebef259df0
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 84291d3dea34aba43889baeb1f6e3d501f71b782
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iassemblycachecreateassemblycacheitem-method"></a><span data-ttu-id="f4358-102">IAssemblyCache::CreateAssemblyCacheItem メソッド</span><span class="sxs-lookup"><span data-stu-id="f4358-102">IAssemblyCache::CreateAssemblyCacheItem Method</span></span>
<span data-ttu-id="f4358-103">新しいへの参照を取得[IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f4358-103">Gets a reference to a new [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4358-104">構文</span><span class="sxs-lookup"><span data-stu-id="f4358-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyCacheItem (  
    [in]  DWORD dwFlags,  
    [in]  PVOID pvReserved,  
    [out] IAssemblyCacheItem **ppAsmItem,  
    [in, optional] LPCWSTR pszAssemblyName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f4358-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f4358-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="f4358-106">[in]ものがありますで定義されているフラグです。</span><span class="sxs-lookup"><span data-stu-id="f4358-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="f4358-107">次の値がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="f4358-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="f4358-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0X00000001)</span><span class="sxs-lookup"><span data-stu-id="f4358-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
-   <span data-ttu-id="f4358-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0X00000002)</span><span class="sxs-lookup"><span data-stu-id="f4358-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="f4358-110">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="f4358-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="f4358-111">`pvReserved`null 参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4358-111">`pvReserved` must be a null reference.</span></span>  
  
 `ppAsmItem`  
 <span data-ttu-id="f4358-112">[out]返された`IAssemblyCacheItem`ポインター。</span><span class="sxs-lookup"><span data-stu-id="f4358-112">[out] The returned `IAssemblyCacheItem` pointer.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="f4358-113">[in、省略可能]Uncanonicalized、コンマで区切られた`name=value`ペア。</span><span class="sxs-lookup"><span data-stu-id="f4358-113">[in, optional] Uncanonicalized, comma-separated `name=value` pairs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4358-114">要件</span><span class="sxs-lookup"><span data-stu-id="f4358-114">Requirements</span></span>  
 <span data-ttu-id="f4358-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f4358-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4358-116">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="f4358-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f4358-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4358-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4358-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="f4358-118">See Also</span></span>  
 [<span data-ttu-id="f4358-119">IAssemblyCache インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f4358-119">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 [<span data-ttu-id="f4358-120">IAssemblyCacheItem インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f4358-120">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
