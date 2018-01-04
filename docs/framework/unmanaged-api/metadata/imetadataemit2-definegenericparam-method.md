---
title: "IMetaDataEmit2::DefineGenericParam メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit2.DefineGenericParam
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit2::DefineGenericParam
helpviewer_keywords:
- IMetaDataEmit2::DefineGenericParam method [.NET Framework metadata]
- DefineGenericParam method [.NET Framework metadata]
ms.assetid: 47b2a3b6-907d-43dc-858d-1ae7dca1316a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 598c616ca91b73d9cb184d9e431e75d00d3f9850
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemit2definegenericparam-method"></a><span data-ttu-id="2ee6d-102">IMetaDataEmit2::DefineGenericParam メソッド</span><span class="sxs-lookup"><span data-stu-id="2ee6d-102">IMetaDataEmit2::DefineGenericParam Method</span></span>
<span data-ttu-id="2ee6d-103">ジェネリック型パラメーターの定義を作成し、そのジェネリック型パラメーターにトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="2ee6d-103">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ee6d-104">構文</span><span class="sxs-lookup"><span data-stu-id="2ee6d-104">Syntax</span></span>  
  
```  
HRESULT DefineGenericParam (   
    [in]  mdToken         tk,   
    [in]  ULONG           ulParamSeq,   
    [in]  DWORD           dwParamFlags,   
    [in]  LPCWSTR         szname,   
    [in]  DWORD           reserved,   
    [in]  mdToken         rtkConstraints[],   
    [out] mdGenericParam  *pgp  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ee6d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2ee6d-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="2ee6d-106">[in]`mdTypeDef`または`mdMethodDef`メソッドまたはジェネリック パラメーターを定義するコンス トラクターを表すトークンです。</span><span class="sxs-lookup"><span data-stu-id="2ee6d-106">[in] An `mdTypeDef` or `mdMethodDef` token that represents the method or constructor for which to define a generic parameter.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="2ee6d-107">[in]ジェネリック パラメーターのインデックス。</span><span class="sxs-lookup"><span data-stu-id="2ee6d-107">[in] The index of the generic parameter.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="2ee6d-108">[in]値、 [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md)ジェネリック パラメーターの型を表す列挙体です。</span><span class="sxs-lookup"><span data-stu-id="2ee6d-108">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szname`  
 <span data-ttu-id="2ee6d-109">[in]パラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="2ee6d-109">[in] The name of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="2ee6d-110">[in]このパラメーターは将来の機能拡張で予約されています。</span><span class="sxs-lookup"><span data-stu-id="2ee6d-110">[in] This parameter is reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="2ee6d-111">[in]型の制約 0 で終わる配列。</span><span class="sxs-lookup"><span data-stu-id="2ee6d-111">[in] A zero-terminated array of type constraints.</span></span> <span data-ttu-id="2ee6d-112">配列のメンバーである必要があります、 `mdTypeDef`、 `mdTypeRef`、または`mdTypeSpec`メタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="2ee6d-112">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
 `pgp`  
 <span data-ttu-id="2ee6d-113">[out]ジェネリック パラメーターを表すトークンです。</span><span class="sxs-lookup"><span data-stu-id="2ee6d-113">[out] A token that represents the generic parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ee6d-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="2ee6d-114">Requirements</span></span>  
 <span data-ttu-id="2ee6d-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2ee6d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ee6d-116">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2ee6d-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2ee6d-117">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="2ee6d-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2ee6d-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ee6d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ee6d-119">参照</span><span class="sxs-lookup"><span data-stu-id="2ee6d-119">See Also</span></span>  
 [<span data-ttu-id="2ee6d-120">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2ee6d-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="2ee6d-121">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2ee6d-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
