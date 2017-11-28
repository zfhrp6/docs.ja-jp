---
title: "IMetaDataImport::EnumMembersWithName メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumMembersWithName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumMembersWithName
helpviewer_keywords:
- IMetaDataImport::EnumMembersWithName method [.NET Framework metadata]
- EnumMembersWithName method [.NET Framework metadata]
ms.assetid: 7c9e9120-3104-42f0-86ce-19a025f20dcc
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 64568fb185cd8a18e43639568ecb67fcfa350dba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenummemberswithname-method"></a><span data-ttu-id="30b5b-102">IMetaDataImport::EnumMembersWithName メソッド</span><span class="sxs-lookup"><span data-stu-id="30b5b-102">IMetaDataImport::EnumMembersWithName Method</span></span>
<span data-ttu-id="30b5b-103">指定した名前を持つ指定した型のメンバーを表す MemberDef トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="30b5b-103">Enumerates MemberDef tokens representing members of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30b5b-104">構文</span><span class="sxs-lookup"><span data-stu-id="30b5b-104">Syntax</span></span>  
  
```  
HRESULT EnumMembersWithName (  
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   cl,   
   [in]      LPCWSTR     szName,   
   [out]     mdToken     rMembers[],   
   [in]      ULONG       cMax,   
   [out]     ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="30b5b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="30b5b-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="30b5b-106">[入力、出力].列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="30b5b-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="30b5b-107">[in]列挙のメンバーを持つ型を表す TypeDef トークンです。</span><span class="sxs-lookup"><span data-stu-id="30b5b-107">[in] A TypeDef token representing the type with members to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="30b5b-108">[in]列挙子のスコープを制限するメンバーの名前。</span><span class="sxs-lookup"><span data-stu-id="30b5b-108">[in] The member name that limits the scope of the enumerator.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="30b5b-109">[out]MemberDef トークンを格納する配列。</span><span class="sxs-lookup"><span data-stu-id="30b5b-109">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="30b5b-110">[in] `rMembers` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="30b5b-110">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="30b5b-111">[out]実際に返される MemberDef トークン数`rMembers`です。</span><span class="sxs-lookup"><span data-stu-id="30b5b-111">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30b5b-112">コメント</span><span class="sxs-lookup"><span data-stu-id="30b5b-112">Remarks</span></span>  
 <span data-ttu-id="30b5b-113">このメソッドは、フィールド、メソッドがないプロパティまたはイベントを列挙します。</span><span class="sxs-lookup"><span data-stu-id="30b5b-113">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="30b5b-114">異なり[imetadataimport::enummembers](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md)、`EnumMembersWithName`指定した名前がないすべてのフィールドとメンバーのトークンを破棄します。</span><span class="sxs-lookup"><span data-stu-id="30b5b-114">Unlike [IMetaDataImport::EnumMembers](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md), `EnumMembersWithName` discards all field and member tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30b5b-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="30b5b-115">Return Value</span></span>  
  
|<span data-ttu-id="30b5b-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="30b5b-116">HRESULT</span></span>|<span data-ttu-id="30b5b-117">説明</span><span class="sxs-lookup"><span data-stu-id="30b5b-117">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="30b5b-118">`EnumTypeDefs`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="30b5b-118">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="30b5b-119">MemberDef トークンを列挙することはありません。</span><span class="sxs-lookup"><span data-stu-id="30b5b-119">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="30b5b-120">その場合は、`pcTokens`ゼロです。</span><span class="sxs-lookup"><span data-stu-id="30b5b-120">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="30b5b-121">要件</span><span class="sxs-lookup"><span data-stu-id="30b5b-121">Requirements</span></span>  
 <span data-ttu-id="30b5b-122">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="30b5b-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30b5b-123">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="30b5b-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="30b5b-124">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="30b5b-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="30b5b-125">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30b5b-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30b5b-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="30b5b-126">See Also</span></span>  
 [<span data-ttu-id="30b5b-127">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="30b5b-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="30b5b-128">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="30b5b-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
