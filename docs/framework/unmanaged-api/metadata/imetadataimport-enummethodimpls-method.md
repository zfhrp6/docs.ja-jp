---
title: "IMetaDataImport::EnumMethodImpls メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumMethodImpls
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumMethodImpls
helpviewer_keywords:
- EnumMethodImpls method [.NET Framework metadata]
- IMetaDataImport::EnumMethodImpls method [.NET Framework metadata]
ms.assetid: 4e0f865d-88b5-44bd-be35-492622e5e08e
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2634642c49c9d95765b6a93048a04ce512b28099
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenummethodimpls-method"></a><span data-ttu-id="b2b3c-102">IMetaDataImport::EnumMethodImpls メソッド</span><span class="sxs-lookup"><span data-stu-id="b2b3c-102">IMetaDataImport::EnumMethodImpls Method</span></span>
<span data-ttu-id="b2b3c-103">指定した型のメソッドを表す MethodBody トークンと MethodDeclaration トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="b2b3c-103">Enumerates MethodBody and MethodDeclaration tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2b3c-104">構文</span><span class="sxs-lookup"><span data-stu-id="b2b3c-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodImpls (  
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   td,   
   [out]     mdToken     rMethodBody[],   
   [out]     mdToken     rMethodDecl[],   
   [in]      ULONG       cMax,   
   [in]      ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b2b3c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b2b3c-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="b2b3c-106">[入力、出力].列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="b2b3c-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="b2b3c-107">このメソッドの最初の呼び出しで NULL があります。</span><span class="sxs-lookup"><span data-stu-id="b2b3c-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="b2b3c-108">[in]TypeDef トークンの型を列挙するメソッドの実装です。</span><span class="sxs-lookup"><span data-stu-id="b2b3c-108">[in] A TypeDef token for the type whose method implementations to enumerate.</span></span>  
  
 `rMethodBody`  
 <span data-ttu-id="b2b3c-109">[out]MethodBody トークンを格納する配列。</span><span class="sxs-lookup"><span data-stu-id="b2b3c-109">[out] The array to store the MethodBody tokens.</span></span>  
  
 `rMethodDecl`  
 <span data-ttu-id="b2b3c-110">[out]MethodDeclaration トークンを格納する配列。</span><span class="sxs-lookup"><span data-stu-id="b2b3c-110">[out] The array to store the MethodDeclaration tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b2b3c-111">[in]最大サイズ、`rMethodBody`と`rMethodDecl`配列。</span><span class="sxs-lookup"><span data-stu-id="b2b3c-111">[in] The maximum size of the `rMethodBody` and `rMethodDecl` arrays.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="b2b3c-112">[in]実際のメソッドで返される数`rMethodBody`と`rMethodDecl`です。</span><span class="sxs-lookup"><span data-stu-id="b2b3c-112">[in] The actual number of methods returned in `rMethodBody` and `rMethodDecl`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2b3c-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="b2b3c-113">Return Value</span></span>  
  
|<span data-ttu-id="b2b3c-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b2b3c-114">HRESULT</span></span>|<span data-ttu-id="b2b3c-115">説明</span><span class="sxs-lookup"><span data-stu-id="b2b3c-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b2b3c-116">`EnumMethodImpls`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="b2b3c-116">`EnumMethodImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b2b3c-117">列挙するメソッドのトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="b2b3c-117">There are no method tokens to enumerate.</span></span> <span data-ttu-id="b2b3c-118">その場合は、`pcTokens`ゼロです。</span><span class="sxs-lookup"><span data-stu-id="b2b3c-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b2b3c-119">要件</span><span class="sxs-lookup"><span data-stu-id="b2b3c-119">Requirements</span></span>  
 <span data-ttu-id="b2b3c-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b2b3c-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2b3c-121">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b2b3c-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b2b3c-122">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="b2b3c-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b2b3c-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2b3c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2b3c-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="b2b3c-124">See Also</span></span>  
 [<span data-ttu-id="b2b3c-125">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b2b3c-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="b2b3c-126">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b2b3c-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
