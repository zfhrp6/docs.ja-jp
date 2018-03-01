---
title: "IMetaDataImport::EnumProperties メソッド"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 63ff10904440f55ec3fe6fb6aa581fbf560763e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumproperties-method"></a><span data-ttu-id="aedf9-102">IMetaDataImport::EnumProperties メソッド</span><span class="sxs-lookup"><span data-stu-id="aedf9-102">IMetaDataImport::EnumProperties Method</span></span>
<span data-ttu-id="aedf9-103">指定した TypeDef トークンによって参照される型のプロパティを表す PropertyDef トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="aedf9-103">Enumerates PropertyDef tokens representing the properties of the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aedf9-104">構文</span><span class="sxs-lookup"><span data-stu-id="aedf9-104">Syntax</span></span>  
  
```  
HRESULT EnumProperties (  
   [in, out] HCORENUM    *phEnum,  
   [in]      mdTypeDef   td,  
   [out]     mdProperty  rProperties[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcProperties  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aedf9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aedf9-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="aedf9-106">[入力、出力].列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aedf9-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="aedf9-107">このメソッドの最初の呼び出しで NULL があります。</span><span class="sxs-lookup"><span data-stu-id="aedf9-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="aedf9-108">[in]列挙するプロパティを持つ型を表す TypeDef トークンです。</span><span class="sxs-lookup"><span data-stu-id="aedf9-108">[in] A TypeDef token representing the type with properties to enumerate.</span></span>  
  
 `rProperties`  
 <span data-ttu-id="aedf9-109">[out]PropertyDef トークンを格納する配列。</span><span class="sxs-lookup"><span data-stu-id="aedf9-109">[out] The array used to store the PropertyDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="aedf9-110">[in] `rProperties` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="aedf9-110">[in] The maximum size of the `rProperties` array.</span></span>  
  
 `pcProperties`  
 <span data-ttu-id="aedf9-111">[out]返される PropertyDef トークン数`rProperties`です。</span><span class="sxs-lookup"><span data-stu-id="aedf9-111">[out] The number of PropertyDef tokens returned in `rProperties`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aedf9-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="aedf9-112">Return Value</span></span>  
  
|<span data-ttu-id="aedf9-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aedf9-113">HRESULT</span></span>|<span data-ttu-id="aedf9-114">説明</span><span class="sxs-lookup"><span data-stu-id="aedf9-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="aedf9-115">`EnumProperties`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="aedf9-115">`EnumProperties` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="aedf9-116">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="aedf9-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="aedf9-117">その場合は、`pcProperties`ゼロです。</span><span class="sxs-lookup"><span data-stu-id="aedf9-117">In that case, `pcProperties` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aedf9-118">必要条件</span><span class="sxs-lookup"><span data-stu-id="aedf9-118">Requirements</span></span>  
 <span data-ttu-id="aedf9-119">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="aedf9-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aedf9-120">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="aedf9-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aedf9-121">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="aedf9-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aedf9-122">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aedf9-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aedf9-123">参照</span><span class="sxs-lookup"><span data-stu-id="aedf9-123">See Also</span></span>  
 [<span data-ttu-id="aedf9-124">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aedf9-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="aedf9-125">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aedf9-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
