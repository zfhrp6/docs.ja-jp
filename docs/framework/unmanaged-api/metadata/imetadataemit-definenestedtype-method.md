---
title: "IMetaDataEmit::DefineNestedType メソッド"
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
- IMetaDataEmit.DefineNestedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineNestedType
helpviewer_keywords:
- IMetaDataEmit::DefineNestedType method [.NET Framework metadata]
- DefineNestedType method [.NET Framework metadata]
ms.assetid: 1e994de6-4628-459c-b967-b34be1e9fe4f
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 99250d98f9ffd90857128aa5d8a675a997926bf5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinenestedtype-method"></a><span data-ttu-id="5c701-102">IMetaDataEmit::DefineNestedType メソッド</span><span class="sxs-lookup"><span data-stu-id="5c701-102">IMetaDataEmit::DefineNestedType Method</span></span>
<span data-ttu-id="5c701-103">型定義のメタデータ署名を作成しを返します、 `mdTypeDef` 、その種類のトークンし、定義済みの型によって参照される型のメンバーであることを指定します、`tdEncloser`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="5c701-103">Creates the metadata signature of a type definition, returns an `mdTypeDef` token for that type, and specifies that the defined type is a member of the type referenced by the `tdEncloser` parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c701-104">構文</span><span class="sxs-lookup"><span data-stu-id="5c701-104">Syntax</span></span>  
  
```  
HRESULT DefineNestedType (   
    [in]  LPCWSTR     szTypeDef,  
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [in]  mdTypeDef   tdEncloser,   
    [out] mdTypeDef   *ptd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5c701-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5c701-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="5c701-106">[in]Unicode での型の名前です。</span><span class="sxs-lookup"><span data-stu-id="5c701-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="5c701-107">[in]`TypeDef`属性。</span><span class="sxs-lookup"><span data-stu-id="5c701-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="5c701-108">これは、ビットマスク`CorTypeAttr`値。</span><span class="sxs-lookup"><span data-stu-id="5c701-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="5c701-109">[in]基本クラスのトークンです。</span><span class="sxs-lookup"><span data-stu-id="5c701-109">[in] The token of the base class.</span></span> <span data-ttu-id="5c701-110">これは、いずれか、`mdTypeDef`または`mdTypeRef`トークンです。</span><span class="sxs-lookup"><span data-stu-id="5c701-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 <span data-ttu-id="5c701-111">`rtkImplements`[]</span><span class="sxs-lookup"><span data-stu-id="5c701-111">`rtkImplements`[]</span></span>  
 <span data-ttu-id="5c701-112">[in]このクラスまたはインターフェイスを実装するインターフェイスを指定するトークンの配列。</span><span class="sxs-lookup"><span data-stu-id="5c701-112">[in] An array of tokens that specify the interfaces that this class or interface implements.</span></span>  
  
 `tdEncloser`  
 <span data-ttu-id="5c701-113">[in]外側の型のトークンです。</span><span class="sxs-lookup"><span data-stu-id="5c701-113">[in] The token of the enclosing type.</span></span> <span data-ttu-id="5c701-114">配列の最後の要素である必要があります`mdTokenNil`です。</span><span class="sxs-lookup"><span data-stu-id="5c701-114">The last element of the array must be `mdTokenNil`.</span></span>  
  
 `ptd`  
 <span data-ttu-id="5c701-115">[out]`mdTypeDef`トークンが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="5c701-115">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c701-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="5c701-116">Requirements</span></span>  
 <span data-ttu-id="5c701-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5c701-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c701-118">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5c701-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5c701-119">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="5c701-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c701-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c701-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c701-121">参照</span><span class="sxs-lookup"><span data-stu-id="5c701-121">See Also</span></span>  
 [<span data-ttu-id="5c701-122">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5c701-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="5c701-123">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5c701-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
