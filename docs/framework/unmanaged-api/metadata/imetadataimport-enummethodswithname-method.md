---
title: "IMetaDataImport::EnumMethodsWithName メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumMethodsWithName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumMethodsWithName
helpviewer_keywords:
- IMetaDataImport::EnumMethodsWithName method [.NET Framework metadata]
- EnumMethodsWithName method [.NET Framework metadata]
ms.assetid: a8624913-2e23-46ad-a0c1-bb8eccbbf20f
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9f16e66f83925104c4be1e69a476e398f33295a7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenummethodswithname-method"></a><span data-ttu-id="b2a41-102">IMetaDataImport::EnumMethodsWithName メソッド</span><span class="sxs-lookup"><span data-stu-id="b2a41-102">IMetaDataImport::EnumMethodsWithName Method</span></span>
<span data-ttu-id="b2a41-103">指定された名前を持ち、指定された TypeDef トークンによって参照される型で定義されているメソッドを列挙します。</span><span class="sxs-lookup"><span data-stu-id="b2a41-103">Enumerates methods that have the specified name and that are defined by the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2a41-104">構文</span><span class="sxs-lookup"><span data-stu-id="b2a41-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodsWithName (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdTypeDef       cl,  
   [in]  LPCWSTR         szName,  
   [out] mdMethodDef     rMethods[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b2a41-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b2a41-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="b2a41-106">[入力、出力].列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="b2a41-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="b2a41-107">このメソッドの最初の呼び出しで NULL があります。</span><span class="sxs-lookup"><span data-stu-id="b2a41-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="b2a41-108">[in]型を列挙するには、そのメソッドを表す TypeDef トークンです。</span><span class="sxs-lookup"><span data-stu-id="b2a41-108">[in] A TypeDef token representing the type whose methods to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="b2a41-109">[in]列挙体のスコープを制限する名前です。</span><span class="sxs-lookup"><span data-stu-id="b2a41-109">[in] The name that limits the scope of the enumeration.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="b2a41-110">[out]MethodDef トークンを格納する配列。</span><span class="sxs-lookup"><span data-stu-id="b2a41-110">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b2a41-111">[in] `rMethods` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="b2a41-111">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="b2a41-112">[out]MethodDef トークンで返される数`rMethods`です。</span><span class="sxs-lookup"><span data-stu-id="b2a41-112">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2a41-113">コメント</span><span class="sxs-lookup"><span data-stu-id="b2a41-113">Remarks</span></span>  
 <span data-ttu-id="b2a41-114">このメソッドは、フィールド、メソッドがないプロパティまたはイベントを列挙します。</span><span class="sxs-lookup"><span data-stu-id="b2a41-114">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="b2a41-115">異なり[imetadataimport::enummethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md)、`EnumMethodsWithName`を指定した名前を持たないすべてのメソッド トークンを破棄します。</span><span class="sxs-lookup"><span data-stu-id="b2a41-115">Unlike [IMetaDataImport::EnumMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` discards all method tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2a41-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="b2a41-116">Return Value</span></span>  
  
|<span data-ttu-id="b2a41-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b2a41-117">HRESULT</span></span>|<span data-ttu-id="b2a41-118">説明</span><span class="sxs-lookup"><span data-stu-id="b2a41-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b2a41-119">`EnumMethodsWithName`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="b2a41-119">`EnumMethodsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b2a41-120">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="b2a41-120">There are no tokens to enumerate.</span></span> <span data-ttu-id="b2a41-121">その場合は、`pcTokens`ゼロです。</span><span class="sxs-lookup"><span data-stu-id="b2a41-121">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b2a41-122">必要条件</span><span class="sxs-lookup"><span data-stu-id="b2a41-122">Requirements</span></span>  
 <span data-ttu-id="b2a41-123">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b2a41-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2a41-124">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b2a41-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b2a41-125">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="b2a41-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b2a41-126">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2a41-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2a41-127">参照</span><span class="sxs-lookup"><span data-stu-id="b2a41-127">See Also</span></span>  
 [<span data-ttu-id="b2a41-128">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b2a41-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="b2a41-129">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b2a41-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
