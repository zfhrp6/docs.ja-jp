---
title: IMetaDataAssemblyEmit::SetManifestResourceProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetManifestResourceProps
helpviewer_keywords:
- SetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetManifestResourceProps method [.NET Framework metadata]
ms.assetid: ef77efd1-849c-4e51-ba92-7ee3d2bf0339
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 755c64aa00b82bf2d8213217787f4dc1916c0898
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a><span data-ttu-id="00520-102">IMetaDataAssemblyEmit::SetManifestResourceProps メソッド</span><span class="sxs-lookup"><span data-stu-id="00520-102">IMetaDataAssemblyEmit::SetManifestResourceProps Method</span></span>
<span data-ttu-id="00520-103">指定された `ManifestResource` メタデータ構造体を変更します。</span><span class="sxs-lookup"><span data-stu-id="00520-103">Modifies the specified `ManifestResource` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00520-104">構文</span><span class="sxs-lookup"><span data-stu-id="00520-104">Syntax</span></span>  
  
```  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,   
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="00520-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="00520-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="00520-106">[in]トークンを指定する、`ManifestResource`メタデータ構造体を変更できます。</span><span class="sxs-lookup"><span data-stu-id="00520-106">[in] The token that specifies the `ManifestResource` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="00520-107">[in]型のトークン、`File`または`AssemblyRef`、リソース プロバイダーにマップします。</span><span class="sxs-lookup"><span data-stu-id="00520-107">[in] The token, of type `File` or `AssemblyRef`, that maps to the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="00520-108">[in]ファイル内のリソースの先頭までのオフセット。</span><span class="sxs-lookup"><span data-stu-id="00520-108">[in] The offset to the beginning of the resource within the file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="00520-109">[in]リソースの属性を指定するフラグ値のビットごとの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="00520-109">[in] A bitwise combination of flag values that specify the attributes of the resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00520-110">コメント</span><span class="sxs-lookup"><span data-stu-id="00520-110">Remarks</span></span>  
 <span data-ttu-id="00520-111">作成する、`ManifestResource`メタデータ構造体を使用して、 [imetadataassemblyemit::definemanifestresource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="00520-111">To create a `ManifestResource` metadata structure, use the [IMetaDataAssemblyEmit::DefineManifestResource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00520-112">要件</span><span class="sxs-lookup"><span data-stu-id="00520-112">Requirements</span></span>  
 <span data-ttu-id="00520-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="00520-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00520-114">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="00520-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="00520-115">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="00520-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="00520-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00520-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00520-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="00520-117">See Also</span></span>  
 [<span data-ttu-id="00520-118">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="00520-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
