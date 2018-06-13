---
title: IMetaDataAssemblyImport::FindManifestResourceByName メソッド
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9afc2ecc34131f62f1f8e8e86ca73f8b8b0126b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443513"
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="dad56-102">IMetaDataAssemblyImport::FindManifestResourceByName メソッド</span><span class="sxs-lookup"><span data-stu-id="dad56-102">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>
<span data-ttu-id="dad56-103">指定された名前、マニフェスト リソースへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="dad56-103">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dad56-104">構文</span><span class="sxs-lookup"><span data-stu-id="dad56-104">Syntax</span></span>  
  
```  
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,   
    [out] mdManifestResource     *ptkManifestResource  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="dad56-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dad56-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="dad56-106">[in]リソースの名前。</span><span class="sxs-lookup"><span data-stu-id="dad56-106">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="dad56-107">[out]配列の格納に使用される、`mdManifestResource`マニフェスト リソースを表すメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="dad56-107">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dad56-108">コメント</span><span class="sxs-lookup"><span data-stu-id="dad56-108">Remarks</span></span>  
 <span data-ttu-id="dad56-109">`FindManifestResourceByName`メソッドは参照を解決するための共通言語ランタイムによって使用されている標準的な規則を使用します。</span><span class="sxs-lookup"><span data-stu-id="dad56-109">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dad56-110">要件</span><span class="sxs-lookup"><span data-stu-id="dad56-110">Requirements</span></span>  
 <span data-ttu-id="dad56-111">**Platform:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="dad56-111">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dad56-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dad56-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dad56-113">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="dad56-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dad56-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dad56-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dad56-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="dad56-115">See Also</span></span>  
 [<span data-ttu-id="dad56-116">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dad56-116">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="dad56-117">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="dad56-117">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
