---
title: "IMetaDataImport::EnumTypeDefs メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumTypeDefs
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a07d9ff237e6d3838fffb068e3a9ebf9febf66fc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="bccd5-102">IMetaDataImport::EnumTypeDefs メソッド</span><span class="sxs-lookup"><span data-stu-id="bccd5-102">IMetaDataImport::EnumTypeDefs Method</span></span>
<span data-ttu-id="bccd5-103">現在のスコープ内のすべての型を表す TypeDef トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="bccd5-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bccd5-104">構文</span><span class="sxs-lookup"><span data-stu-id="bccd5-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,   
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,   
   [out] ULONG      *pcTypeDefs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bccd5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bccd5-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="bccd5-106">[out]新しい列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="bccd5-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="bccd5-107">このメソッドの最初の呼び出しで NULL があります。</span><span class="sxs-lookup"><span data-stu-id="bccd5-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="bccd5-108">[in]TypeDef トークンの保存に使用する配列。</span><span class="sxs-lookup"><span data-stu-id="bccd5-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="bccd5-109">[in] `rTypeDefs` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="bccd5-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="bccd5-110">[out]返される TypeDef トークンの数`rTypeDefs`です。</span><span class="sxs-lookup"><span data-stu-id="bccd5-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bccd5-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="bccd5-111">Return Value</span></span>  
  
|<span data-ttu-id="bccd5-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bccd5-112">HRESULT</span></span>|<span data-ttu-id="bccd5-113">説明</span><span class="sxs-lookup"><span data-stu-id="bccd5-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="bccd5-114">`EnumTypeDefs`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="bccd5-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="bccd5-115">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="bccd5-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="bccd5-116">その場合は、`pcTypeDefs`ゼロです。</span><span class="sxs-lookup"><span data-stu-id="bccd5-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bccd5-117">コメント</span><span class="sxs-lookup"><span data-stu-id="bccd5-117">Remarks</span></span>  
 <span data-ttu-id="bccd5-118">TypeDef トークンは、クラスやインターフェイスなど、型だけでなく、機能拡張メカニズムを使用して追加された型を表します。</span><span class="sxs-lookup"><span data-stu-id="bccd5-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bccd5-119">要件</span><span class="sxs-lookup"><span data-stu-id="bccd5-119">Requirements</span></span>  
 <span data-ttu-id="bccd5-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="bccd5-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bccd5-121">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bccd5-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bccd5-122">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="bccd5-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bccd5-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bccd5-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bccd5-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="bccd5-124">See Also</span></span>  
 [<span data-ttu-id="bccd5-125">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bccd5-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="bccd5-126">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bccd5-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
