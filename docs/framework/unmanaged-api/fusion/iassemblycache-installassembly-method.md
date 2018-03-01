---
title: "IAssemblyCache::InstallAssembly メソッド"
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
- IAssemblyCache.InstallAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::InstallAssembly
helpviewer_keywords:
- InstallAssembly method [.NET Framework fusion]
- IAssemblyCache::InstallAssembly method [.NET Framework fusion]
ms.assetid: 33c1d269-c85e-4cb1-b0e6-1c510c8fb5fa
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e269d96b28c43918d9913e899db5928c5c73ca96
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblycacheinstallassembly-method"></a><span data-ttu-id="48402-102">IAssemblyCache::InstallAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="48402-102">IAssemblyCache::InstallAssembly Method</span></span>
<span data-ttu-id="48402-103">指定したアセンブリをグローバル アセンブリ キャッシュにインストールします。</span><span class="sxs-lookup"><span data-stu-id="48402-103">Installs the specified assembly in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48402-104">構文</span><span class="sxs-lookup"><span data-stu-id="48402-104">Syntax</span></span>  
  
```  
HRESULT InstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszManifestFilePath,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="48402-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="48402-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="48402-106">[in]ものがありますで定義されているフラグです。</span><span class="sxs-lookup"><span data-stu-id="48402-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="48402-107">次の値がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="48402-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="48402-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0X00000001)</span><span class="sxs-lookup"><span data-stu-id="48402-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
-   <span data-ttu-id="48402-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0X00000002)</span><span class="sxs-lookup"><span data-stu-id="48402-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pszManifestFilePath`  
 <span data-ttu-id="48402-110">[in]インストールするアセンブリのマニフェストへのパス。</span><span class="sxs-lookup"><span data-stu-id="48402-110">[in] The path to the manifest for the assembly to install.</span></span>  
  
 `pRefData`  
 <span data-ttu-id="48402-111">[in]A [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md)をインストールするためのデータを格納する構造体。</span><span class="sxs-lookup"><span data-stu-id="48402-111">[in] A [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure that contains data for the installation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48402-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="48402-112">Requirements</span></span>  
 <span data-ttu-id="48402-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="48402-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48402-114">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="48402-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="48402-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48402-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48402-116">参照</span><span class="sxs-lookup"><span data-stu-id="48402-116">See Also</span></span>  
 [<span data-ttu-id="48402-117">IAssemblyCache インターフェイス</span><span class="sxs-lookup"><span data-stu-id="48402-117">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
