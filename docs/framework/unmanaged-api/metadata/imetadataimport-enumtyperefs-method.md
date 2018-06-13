---
title: IMetaDataImport::EnumTypeRefs メソッド
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b8a4fe2a65244156abe1bb0da4266f949ddd3df6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447074"
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="5c9b9-102">IMetaDataImport::EnumTypeRefs メソッド</span><span class="sxs-lookup"><span data-stu-id="5c9b9-102">IMetaDataImport::EnumTypeRefs Method</span></span>
<span data-ttu-id="5c9b9-103">現在のメタデータ スコープに定義されている TypeRef トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="5c9b9-103">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c9b9-104">構文</span><span class="sxs-lookup"><span data-stu-id="5c9b9-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,   
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTypeRefs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5c9b9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5c9b9-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="5c9b9-106">[入力、出力].列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5c9b9-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="5c9b9-107">このメソッドの最初の呼び出しで NULL があります。</span><span class="sxs-lookup"><span data-stu-id="5c9b9-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="5c9b9-108">[out]TypeRef トークンを格納する配列。</span><span class="sxs-lookup"><span data-stu-id="5c9b9-108">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="5c9b9-109">[in] `rTypeRefs` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="5c9b9-109">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="5c9b9-110">[out]返される TypeRef トークンの数へのポインター`rTypeRefs`です。</span><span class="sxs-lookup"><span data-stu-id="5c9b9-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c9b9-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="5c9b9-111">Return Value</span></span>  
  
|<span data-ttu-id="5c9b9-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5c9b9-112">HRESULT</span></span>|<span data-ttu-id="5c9b9-113">説明</span><span class="sxs-lookup"><span data-stu-id="5c9b9-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="5c9b9-114">`EnumTypeRefs` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="5c9b9-114">`EnumTypeRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="5c9b9-115">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="5c9b9-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="5c9b9-116">その場合は、`pcTypeRefs`ゼロです。</span><span class="sxs-lookup"><span data-stu-id="5c9b9-116">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c9b9-117">コメント</span><span class="sxs-lookup"><span data-stu-id="5c9b9-117">Remarks</span></span>  
 <span data-ttu-id="5c9b9-118">TypeRef トークンでは、型への参照を表します。</span><span class="sxs-lookup"><span data-stu-id="5c9b9-118">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c9b9-119">要件</span><span class="sxs-lookup"><span data-stu-id="5c9b9-119">Requirements</span></span>  
 <span data-ttu-id="5c9b9-120">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5c9b9-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c9b9-121">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5c9b9-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5c9b9-122">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="5c9b9-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5c9b9-123">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c9b9-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c9b9-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="5c9b9-124">See Also</span></span>  
 [<span data-ttu-id="5c9b9-125">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5c9b9-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="5c9b9-126">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5c9b9-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
