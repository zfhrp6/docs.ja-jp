---
title: "IMetaDataImport2::GetGenericParamProps メソッド"
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
- IMetaDataImport2.GetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamProps method [.NET Framework metadata]
- GetGenericParamProps method [.NET Framework metadata]
ms.assetid: dbb21e67-712b-49e7-a27c-a1e73ffd46c5
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 70a9669e2f47c3b56f7b50dc96ed2d3ba8314c4e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimport2getgenericparamprops-method"></a><span data-ttu-id="5995e-102">IMetaDataImport2::GetGenericParamProps メソッド</span><span class="sxs-lookup"><span data-stu-id="5995e-102">IMetaDataImport2::GetGenericParamProps Method</span></span>
<span data-ttu-id="5995e-103">指定したトークンによって表されるジェネリック パラメーターに関連付けられているメタデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="5995e-103">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5995e-104">構文</span><span class="sxs-lookup"><span data-stu-id="5995e-104">Syntax</span></span>  
  
```  
HRESULT GetGenericParamProps (  
   [in]  mdGenericParam  gp,  
   [out] ULONG           *pulParamSeq,  
   [out] DWORD           *pdwParamFlags,  
   [out] mdToken         *ptOwner,  
   [out] DWORD           *reserved,  
   [out] LPWSTR          wzName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5995e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5995e-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="5995e-106">[in]メタデータを返す対象のジェネリック パラメーターを表すトークンです。</span><span class="sxs-lookup"><span data-stu-id="5995e-106">[in] The token that represents the generic parameter for which to return metadata.</span></span>  
  
 `pulParamSeq`  
 <span data-ttu-id="5995e-107">[out]序数の位置、`Type`親コンス トラクターまたはメソッドのパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="5995e-107">[out] The ordinal position of the `Type` parameter in the parent constructor or method.</span></span>  
  
 `pdwParamFlags`  
 <span data-ttu-id="5995e-108">[out]値、 [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md)を表す列挙体、`Type`のジェネリック パラメーター。</span><span class="sxs-lookup"><span data-stu-id="5995e-108">[out] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the `Type` for the generic parameter.</span></span>  
  
 `ptOwner`  
 <span data-ttu-id="5995e-109">[out]パラメーターの所有者を表す TypeDef または MethodDef トークンです。</span><span class="sxs-lookup"><span data-stu-id="5995e-109">[out] A TypeDef or MethodDef token that represents the owner of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="5995e-110">[out]将来の機能拡張予約されています。</span><span class="sxs-lookup"><span data-stu-id="5995e-110">[out] Reserved for future extensibility.</span></span>  
  
 `wzName`  
 <span data-ttu-id="5995e-111">[out]ジェネリック パラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="5995e-111">[out] The name of the generic parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="5995e-112">[in]サイズ、`wzName`バッファー。</span><span class="sxs-lookup"><span data-stu-id="5995e-112">[in] The size of the `wzName` buffer.</span></span>  
  
 `pchName`  
 <span data-ttu-id="5995e-113">[out]ワイド文字で、名前の返されたサイズ。</span><span class="sxs-lookup"><span data-stu-id="5995e-113">[out] The returned size of the name, in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5995e-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="5995e-114">Requirements</span></span>  
 <span data-ttu-id="5995e-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5995e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5995e-116">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5995e-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5995e-117">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="5995e-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5995e-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5995e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5995e-119">参照</span><span class="sxs-lookup"><span data-stu-id="5995e-119">See Also</span></span>  
 [<span data-ttu-id="5995e-120">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5995e-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="5995e-121">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5995e-121">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
