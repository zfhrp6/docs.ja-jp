---
title: "CreateAssemblyCache 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateAssemblyCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: DLLExport
f1_keywords: CreateAssemblyCache
helpviewer_keywords: CreateAssemblyCache function [.NET Framework fusion]
ms.assetid: 348c7c8c-8578-46ae-97cf-480d6015c3c6
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1b6dfc8cd90b5a37b82b26d4f8e494159dc1fd30
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="createassemblycache-function"></a><span data-ttu-id="0c070-102">CreateAssemblyCache 関数</span><span class="sxs-lookup"><span data-stu-id="0c070-102">CreateAssemblyCache Function</span></span>
<span data-ttu-id="0c070-103">新しいへのポインターを取得[IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)をグローバル アセンブリ キャッシュを表すインスタンス。</span><span class="sxs-lookup"><span data-stu-id="0c070-103">Gets a pointer to a new [IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c070-104">構文</span><span class="sxs-lookup"><span data-stu-id="0c070-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyCache (  
    [out] IAssemblyCache  **ppAsmCache,  
    [in]  DWORD           dwReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0c070-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0c070-105">Parameters</span></span>  
 `ppAsmCache`  
 <span data-ttu-id="0c070-106">[out]返された`IAssemblyCache`ポインター。</span><span class="sxs-lookup"><span data-stu-id="0c070-106">[out] The returned `IAssemblyCache` pointer.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="0c070-107">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="0c070-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="0c070-108">`dwReserved`0 (ゼロ) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0c070-108">`dwReserved` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c070-109">要件</span><span class="sxs-lookup"><span data-stu-id="0c070-109">Requirements</span></span>  
 <span data-ttu-id="0c070-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0c070-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c070-111">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="0c070-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="0c070-112">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="0c070-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0c070-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c070-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c070-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="0c070-114">See Also</span></span>  
 [<span data-ttu-id="0c070-115">IAssemblyCache インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0c070-115">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 [<span data-ttu-id="0c070-116">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="0c070-116">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
 [<span data-ttu-id="0c070-117">グローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="0c070-117">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
