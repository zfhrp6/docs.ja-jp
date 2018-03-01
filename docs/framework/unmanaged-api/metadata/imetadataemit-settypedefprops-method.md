---
title: "IMetaDataEmit::SetTypeDefProps メソッド"
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
- IMetaDataEmit.SetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetTypeDefProps
helpviewer_keywords:
- SetTypeDefProps method [.NET Framework metadata]
- IMetaDataEmit::SetTypeDefProps method [.NET Framework metadata]
ms.assetid: 480d596a-759f-4d29-ac1a-3dbff8f3544d
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a03b781865b55b832b34bfdab7c88ce33f4e9e12
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="6b4e4-102">IMetaDataEmit::SetTypeDefProps メソッド</span><span class="sxs-lookup"><span data-stu-id="6b4e4-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="6b4e4-103">前回の呼び出しによって定義された型の機能を設定[imetadataemit::definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="6b4e4-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b4e4-104">構文</span><span class="sxs-lookup"><span data-stu-id="6b4e4-104">Syntax</span></span>  
  
```  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[]   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6b4e4-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6b4e4-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="6b4e4-106">[in]`mdTypeDef`トークンを取得する元の呼び出しから[imetadataemit::definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="6b4e4-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="6b4e4-107">[in]`TypeDef`属性。</span><span class="sxs-lookup"><span data-stu-id="6b4e4-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="6b4e4-108">これは、ビットマスク`CorTypeAttr`値。</span><span class="sxs-lookup"><span data-stu-id="6b4e4-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="6b4e4-109">[in]`mdToken`の基本クラスです。</span><span class="sxs-lookup"><span data-stu-id="6b4e4-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="6b4e4-110">以前の呼び出しから取得した[imetadataemit::defineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)、または`null`です。</span><span class="sxs-lookup"><span data-stu-id="6b4e4-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="6b4e4-111">[in]この型が実装するインターフェイスのトークンの配列。</span><span class="sxs-lookup"><span data-stu-id="6b4e4-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="6b4e4-112">これら`mdTypeRef`を使用してトークンが取得された[imetadataemit::defineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="6b4e4-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="6b4e4-113">配列の最後の要素がある必要があります`mdTokenNil`です。</span><span class="sxs-lookup"><span data-stu-id="6b4e4-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b4e4-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="6b4e4-114">Requirements</span></span>  
 <span data-ttu-id="6b4e4-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6b4e4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b4e4-116">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6b4e4-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6b4e4-117">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="6b4e4-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b4e4-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b4e4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b4e4-119">参照</span><span class="sxs-lookup"><span data-stu-id="6b4e4-119">See Also</span></span>  
 [<span data-ttu-id="6b4e4-120">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6b4e4-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="6b4e4-121">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6b4e4-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
