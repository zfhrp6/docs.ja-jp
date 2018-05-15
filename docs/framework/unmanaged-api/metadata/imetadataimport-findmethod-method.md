---
title: IMetaDataImport::FindMethod メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMethod
helpviewer_keywords:
- FindMethod method [.NET Framework metadata]
- IMetaDataImport::FindMethod method [.NET Framework metadata]
ms.assetid: 0f9bde1d-e306-438d-941b-d0925b322304
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6b68d4e3d51fdb50290319de804a78c1a78a07a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportfindmethod-method"></a><span data-ttu-id="b9afc-102">IMetaDataImport::FindMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="b9afc-102">IMetaDataImport::FindMethod Method</span></span>
<span data-ttu-id="b9afc-103">ポインターを取得した MethodDef トークンが囲まれているメソッドに、指定した<xref:System.Type>指定した名前とメタデータ シグネチャを持つとします。</span><span class="sxs-lookup"><span data-stu-id="b9afc-103">Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9afc-104">構文</span><span class="sxs-lookup"><span data-stu-id="b9afc-104">Syntax</span></span>  
  
```  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMethodDef        *pmb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b9afc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b9afc-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="b9afc-106">[in]`mdTypeDef`を検索するメンバーを囲む型 (クラスまたはインターフェイス) のトークン。</span><span class="sxs-lookup"><span data-stu-id="b9afc-106">[in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for.</span></span> <span data-ttu-id="b9afc-107">この値が場合`mdTokenNil`、グローバル関数の参照を実行し、します。</span><span class="sxs-lookup"><span data-stu-id="b9afc-107">If this value is `mdTokenNil`, then the lookup is done for a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="b9afc-108">[in]検索するメソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="b9afc-108">[in] The name of the method to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="b9afc-109">[in]メソッドのバイナリ メタデータ シグネチャへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b9afc-109">[in] A pointer to the binary metadata signature of the method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="b9afc-110">[in]バイト サイズ`pvSigBlob`です。</span><span class="sxs-lookup"><span data-stu-id="b9afc-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="b9afc-111">[out]一致する MethodDef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b9afc-111">[out] A pointer to the matching MethodDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9afc-112">コメント</span><span class="sxs-lookup"><span data-stu-id="b9afc-112">Remarks</span></span>  
 <span data-ttu-id="b9afc-113">外側のクラスまたはインターフェイスを使用して、メソッドを指定する (`td`)、その名前 (`szName`)、および必要に応じて、シグネチャ (`pvSigBlob`)。</span><span class="sxs-lookup"><span data-stu-id="b9afc-113">You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="b9afc-114">クラスまたはインターフェイスで同じ名前の複数のメソッドである可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b9afc-114">There might be multiple methods with the same name in a class or interface.</span></span> <span data-ttu-id="b9afc-115">その場合は、一意の一致を検索するメソッドのシグネチャを渡します。</span><span class="sxs-lookup"><span data-stu-id="b9afc-115">In that case, pass the method's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="b9afc-116">渡される署名`FindMethod`生成された、現在のスコープで特定のスコープにバインドされるためです。</span><span class="sxs-lookup"><span data-stu-id="b9afc-116">The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="b9afc-117">シグネチャには、外側のクラスまたは値の型を識別するトークンを埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="b9afc-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="b9afc-118">トークンは、ローカルの TypeDef テーブルへのインデックスです。</span><span class="sxs-lookup"><span data-stu-id="b9afc-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="b9afc-119">現在のスコープのコンテキストの外部のランタイムのシグネチャを作成できずを入力としてにその署名を使用して`FindMethod`です。</span><span class="sxs-lookup"><span data-stu-id="b9afc-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.</span></span>  
  
 <span data-ttu-id="b9afc-120">`FindMethod` クラスまたはインターフェイスで直接定義されたメソッドのみを検索します。継承されたメソッドが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="b9afc-120">`FindMethod` finds only methods that were defined directly in the class or interface; it does not find inherited methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9afc-121">要件</span><span class="sxs-lookup"><span data-stu-id="b9afc-121">Requirements</span></span>  
 <span data-ttu-id="b9afc-122">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b9afc-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9afc-123">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b9afc-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b9afc-124">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="b9afc-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b9afc-125">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9afc-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9afc-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="b9afc-126">See Also</span></span>  
 <xref:System.Reflection.MethodInfo>  
 [<span data-ttu-id="b9afc-127">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b9afc-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="b9afc-128">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b9afc-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
