---
title: "IMetaDataImport2::EnumGenericParamConstraints メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.EnumGenericParamConstraints
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::EnumGenericParamConstraints
helpviewer_keywords:
- EnumGenericParamConstraints method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParamConstraints method [.NET Framework metadata]
ms.assetid: 8a7d4e40-28fe-4e14-b801-4049880130e7
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72f863205c0fa7f4c6b4477c9d9143d1923a5d4c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="aa5fb-102">IMetaDataImport2::EnumGenericParamConstraints メソッド</span><span class="sxs-lookup"><span data-stu-id="aa5fb-102">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>
<span data-ttu-id="aa5fb-103">指定したトークンによって表されるジェネリック パラメーターに関連付けられているジェネリック パラメーターの制約の配列の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="aa5fb-103">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa5fb-104">構文</span><span class="sxs-lookup"><span data-stu-id="aa5fb-104">Syntax</span></span>  
  
```  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aa5fb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa5fb-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="aa5fb-106">[入力、出力].列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa5fb-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="aa5fb-107">[in]  列挙されるまでの制約は、ジェネリック パラメーターを表すトークンです。</span><span class="sxs-lookup"><span data-stu-id="aa5fb-107">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="aa5fb-108">[out]列挙するジェネリック パラメーターの制約の配列。</span><span class="sxs-lookup"><span data-stu-id="aa5fb-108">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="aa5fb-109">[in]  配置するトークンの要求の最大数`rGenericParamConstraints`です。</span><span class="sxs-lookup"><span data-stu-id="aa5fb-109">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="aa5fb-110">[out]トークンの数へのポインターに格納`rGenericParamConstraints`です。</span><span class="sxs-lookup"><span data-stu-id="aa5fb-110">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa5fb-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa5fb-111">Return Value</span></span>  
  
|<span data-ttu-id="aa5fb-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aa5fb-112">HRESULT</span></span>|<span data-ttu-id="aa5fb-113">説明</span><span class="sxs-lookup"><span data-stu-id="aa5fb-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="aa5fb-114">`EnumGenericParameterConstraints`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="aa5fb-114">`EnumGenericParameterConstraints` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="aa5fb-115">`phEnum`メンバーの要素がありません。</span><span class="sxs-lookup"><span data-stu-id="aa5fb-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="aa5fb-116">この場合、`pcGenericParameterConstraints`は 0 (ゼロ) に設定します。</span><span class="sxs-lookup"><span data-stu-id="aa5fb-116">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aa5fb-117">必要条件</span><span class="sxs-lookup"><span data-stu-id="aa5fb-117">Requirements</span></span>  
 <span data-ttu-id="aa5fb-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="aa5fb-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa5fb-119">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="aa5fb-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aa5fb-120">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="aa5fb-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aa5fb-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa5fb-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa5fb-122">参照</span><span class="sxs-lookup"><span data-stu-id="aa5fb-122">See Also</span></span>  
 [<span data-ttu-id="aa5fb-123">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aa5fb-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="aa5fb-124">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aa5fb-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
