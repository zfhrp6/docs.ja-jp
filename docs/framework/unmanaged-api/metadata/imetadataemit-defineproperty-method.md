---
title: IMetaDataEmit::DefineProperty メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineProperty
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineProperty
helpviewer_keywords:
- IMetaDataEmit::DefineProperty method [.NET Framework metadata]
- DefineProperty method [.NET Framework metadata]
ms.assetid: 5c4c1dc2-d40d-4173-bbe6-7058fb21c98f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5c250a577f2ccdbbfefb35225b880c0e4317db36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitdefineproperty-method"></a><span data-ttu-id="64184-102">IMetaDataEmit::DefineProperty メソッド</span><span class="sxs-lookup"><span data-stu-id="64184-102">IMetaDataEmit::DefineProperty Method</span></span>
<span data-ttu-id="64184-103">指定した、指定した型のプロパティ定義を作成`get`と`set`メソッド アクセサーし、そのプロパティ定義トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="64184-103">Creates a property definition for the specified type, with the specified `get` and `set` method accessors, and gets a token to that property definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64184-104">構文</span><span class="sxs-lookup"><span data-stu-id="64184-104">Syntax</span></span>  
  
```  
HRESULT DefineProperty (   
    [in]  mdTypeDef          td,   
    [in]  LPCWSTR            szProperty,   
    [in]  DWORD              dwPropFlags,   
    [in]  PCCOR_SIGNATURE    pvSig,   
    [in]  ULONG              cbSig,   
    [in]  DWORD              dwCPlusTypeFlag,   
    [in]  void const         *pValue,   
    [in]  ULONG              cchValue,   
    [in]  mdMethodDef        mdSetter,   
    [in]  mdMethodDef        mdGetter,   
    [in]  mdMethodDef        rmdOtherMethods[],   
    [out] mdProperty         *pmdProp   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="64184-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="64184-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="64184-106">[in]クラスまたはインターフェイスのプロパティを定義するトークンです。</span><span class="sxs-lookup"><span data-stu-id="64184-106">[in] The token for class or interface on which the property is being defined.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="64184-107">[in]プロパティの名前です。</span><span class="sxs-lookup"><span data-stu-id="64184-107">[in] The name of the property.</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="64184-108">[in]プロパティのフラグです。</span><span class="sxs-lookup"><span data-stu-id="64184-108">[in] The property flags.</span></span>  
  
 `pvSig`  
 <span data-ttu-id="64184-109">[in]プロパティの署名。</span><span class="sxs-lookup"><span data-stu-id="64184-109">[in] The property signature.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="64184-110">[in]内のバイト数`pvSig`です。</span><span class="sxs-lookup"><span data-stu-id="64184-110">[in] The count of bytes in `pvSig`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="64184-111">[in]プロパティの既定値の型。</span><span class="sxs-lookup"><span data-stu-id="64184-111">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="64184-112">[in]プロパティの既定値。</span><span class="sxs-lookup"><span data-stu-id="64184-112">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="64184-113">[in] \(Unicode) の数の文字について`pValue`です。</span><span class="sxs-lookup"><span data-stu-id="64184-113">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="64184-114">[in]プロパティの値を設定するメソッド。</span><span class="sxs-lookup"><span data-stu-id="64184-114">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="64184-115">[in]このメソッドは、プロパティ値を取得します。</span><span class="sxs-lookup"><span data-stu-id="64184-115">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="64184-116">[in]プロパティに関連付けられている他のメソッドの配列。</span><span class="sxs-lookup"><span data-stu-id="64184-116">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="64184-117">配列を終了、`mdTokenNil`です。</span><span class="sxs-lookup"><span data-stu-id="64184-117">Terminate the array with an `mdTokenNil`.</span></span>  
  
 `pmdProp`  
 <span data-ttu-id="64184-118">[out]`mdProperty`トークンが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="64184-118">[out] The `mdProperty` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64184-119">要件</span><span class="sxs-lookup"><span data-stu-id="64184-119">Requirements</span></span>  
 <span data-ttu-id="64184-120">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="64184-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64184-121">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="64184-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="64184-122">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="64184-122">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="64184-123">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64184-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64184-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="64184-124">See Also</span></span>  
 [<span data-ttu-id="64184-125">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="64184-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="64184-126">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="64184-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
