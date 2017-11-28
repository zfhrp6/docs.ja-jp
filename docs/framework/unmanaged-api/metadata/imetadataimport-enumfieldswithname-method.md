---
title: "IMetaDataImport::EnumFieldsWithName メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumFieldsWithName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumFieldsWithName
helpviewer_keywords:
- IMetaDataImport::EnumFieldsWithName method [.NET Framework metadata]
- EnumFieldsWithName method [.NET Framework metadata]
ms.assetid: 42145e8d-000f-4d0b-ae43-c08201190fa2
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2f6104f287350a9ac2f0eb5b82c05422a18a48a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumfieldswithname-method"></a><span data-ttu-id="3110a-102">IMetaDataImport::EnumFieldsWithName メソッド</span><span class="sxs-lookup"><span data-stu-id="3110a-102">IMetaDataImport::EnumFieldsWithName Method</span></span>
<span data-ttu-id="3110a-103">指定した名前を持つ指定した型の FieldDef トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="3110a-103">Enumerates FieldDef tokens of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3110a-104">構文</span><span class="sxs-lookup"><span data-stu-id="3110a-104">Syntax</span></span>  
  
```  
HRESULT EnumFieldsWithName (  
   [in, out] HCORENUM    *phEnum,   
   [in]  mdTypeDef       cl,   
   [in]  LPCWSTR         szName,   
   [out] mdFieldDef      rFields[],   
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTokens   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3110a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3110a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="3110a-106">[入力、出力].列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="3110a-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="3110a-107">[in]その結果、フィールドが列挙するのには、型のトークンです。</span><span class="sxs-lookup"><span data-stu-id="3110a-107">[in] The token of the type whose fields are to be enumerated.</span></span>  
  
 `szName`  
 <span data-ttu-id="3110a-108">[in]列挙体のスコープを制限するフィールド名です。</span><span class="sxs-lookup"><span data-stu-id="3110a-108">[in] The field name that limits the scope of the enumeration.</span></span>  
  
 `rFields`  
 <span data-ttu-id="3110a-109">[out]FieldDef トークンを格納する配列。</span><span class="sxs-lookup"><span data-stu-id="3110a-109">[out] Array used to store the FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3110a-110">[in] `rFields` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="3110a-110">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="3110a-111">[out]実際に返される FieldDef トークン数`rFields`です。</span><span class="sxs-lookup"><span data-stu-id="3110a-111">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3110a-112">コメント</span><span class="sxs-lookup"><span data-stu-id="3110a-112">Remarks</span></span>  
 <span data-ttu-id="3110a-113">異なり[imetadataimport::enumfields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md)、`EnumFieldsWithName`を指定した名前を持たないすべてのフィールド トークンを破棄します。</span><span class="sxs-lookup"><span data-stu-id="3110a-113">Unlike [IMetaDataImport::EnumFields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md), `EnumFieldsWithName` discards all field tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3110a-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="3110a-114">Return Value</span></span>  
  
|<span data-ttu-id="3110a-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3110a-115">HRESULT</span></span>|<span data-ttu-id="3110a-116">説明</span><span class="sxs-lookup"><span data-stu-id="3110a-116">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="3110a-117">`EnumFieldsWithName`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="3110a-117">`EnumFieldsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="3110a-118">列挙するフィールドはありません。</span><span class="sxs-lookup"><span data-stu-id="3110a-118">There are no fields to enumerate.</span></span> <span data-ttu-id="3110a-119">その場合は、`pcTokens`ゼロです。</span><span class="sxs-lookup"><span data-stu-id="3110a-119">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3110a-120">要件</span><span class="sxs-lookup"><span data-stu-id="3110a-120">Requirements</span></span>  
 <span data-ttu-id="3110a-121">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3110a-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3110a-122">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3110a-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3110a-123">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="3110a-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3110a-124">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3110a-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3110a-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="3110a-125">See Also</span></span>  
 [<span data-ttu-id="3110a-126">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3110a-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="3110a-127">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3110a-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
