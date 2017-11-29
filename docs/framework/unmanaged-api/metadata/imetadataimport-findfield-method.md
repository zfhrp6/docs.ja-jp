---
title: "IMetaDataImport::FindField メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.FindField
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::FindField
helpviewer_keywords:
- IMetaDataImport::FindField method [.NET Framework metadata]
- FindField method [.NET Framework metadata]
ms.assetid: 38cd4e16-fbb2-471c-aa73-ac51a1931ad2
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2178f8738ca510fb2163c1043dd94ebcb7043904
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportfindfield-method"></a><span data-ttu-id="fb9d1-102">IMetaDataImport::FindField メソッド</span><span class="sxs-lookup"><span data-stu-id="fb9d1-102">IMetaDataImport::FindField Method</span></span>
<span data-ttu-id="fb9d1-103">ポインターを取得した FieldDef トークンが囲まれているフィールドの指定した<xref:System.Type>指定した名前とメタデータ シグネチャを持つとします。</span><span class="sxs-lookup"><span data-stu-id="fb9d1-103">Gets a pointer to the FieldDef token for the field that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb9d1-104">構文</span><span class="sxs-lookup"><span data-stu-id="fb9d1-104">Syntax</span></span>  
  
```  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb9d1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fb9d1-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="fb9d1-106">[in]クラスまたはインターフェイスを検索するフィールドを囲む TypeDef トークンです。</span><span class="sxs-lookup"><span data-stu-id="fb9d1-106">[in] The TypeDef token for the class or interface that encloses the field to search for.</span></span> <span data-ttu-id="fb9d1-107">この値が場合`mdTokenNil`、グローバル変数の参照が行われます。</span><span class="sxs-lookup"><span data-stu-id="fb9d1-107">If this value is `mdTokenNil`, the lookup is done for a global variable.</span></span>  
  
 `szName`  
 <span data-ttu-id="fb9d1-108">[in]検索するフィールドの名前。</span><span class="sxs-lookup"><span data-stu-id="fb9d1-108">[in] The name of the field to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="fb9d1-109">[in]フィールドのバイナリ メタデータ シグネチャへのポインター。</span><span class="sxs-lookup"><span data-stu-id="fb9d1-109">[in] A pointer to the binary metadata signature of the field.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="fb9d1-110">[in]バイト サイズ`pvSigBlob`です。</span><span class="sxs-lookup"><span data-stu-id="fb9d1-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="fb9d1-111">[out]一致する FieldDef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="fb9d1-111">[out] A pointer to the matching FieldDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb9d1-112">コメント</span><span class="sxs-lookup"><span data-stu-id="fb9d1-112">Remarks</span></span>  
 <span data-ttu-id="fb9d1-113">外側のクラスまたはインターフェイスを使用してフィールドを指定する (`td`)、その名前 (`szName`)、および必要に応じて、シグネチャ (`pvSigBlob`)。</span><span class="sxs-lookup"><span data-stu-id="fb9d1-113">You specify the field using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="fb9d1-114">渡される署名`FindField`生成された、現在のスコープで特定のスコープにバインドされるためです。</span><span class="sxs-lookup"><span data-stu-id="fb9d1-114">The signature passed to `FindField` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="fb9d1-115">シグネチャには、外側のクラスまたは値の型を識別するトークンを埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="fb9d1-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="fb9d1-116">(トークンは、ローカルの TypeDef テーブルへのインデックスです。)</span><span class="sxs-lookup"><span data-stu-id="fb9d1-116">(The token is an index into the local TypeDef table).</span></span> <span data-ttu-id="fb9d1-117">コンテキストの外部の現在のスコープの実行時のシグネチャを作成してへの入力としてその署名を使用することはできません`FindField`です。</span><span class="sxs-lookup"><span data-stu-id="fb9d1-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindField`.</span></span>  
  
 <span data-ttu-id="fb9d1-118">`FindField`クラスまたはインターフェイスで直接定義されたフィールドのみを検索します。継承されたフィールドは検索されません。</span><span class="sxs-lookup"><span data-stu-id="fb9d1-118">`FindField` finds only fields that were defined directly in the class or interface; it does not find inherited fields.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb9d1-119">要件</span><span class="sxs-lookup"><span data-stu-id="fb9d1-119">Requirements</span></span>  
 <span data-ttu-id="fb9d1-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="fb9d1-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb9d1-121">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fb9d1-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fb9d1-122">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="fb9d1-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fb9d1-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb9d1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb9d1-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="fb9d1-124">See Also</span></span>  
 [<span data-ttu-id="fb9d1-125">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fb9d1-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="fb9d1-126">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fb9d1-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
