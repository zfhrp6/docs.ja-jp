---
title: "IMetaDataImport2::EnumGenericParams メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.EnumGenericParams
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::EnumGenericParams
helpviewer_keywords:
- EnumGenericParams method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParams method [.NET Framework metadata]
ms.assetid: b50488a5-3cf0-483c-82dc-2892a3ec61ac
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0e6a5dc6cd1d82a3ccd46b09e301a84f90a3f429
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2enumgenericparams-method"></a><span data-ttu-id="ff779-102">IMetaDataImport2::EnumGenericParams メソッド</span><span class="sxs-lookup"><span data-stu-id="ff779-102">IMetaDataImport2::EnumGenericParams Method</span></span>
<span data-ttu-id="ff779-103">トークンのジェネリック パラメーターのトークンが、指定した TypeDef または MethodDef に関連付けられている配列の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="ff779-103">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff779-104">構文</span><span class="sxs-lookup"><span data-stu-id="ff779-104">Syntax</span></span>  
  
```  
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,   
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],   
   [in]  ULONG            cMax,   
   [out] ULONG            *pcGenericParams  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff779-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff779-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="ff779-106">[入力、出力].列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ff779-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="ff779-107">[in]ジェネリック パラメーターがある列挙される TypeDef または MethodDef トークンです。</span><span class="sxs-lookup"><span data-stu-id="ff779-107">[in] The TypeDef or MethodDef token whose generic parameters are to be enumerated.</span></span>  
  
 `rGenericParams`  
 <span data-ttu-id="ff779-108">[out]列挙するジェネリック パラメーターの配列。</span><span class="sxs-lookup"><span data-stu-id="ff779-108">[out] The array of generic parameters to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="ff779-109">[in]配置するトークンの要求の最大数`rGenericParams`です。</span><span class="sxs-lookup"><span data-stu-id="ff779-109">[in] The requested maximum number of tokens to place in `rGenericParams`.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="ff779-110">[out]返されたトークンの数が内に配置`rGenericParams`です。</span><span class="sxs-lookup"><span data-stu-id="ff779-110">[out] The returned number of tokens placed in `rGenericParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ff779-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff779-111">Return Value</span></span>  
  
|<span data-ttu-id="ff779-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ff779-112">HRESULT</span></span>|<span data-ttu-id="ff779-113">説明</span><span class="sxs-lookup"><span data-stu-id="ff779-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="ff779-114">`EnumGenericParams`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="ff779-114">`EnumGenericParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="ff779-115">`phEnum`メンバーの要素がありません。</span><span class="sxs-lookup"><span data-stu-id="ff779-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="ff779-116">この場合、`pcGenericParams`は 0 (ゼロ) に設定します。</span><span class="sxs-lookup"><span data-stu-id="ff779-116">In this case, `pcGenericParams` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ff779-117">要件</span><span class="sxs-lookup"><span data-stu-id="ff779-117">Requirements</span></span>  
 <span data-ttu-id="ff779-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ff779-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff779-119">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ff779-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ff779-120">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="ff779-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ff779-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff779-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff779-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="ff779-122">See Also</span></span>  
 [<span data-ttu-id="ff779-123">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ff779-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="ff779-124">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ff779-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
