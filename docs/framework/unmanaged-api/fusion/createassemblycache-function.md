---
title: "CreateAssemblyCache 関数"
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
- CreateAssemblyCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyCache
helpviewer_keywords:
- CreateAssemblyCache function [.NET Framework fusion]
ms.assetid: 348c7c8c-8578-46ae-97cf-480d6015c3c6
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5e730ea9f83a40d92cb6a865fcdd87ebf523fe7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="createassemblycache-function"></a><span data-ttu-id="a8608-102">CreateAssemblyCache 関数</span><span class="sxs-lookup"><span data-stu-id="a8608-102">CreateAssemblyCache Function</span></span>
<span data-ttu-id="a8608-103">新しいへのポインターを取得[IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)をグローバル アセンブリ キャッシュを表すインスタンス。</span><span class="sxs-lookup"><span data-stu-id="a8608-103">Gets a pointer to a new [IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8608-104">構文</span><span class="sxs-lookup"><span data-stu-id="a8608-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyCache (  
    [out] IAssemblyCache  **ppAsmCache,  
    [in]  DWORD           dwReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a8608-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a8608-105">Parameters</span></span>  
 `ppAsmCache`  
 <span data-ttu-id="a8608-106">[out]返された`IAssemblyCache`ポインター。</span><span class="sxs-lookup"><span data-stu-id="a8608-106">[out] The returned `IAssemblyCache` pointer.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="a8608-107">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="a8608-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="a8608-108">`dwReserved`0 (ゼロ) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8608-108">`dwReserved` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8608-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="a8608-109">Requirements</span></span>  
 <span data-ttu-id="a8608-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a8608-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8608-111">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="a8608-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a8608-112">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="a8608-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a8608-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8608-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8608-114">参照</span><span class="sxs-lookup"><span data-stu-id="a8608-114">See Also</span></span>  
 [<span data-ttu-id="a8608-115">IAssemblyCache インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a8608-115">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 [<span data-ttu-id="a8608-116">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="a8608-116">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
 [<span data-ttu-id="a8608-117">グローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="a8608-117">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
