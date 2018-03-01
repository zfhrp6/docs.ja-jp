---
title: "IMetaDataAssemblyImport::FindManifestResourceByName メソッド"
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
- IMetaDataAssemblyImport.FindManifestResourceByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindManifestResourceByName
helpviewer_keywords:
- FindManifestResourceByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindManifestResourceByName method [.NET Framework metadata]
ms.assetid: 7b72fa11-3866-402b-bdea-2b966b77cfe0
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2d6cc738c227157b45e242fb46a672d28d6ce778
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="0d17d-102">IMetaDataAssemblyImport::FindManifestResourceByName メソッド</span><span class="sxs-lookup"><span data-stu-id="0d17d-102">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>
<span data-ttu-id="0d17d-103">指定された名前、マニフェスト リソースへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="0d17d-103">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d17d-104">構文</span><span class="sxs-lookup"><span data-stu-id="0d17d-104">Syntax</span></span>  
  
```  
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,   
    [out] mdManifestResource     *ptkManifestResource  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="0d17d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0d17d-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="0d17d-106">[in]リソースの名前。</span><span class="sxs-lookup"><span data-stu-id="0d17d-106">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="0d17d-107">[out]配列の格納に使用される、`mdManifestResource`マニフェスト リソースを表すメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="0d17d-107">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d17d-108">コメント</span><span class="sxs-lookup"><span data-stu-id="0d17d-108">Remarks</span></span>  
 <span data-ttu-id="0d17d-109">`FindManifestResourceByName`メソッドは参照を解決するための共通言語ランタイムによって使用されている標準的な規則を使用します。</span><span class="sxs-lookup"><span data-stu-id="0d17d-109">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d17d-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="0d17d-110">Requirements</span></span>  
 <span data-ttu-id="0d17d-111">**Platform:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0d17d-111">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d17d-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0d17d-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0d17d-113">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="0d17d-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0d17d-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d17d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d17d-115">参照</span><span class="sxs-lookup"><span data-stu-id="0d17d-115">See Also</span></span>  
 [<span data-ttu-id="0d17d-116">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0d17d-116">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="0d17d-117">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="0d17d-117">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
