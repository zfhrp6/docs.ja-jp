---
title: IMetaDataEmit::SetTypeDefProps メソッド
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b72088e4aa9994ca6ae411ec36d4c578e3017e5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447884"
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="31ee6-102">IMetaDataEmit::SetTypeDefProps メソッド</span><span class="sxs-lookup"><span data-stu-id="31ee6-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="31ee6-103">前回の呼び出しによって定義された型の機能を設定[imetadataemit::definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="31ee6-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31ee6-104">構文</span><span class="sxs-lookup"><span data-stu-id="31ee6-104">Syntax</span></span>  
  
```  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[]   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31ee6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="31ee6-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="31ee6-106">[in]`mdTypeDef`トークンを取得する元の呼び出しから[imetadataemit::definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="31ee6-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="31ee6-107">[in]`TypeDef`属性。</span><span class="sxs-lookup"><span data-stu-id="31ee6-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="31ee6-108">これは、ビットマスク`CorTypeAttr`値。</span><span class="sxs-lookup"><span data-stu-id="31ee6-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="31ee6-109">[in]`mdToken`の基本クラスです。</span><span class="sxs-lookup"><span data-stu-id="31ee6-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="31ee6-110">以前の呼び出しから取得した[imetadataemit::defineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)、または`null`です。</span><span class="sxs-lookup"><span data-stu-id="31ee6-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="31ee6-111">[in]この型が実装するインターフェイスのトークンの配列。</span><span class="sxs-lookup"><span data-stu-id="31ee6-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="31ee6-112">これら`mdTypeRef`を使用してトークンが取得された[imetadataemit::defineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="31ee6-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="31ee6-113">配列の最後の要素がある必要があります`mdTokenNil`です。</span><span class="sxs-lookup"><span data-stu-id="31ee6-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31ee6-114">要件</span><span class="sxs-lookup"><span data-stu-id="31ee6-114">Requirements</span></span>  
 <span data-ttu-id="31ee6-115">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="31ee6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31ee6-116">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="31ee6-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="31ee6-117">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="31ee6-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31ee6-118">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31ee6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31ee6-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="31ee6-119">See Also</span></span>  
 [<span data-ttu-id="31ee6-120">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="31ee6-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="31ee6-121">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="31ee6-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
