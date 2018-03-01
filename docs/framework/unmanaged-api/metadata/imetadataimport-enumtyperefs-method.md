---
title: "IMetaDataImport::EnumTypeRefs メソッド"
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
- IMetaDataImport.EnumTypeRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeRefs
helpviewer_keywords:
- EnumTypeRefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeRefs method [.NET Framework metadata]
ms.assetid: b4896b8f-8e97-469c-8089-e72a025661b5
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3099f129abd3477aeb08526b9f0dcd5b701d4dc8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="a1ba8-102">IMetaDataImport::EnumTypeRefs メソッド</span><span class="sxs-lookup"><span data-stu-id="a1ba8-102">IMetaDataImport::EnumTypeRefs Method</span></span>
<span data-ttu-id="a1ba8-103">現在のメタデータ スコープに定義されている TypeRef トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="a1ba8-103">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1ba8-104">構文</span><span class="sxs-lookup"><span data-stu-id="a1ba8-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,   
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTypeRefs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a1ba8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a1ba8-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="a1ba8-106">[入力、出力].列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a1ba8-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="a1ba8-107">このメソッドの最初の呼び出しで NULL があります。</span><span class="sxs-lookup"><span data-stu-id="a1ba8-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="a1ba8-108">[out]TypeRef トークンを格納する配列。</span><span class="sxs-lookup"><span data-stu-id="a1ba8-108">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a1ba8-109">[in] `rTypeRefs` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="a1ba8-109">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="a1ba8-110">[out]返される TypeRef トークンの数へのポインター`rTypeRefs`です。</span><span class="sxs-lookup"><span data-stu-id="a1ba8-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1ba8-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="a1ba8-111">Return Value</span></span>  
  
|<span data-ttu-id="a1ba8-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a1ba8-112">HRESULT</span></span>|<span data-ttu-id="a1ba8-113">説明</span><span class="sxs-lookup"><span data-stu-id="a1ba8-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a1ba8-114">`EnumTypeRefs`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="a1ba8-114">`EnumTypeRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a1ba8-115">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="a1ba8-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="a1ba8-116">その場合は、`pcTypeRefs`ゼロです。</span><span class="sxs-lookup"><span data-stu-id="a1ba8-116">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1ba8-117">コメント</span><span class="sxs-lookup"><span data-stu-id="a1ba8-117">Remarks</span></span>  
 <span data-ttu-id="a1ba8-118">TypeRef トークンでは、型への参照を表します。</span><span class="sxs-lookup"><span data-stu-id="a1ba8-118">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1ba8-119">必要条件</span><span class="sxs-lookup"><span data-stu-id="a1ba8-119">Requirements</span></span>  
 <span data-ttu-id="a1ba8-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a1ba8-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1ba8-121">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a1ba8-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a1ba8-122">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="a1ba8-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a1ba8-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1ba8-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1ba8-124">参照</span><span class="sxs-lookup"><span data-stu-id="a1ba8-124">See Also</span></span>  
 [<span data-ttu-id="a1ba8-125">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1ba8-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="a1ba8-126">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1ba8-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
