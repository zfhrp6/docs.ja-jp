---
title: IMetaDataImport::EnumMembers メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembers
helpviewer_keywords:
- IMetaDataImport::EnumMembers method [.NET Framework metadata]
- EnumMembers method [.NET Framework metadata]
ms.assetid: 3fb8e178-342b-4c89-9bcf-f7f834e6cb77
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 46ee8c62861a62ac044f295f7da082756d87347b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447634"
---
# <a name="imetadataimportenummembers-method"></a><span data-ttu-id="8968a-102">IMetaDataImport::EnumMembers メソッド</span><span class="sxs-lookup"><span data-stu-id="8968a-102">IMetaDataImport::EnumMembers Method</span></span>
<span data-ttu-id="8968a-103">指定した型のメンバーを表す MemberDef トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="8968a-103">Enumerates MemberDef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8968a-104">構文</span><span class="sxs-lookup"><span data-stu-id="8968a-104">Syntax</span></span>  
  
```  
HRESULT EnumMembers (   
   [in, out]  HCORENUM    *phEnum,   
   [in]  mdTypeDef   cl,   
   [out] mdToken     rMembers[],   
   [in]  ULONG       cMax,   
   [out] ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8968a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8968a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="8968a-106">[入力、出力].列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8968a-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="8968a-107">[in]メンバーは、列挙型を表す TypeDef トークンです。</span><span class="sxs-lookup"><span data-stu-id="8968a-107">[in] A TypeDef token representing the type whose members are to be enumerated.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="8968a-108">[out]MemberDef トークンを保持するために使用する配列。</span><span class="sxs-lookup"><span data-stu-id="8968a-108">[out] The array used to hold the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="8968a-109">[in] `rMembers` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="8968a-109">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="8968a-110">[out]実際に返される MemberDef トークン数`rMembers`です。</span><span class="sxs-lookup"><span data-stu-id="8968a-110">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8968a-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="8968a-111">Return Value</span></span>  
  
|<span data-ttu-id="8968a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8968a-112">HRESULT</span></span>|<span data-ttu-id="8968a-113">説明</span><span class="sxs-lookup"><span data-stu-id="8968a-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="8968a-114">`EnumMembers` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="8968a-114">`EnumMembers` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="8968a-115">MemberDef トークンを列挙することはありません。</span><span class="sxs-lookup"><span data-stu-id="8968a-115">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="8968a-116">その場合は、`pcTokens`ゼロです。</span><span class="sxs-lookup"><span data-stu-id="8968a-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8968a-117">コメント</span><span class="sxs-lookup"><span data-stu-id="8968a-117">Remarks</span></span>  
 <span data-ttu-id="8968a-118">クラスのメンバーのコレクションを列挙中に`EnumMembers`クラスで直接定義されたメンバーのみを返します。</span><span class="sxs-lookup"><span data-stu-id="8968a-118">When enumerating collections of members for a class, `EnumMembers` returns only members defined directly on the class.</span></span> <span data-ttu-id="8968a-119">返しませんクラスが継承する任意のメンバー場合でも、クラスは継承されたメンバーの実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="8968a-119">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span></span> <span data-ttu-id="8968a-120">継承されたメンバーを列挙するには、呼び出し元は明示的に継承チェーンを走査する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8968a-120">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span></span> <span data-ttu-id="8968a-121">継承チェーンの規則を元のメタデータを生成したコンパイラ、言語によって異なることがありますに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8968a-121">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8968a-122">要件</span><span class="sxs-lookup"><span data-stu-id="8968a-122">Requirements</span></span>  
 <span data-ttu-id="8968a-123">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8968a-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8968a-124">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8968a-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8968a-125">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="8968a-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8968a-126">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8968a-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8968a-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="8968a-127">See Also</span></span>  
 [<span data-ttu-id="8968a-128">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8968a-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="8968a-129">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8968a-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
