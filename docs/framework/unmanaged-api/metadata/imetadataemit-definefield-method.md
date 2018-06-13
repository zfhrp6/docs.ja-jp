---
title: IMetaDataEmit::DefineField メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fd0ddda898911da2c96a53d941c4290af9028154
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446575"
---
# <a name="imetadataemitdefinefield-method"></a><span data-ttu-id="facdc-102">IMetaDataEmit::DefineField メソッド</span><span class="sxs-lookup"><span data-stu-id="facdc-102">IMetaDataEmit::DefineField Method</span></span>
<span data-ttu-id="facdc-103">指定したメタデータ シグネチャを持つフィールドの定義を作成し、そのフィールド定義トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="facdc-103">Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="facdc-104">構文</span><span class="sxs-lookup"><span data-stu-id="facdc-104">Syntax</span></span>  
  
```  
HRESULT DefineField (   
    [in]  mdTypeDef   td,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwFieldFlags,   
    [in]  PCCOR_SIGNATURE pvSigBlob,   
    [in]  ULONG       cbSigBlob,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue,   
    [out] mdFieldDef  *pmd   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="facdc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="facdc-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="facdc-106">[in]`mdTypeDef`外側のクラスまたはインターフェイスのトークン。</span><span class="sxs-lookup"><span data-stu-id="facdc-106">[in] The `mdTypeDef` token for the enclosing class or interface.</span></span>  
  
 `szName`  
 <span data-ttu-id="facdc-107">[in]Unicode でフィールド名です。</span><span class="sxs-lookup"><span data-stu-id="facdc-107">[in] The field name in Unicode.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="facdc-108">[in]フィールドの属性。</span><span class="sxs-lookup"><span data-stu-id="facdc-108">[in] The field attributes.</span></span> <span data-ttu-id="facdc-109">これは、ビットマスク`CorFieldAttr`値。</span><span class="sxs-lookup"><span data-stu-id="facdc-109">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="facdc-110">[in]BLOB としてフィールド シグネチャ。</span><span class="sxs-lookup"><span data-stu-id="facdc-110">[in] The field signature as a BLOB.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="facdc-111">[in]内のバイト数`pvSigBlob`です。</span><span class="sxs-lookup"><span data-stu-id="facdc-111">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `dwCPlusTypeFlage`  
 <span data-ttu-id="facdc-112">[in]`ELEMENT_TYPE_` *\** 定数値にします。</span><span class="sxs-lookup"><span data-stu-id="facdc-112">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="facdc-113">これは、`CorElementType`値。</span><span class="sxs-lookup"><span data-stu-id="facdc-113">This is a `CorElementType` value.</span></span> <span data-ttu-id="facdc-114">場合は、フィールドの定数値を定義しないを使用して`ELEMENT_TYPE_END`です。</span><span class="sxs-lookup"><span data-stu-id="facdc-114">If not defining a constant value for the field, use `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="facdc-115">[in]フィールドの定数値。</span><span class="sxs-lookup"><span data-stu-id="facdc-115">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="facdc-116">[in]サイズ (Unicode) 文字の`pValue`します。</span><span class="sxs-lookup"><span data-stu-id="facdc-116">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
 `pmd`  
 <span data-ttu-id="facdc-117">[out]`mdFieldDef`トークンが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="facdc-117">[out] The `mdFieldDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="facdc-118">要件</span><span class="sxs-lookup"><span data-stu-id="facdc-118">Requirements</span></span>  
 <span data-ttu-id="facdc-119">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="facdc-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="facdc-120">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="facdc-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="facdc-121">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="facdc-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="facdc-122">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="facdc-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="facdc-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="facdc-123">See Also</span></span>  
 [<span data-ttu-id="facdc-124">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="facdc-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="facdc-125">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="facdc-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
