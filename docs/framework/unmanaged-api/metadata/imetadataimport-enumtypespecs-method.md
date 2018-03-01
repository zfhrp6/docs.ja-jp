---
title: "IMetaDataImport::EnumTypeSpecs メソッド"
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
- IMetaDataImport.EnumTypeSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeSpecs
helpviewer_keywords:
- EnumTypeSpecs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeSpecs method [.NET Framework metadata]
ms.assetid: 75331c7b-988b-436c-9eb9-a270d37b4f06
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9e34a3086474918c913a366c02bbf9eadf313b43
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumtypespecs-method"></a><span data-ttu-id="ee4ec-102">IMetaDataImport::EnumTypeSpecs メソッド</span><span class="sxs-lookup"><span data-stu-id="ee4ec-102">IMetaDataImport::EnumTypeSpecs Method</span></span>
<span data-ttu-id="ee4ec-103">現在のメタデータ スコープに定義されている TypeSpec トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-103">Enumerates TypeSpec tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee4ec-104">構文</span><span class="sxs-lookup"><span data-stu-id="ee4ec-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ee4ec-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ee4ec-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="ee4ec-106">[入力、出力].列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="ee4ec-107">この値は、このメソッドの最初の呼び出しで、NULL をする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-107">This value must be NULL for the first call of this method.</span></span>  
  
 `rTypeSpecs`  
 <span data-ttu-id="ee4ec-108">[out]TypeSpec トークンを格納する配列。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-108">[out] The array used to store the TypeSpec tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="ee4ec-109">[in] `rTypeSpecs` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-109">[in] The maximum size of the `rTypeSpecs` array.</span></span>  
  
 `pcTypeSpecs`  
 <span data-ttu-id="ee4ec-110">[out]返される TypeSpec トークン数`rTypeSpecs`です。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-110">[out] The number of TypeSpec tokens returned in `rTypeSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ee4ec-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="ee4ec-111">Return Value</span></span>  
  
|<span data-ttu-id="ee4ec-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ee4ec-112">HRESULT</span></span>|<span data-ttu-id="ee4ec-113">説明</span><span class="sxs-lookup"><span data-stu-id="ee4ec-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="ee4ec-114">`EnumTypeSpecs`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-114">`EnumTypeSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="ee4ec-115">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="ee4ec-116">その場合は、`pcTypeSpecs`ゼロです。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-116">In that case, `pcTypeSpecs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee4ec-117">コメント</span><span class="sxs-lookup"><span data-stu-id="ee4ec-117">Remarks</span></span>  
 <span data-ttu-id="ee4ec-118">TypeSpec トークンがによって作成された、 [imetadataemit::gettokenfromtypespec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-118">The TypeSpec tokens are created by the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee4ec-119">必要条件</span><span class="sxs-lookup"><span data-stu-id="ee4ec-119">Requirements</span></span>  
 <span data-ttu-id="ee4ec-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee4ec-121">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ee4ec-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ee4ec-122">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="ee4ec-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ee4ec-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee4ec-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee4ec-124">参照</span><span class="sxs-lookup"><span data-stu-id="ee4ec-124">See Also</span></span>  
 [<span data-ttu-id="ee4ec-125">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ee4ec-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="ee4ec-126">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ee4ec-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
