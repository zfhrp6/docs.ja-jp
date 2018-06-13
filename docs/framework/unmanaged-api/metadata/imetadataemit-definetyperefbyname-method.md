---
title: IMetaDataEmit::DefineTypeRefByName メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeRefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeRefByName
helpviewer_keywords:
- DefineTypeRefByName method [.NET Framework metadata]
- IMetaDataEmit::DefineTypeRefByName method [.NET Framework metadata]
ms.assetid: c30a4ce3-2d3e-411a-98df-e62ac4a5dd50
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4fd6102b65137a06009428c1245b80c0d44924a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445492"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="15d99-102">IMetaDataEmit::DefineTypeRefByName メソッド</span><span class="sxs-lookup"><span data-stu-id="15d99-102">IMetaDataEmit::DefineTypeRefByName Method</span></span>
<span data-ttu-id="15d99-103">現在のスコープ外には、指定されたスコープで定義されている型のメタデータ トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="15d99-103">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15d99-104">構文</span><span class="sxs-lookup"><span data-stu-id="15d99-104">Syntax</span></span>  
  
```  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="15d99-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="15d99-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="15d99-106">[in]解決スコープを指定するトークンです。</span><span class="sxs-lookup"><span data-stu-id="15d99-106">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="15d99-107">次のトークンの種類は有効です。</span><span class="sxs-lookup"><span data-stu-id="15d99-107">The following token types are valid:</span></span>  
  
-   <span data-ttu-id="15d99-108">`mdModuleRef`、型が呼び出し元が定義されている同じアセンブリに定義されている場合。</span><span class="sxs-lookup"><span data-stu-id="15d99-108">`mdModuleRef`, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="15d99-109">`mdAssemblyRef`、型が呼び出し元が定義されている以外のアセンブリで定義されている場合。</span><span class="sxs-lookup"><span data-stu-id="15d99-109">`mdAssemblyRef`, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="15d99-110">`mdTypeRef`、型が入れ子にされた型である場合。</span><span class="sxs-lookup"><span data-stu-id="15d99-110">`mdTypeRef`, if the type is a nested type.</span></span>  
  
-   <span data-ttu-id="15d99-111">`mdModule`、型が呼び出し元が定義されている同じモジュールで定義されている場合。</span><span class="sxs-lookup"><span data-stu-id="15d99-111">`mdModule`, if the type is defined in the same module in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="15d99-112">型がグローバルに定義されている場合は null です。</span><span class="sxs-lookup"><span data-stu-id="15d99-112">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="15d99-113">[in]Unicode で対象の型の名前です。</span><span class="sxs-lookup"><span data-stu-id="15d99-113">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="15d99-114">[out]ポインター、`mdTypeRef`型に割り当てられているトークンです。</span><span class="sxs-lookup"><span data-stu-id="15d99-114">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15d99-115">要件</span><span class="sxs-lookup"><span data-stu-id="15d99-115">Requirements</span></span>  
 <span data-ttu-id="15d99-116">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="15d99-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15d99-117">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="15d99-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="15d99-118">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="15d99-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="15d99-119">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15d99-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15d99-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="15d99-120">See Also</span></span>  
 [<span data-ttu-id="15d99-121">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="15d99-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="15d99-122">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="15d99-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
