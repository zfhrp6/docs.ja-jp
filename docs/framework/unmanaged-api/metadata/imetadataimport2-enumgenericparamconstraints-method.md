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
ms.openlocfilehash: 9afbcae016ce111456588ddbbc9f664dd7e76196
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="9a8ee-102">IMetaDataImport2::EnumGenericParamConstraints メソッド</span><span class="sxs-lookup"><span data-stu-id="9a8ee-102">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>
<span data-ttu-id="9a8ee-103">指定したトークンによって表されるジェネリック パラメーターに関連付けられているジェネリック パラメーターの制約の配列の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="9a8ee-103">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a8ee-104">構文</span><span class="sxs-lookup"><span data-stu-id="9a8ee-104">Syntax</span></span>  
  
```  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9a8ee-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9a8ee-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="9a8ee-106">[入力、出力].列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="9a8ee-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="9a8ee-107">[in]  列挙されるまでの制約は、ジェネリック パラメーターを表すトークンです。</span><span class="sxs-lookup"><span data-stu-id="9a8ee-107">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="9a8ee-108">[out]列挙するジェネリック パラメーターの制約の配列。</span><span class="sxs-lookup"><span data-stu-id="9a8ee-108">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="9a8ee-109">[in]  配置するトークンの要求の最大数`rGenericParamConstraints`です。</span><span class="sxs-lookup"><span data-stu-id="9a8ee-109">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="9a8ee-110">[out]トークンの数へのポインターに格納`rGenericParamConstraints`です。</span><span class="sxs-lookup"><span data-stu-id="9a8ee-110">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9a8ee-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="9a8ee-111">Return Value</span></span>  
  
|<span data-ttu-id="9a8ee-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9a8ee-112">HRESULT</span></span>|<span data-ttu-id="9a8ee-113">説明</span><span class="sxs-lookup"><span data-stu-id="9a8ee-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="9a8ee-114">`EnumGenericParameterConstraints`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="9a8ee-114">`EnumGenericParameterConstraints` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="9a8ee-115">`phEnum`メンバーの要素がありません。</span><span class="sxs-lookup"><span data-stu-id="9a8ee-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="9a8ee-116">この場合、`pcGenericParameterConstraints`は 0 (ゼロ) に設定します。</span><span class="sxs-lookup"><span data-stu-id="9a8ee-116">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9a8ee-117">要件</span><span class="sxs-lookup"><span data-stu-id="9a8ee-117">Requirements</span></span>  
 <span data-ttu-id="9a8ee-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9a8ee-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a8ee-119">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9a8ee-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9a8ee-120">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="9a8ee-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9a8ee-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a8ee-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a8ee-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a8ee-122">See Also</span></span>  
 [<span data-ttu-id="9a8ee-123">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a8ee-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="9a8ee-124">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a8ee-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
