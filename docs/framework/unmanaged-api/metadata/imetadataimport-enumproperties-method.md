---
title: IMetaDataImport::EnumProperties メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumProperties
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumProperties
helpviewer_keywords:
- IMetaDataImport::EnumProperties method [.NET Framework metadata]
- EnumProperties method [.NET Framework metadata]
ms.assetid: 60573ad7-8821-4721-a068-3f7a6d25926a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ad29204e445bc61b6dc9753d594f0e4bf62930fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448574"
---
# <a name="imetadataimportenumproperties-method"></a><span data-ttu-id="82778-102">IMetaDataImport::EnumProperties メソッド</span><span class="sxs-lookup"><span data-stu-id="82778-102">IMetaDataImport::EnumProperties Method</span></span>
<span data-ttu-id="82778-103">指定した TypeDef トークンによって参照される型のプロパティを表す PropertyDef トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="82778-103">Enumerates PropertyDef tokens representing the properties of the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82778-104">構文</span><span class="sxs-lookup"><span data-stu-id="82778-104">Syntax</span></span>  
  
```  
HRESULT EnumProperties (  
   [in, out] HCORENUM    *phEnum,  
   [in]      mdTypeDef   td,  
   [out]     mdProperty  rProperties[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcProperties  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="82778-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="82778-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="82778-106">[入力、出力].列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="82778-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="82778-107">このメソッドの最初の呼び出しで NULL があります。</span><span class="sxs-lookup"><span data-stu-id="82778-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="82778-108">[in]列挙するプロパティを持つ型を表す TypeDef トークンです。</span><span class="sxs-lookup"><span data-stu-id="82778-108">[in] A TypeDef token representing the type with properties to enumerate.</span></span>  
  
 `rProperties`  
 <span data-ttu-id="82778-109">[out]PropertyDef トークンを格納する配列。</span><span class="sxs-lookup"><span data-stu-id="82778-109">[out] The array used to store the PropertyDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="82778-110">[in] `rProperties` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="82778-110">[in] The maximum size of the `rProperties` array.</span></span>  
  
 `pcProperties`  
 <span data-ttu-id="82778-111">[out]返される PropertyDef トークン数`rProperties`です。</span><span class="sxs-lookup"><span data-stu-id="82778-111">[out] The number of PropertyDef tokens returned in `rProperties`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82778-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="82778-112">Return Value</span></span>  
  
|<span data-ttu-id="82778-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="82778-113">HRESULT</span></span>|<span data-ttu-id="82778-114">説明</span><span class="sxs-lookup"><span data-stu-id="82778-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="82778-115">`EnumProperties` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="82778-115">`EnumProperties` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="82778-116">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="82778-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="82778-117">その場合は、`pcProperties`ゼロです。</span><span class="sxs-lookup"><span data-stu-id="82778-117">In that case, `pcProperties` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="82778-118">要件</span><span class="sxs-lookup"><span data-stu-id="82778-118">Requirements</span></span>  
 <span data-ttu-id="82778-119">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="82778-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82778-120">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="82778-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="82778-121">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="82778-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="82778-122">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82778-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82778-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="82778-123">See Also</span></span>  
 [<span data-ttu-id="82778-124">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="82778-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="82778-125">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="82778-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
