---
title: "IMetaDataEmit::DefineTypeRefByName メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineTypeRefByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineTypeRefByName
helpviewer_keywords:
- DefineTypeRefByName method [.NET Framework metadata]
- IMetaDataEmit::DefineTypeRefByName method [.NET Framework metadata]
ms.assetid: c30a4ce3-2d3e-411a-98df-e62ac4a5dd50
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9ce04733fa9f149f155d850c53b65b263943cf8b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="f7c37-102">IMetaDataEmit::DefineTypeRefByName メソッド</span><span class="sxs-lookup"><span data-stu-id="f7c37-102">IMetaDataEmit::DefineTypeRefByName Method</span></span>
<span data-ttu-id="f7c37-103">現在のスコープ外には、指定されたスコープで定義されている型のメタデータ トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="f7c37-103">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7c37-104">構文</span><span class="sxs-lookup"><span data-stu-id="f7c37-104">Syntax</span></span>  
  
```  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f7c37-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f7c37-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="f7c37-106">[in]解決スコープを指定するトークンです。</span><span class="sxs-lookup"><span data-stu-id="f7c37-106">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="f7c37-107">次のトークンの種類は有効です。</span><span class="sxs-lookup"><span data-stu-id="f7c37-107">The following token types are valid:</span></span>  
  
-   <span data-ttu-id="f7c37-108">`mdModuleRef`、型が呼び出し元が定義されている同じアセンブリに定義されている場合。</span><span class="sxs-lookup"><span data-stu-id="f7c37-108">`mdModuleRef`, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="f7c37-109">`mdAssemblyRef`、型が呼び出し元が定義されている以外のアセンブリで定義されている場合。</span><span class="sxs-lookup"><span data-stu-id="f7c37-109">`mdAssemblyRef`, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="f7c37-110">`mdTypeRef`、型が入れ子にされた型である場合。</span><span class="sxs-lookup"><span data-stu-id="f7c37-110">`mdTypeRef`, if the type is a nested type.</span></span>  
  
-   <span data-ttu-id="f7c37-111">`mdModule`、型が呼び出し元が定義されている同じモジュールで定義されている場合。</span><span class="sxs-lookup"><span data-stu-id="f7c37-111">`mdModule`, if the type is defined in the same module in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="f7c37-112">型がグローバルに定義されている場合は null です。</span><span class="sxs-lookup"><span data-stu-id="f7c37-112">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="f7c37-113">[in]Unicode で対象の型の名前です。</span><span class="sxs-lookup"><span data-stu-id="f7c37-113">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="f7c37-114">[out]ポインター、`mdTypeRef`型に割り当てられているトークンです。</span><span class="sxs-lookup"><span data-stu-id="f7c37-114">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7c37-115">要件</span><span class="sxs-lookup"><span data-stu-id="f7c37-115">Requirements</span></span>  
 <span data-ttu-id="f7c37-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f7c37-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7c37-117">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f7c37-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f7c37-118">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="f7c37-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f7c37-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7c37-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7c37-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="f7c37-120">See Also</span></span>  
 [<span data-ttu-id="f7c37-121">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f7c37-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="f7c37-122">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f7c37-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
