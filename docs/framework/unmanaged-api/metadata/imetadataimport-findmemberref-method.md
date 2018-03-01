---
title: "IMetaDataImport::FindMemberRef メソッド"
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
- IMetaDataImport.FindMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMemberRef
helpviewer_keywords:
- IMetaDataImport::FindMemberRef method [.NET Framework metadata]
- FindMemberRef method [.NET Framework metadata]
ms.assetid: 1ccda329-d752-4d89-abe8-511af3c3f4c9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a94fb09e1ff62abac9dd716257ba75542453707e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportfindmemberref-method"></a><span data-ttu-id="cee52-102">IMetaDataImport::FindMemberRef メソッド</span><span class="sxs-lookup"><span data-stu-id="cee52-102">IMetaDataImport::FindMemberRef Method</span></span>
<span data-ttu-id="cee52-103">指定したで囲まれているメンバーの MemberRef トークンへのポインターが参照されている取得<xref:System.Type>指定した名前とメタデータ シグネチャを持つとします。</span><span class="sxs-lookup"><span data-stu-id="cee52-103">Gets a pointer to the MemberRef token for the member reference that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cee52-104">構文</span><span class="sxs-lookup"><span data-stu-id="cee52-104">Syntax</span></span>  
  
```  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMemberRef        *pmr  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cee52-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cee52-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="cee52-106">[in]クラスまたはインターフェイスを検索するメンバーの参照を囲む TypeRef トークンです。</span><span class="sxs-lookup"><span data-stu-id="cee52-106">[in] The TypeRef token for the class or interface that encloses the member reference to search for.</span></span> <span data-ttu-id="cee52-107">この値が場合`mdTokenNil`、グローバル変数またはグローバル関数の参照の検索が行われます。</span><span class="sxs-lookup"><span data-stu-id="cee52-107">If this value is `mdTokenNil`, the lookup is done for a global variable or a global-function reference.</span></span>  
  
 `szName`  
 <span data-ttu-id="cee52-108">[in]検索するメンバーの参照の名前。</span><span class="sxs-lookup"><span data-stu-id="cee52-108">[in] The name of the member reference to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="cee52-109">[in]メンバー参照のバイナリ メタデータ シグネチャへのポインター。</span><span class="sxs-lookup"><span data-stu-id="cee52-109">[in] A pointer to the binary metadata signature of the member reference.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="cee52-110">[in]バイト サイズ`pvSigBlob`です。</span><span class="sxs-lookup"><span data-stu-id="cee52-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="cee52-111">[out]一致する MemberRef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="cee52-111">[out] A pointer to the matching MemberRef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cee52-112">コメント</span><span class="sxs-lookup"><span data-stu-id="cee52-112">Remarks</span></span>  
 <span data-ttu-id="cee52-113">外側のクラスまたはインターフェイスを使用してメンバーを指定する (`td`)、その名前 (`szName`)、および必要に応じて、シグネチャ (`pvSigBlob`)。</span><span class="sxs-lookup"><span data-stu-id="cee52-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="cee52-114">渡される署名`FindMemberRef`生成された、現在のスコープで特定のスコープにバインドされるためです。</span><span class="sxs-lookup"><span data-stu-id="cee52-114">The signature passed to `FindMemberRef` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="cee52-115">シグネチャには、外側のクラスまたは値の型を識別するトークンを埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="cee52-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="cee52-116">トークンは、ローカルの TypeDef テーブルへのインデックスです。</span><span class="sxs-lookup"><span data-stu-id="cee52-116">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="cee52-117">コンテキストの外部の現在のスコープの実行時のシグネチャを作成してへの入力としてその署名を使用することはできません`FindMemberRef`です。</span><span class="sxs-lookup"><span data-stu-id="cee52-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindMemberRef`.</span></span>  
  
 <span data-ttu-id="cee52-118">`FindMemberRef`クラスまたはインターフェイスで直接定義されたメンバーの参照のみを検索します。継承されたメンバーの参照は検索されません。</span><span class="sxs-lookup"><span data-stu-id="cee52-118">`FindMemberRef` finds only member references that were defined directly in the class or interface; it does not find inherited member references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cee52-119">必要条件</span><span class="sxs-lookup"><span data-stu-id="cee52-119">Requirements</span></span>  
 <span data-ttu-id="cee52-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cee52-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cee52-121">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cee52-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cee52-122">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="cee52-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cee52-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cee52-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cee52-124">参照</span><span class="sxs-lookup"><span data-stu-id="cee52-124">See Also</span></span>  
 [<span data-ttu-id="cee52-125">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cee52-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="cee52-126">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cee52-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
