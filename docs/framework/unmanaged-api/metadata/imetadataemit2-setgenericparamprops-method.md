---
title: "IMetaDataEmit2::SetGenericParamProps メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit2.SetGenericParamProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit2::SetGenericParamProps
helpviewer_keywords:
- IMetaDataEmit2::SetGenericParamProps method [.NET Framework metadata]
- SetGenericParamProps method [.NET Framework metadata]
ms.assetid: cd93a48d-1fed-4706-bec6-a05dc3b64fbd
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e8e0720934fa9d7ec3669fa1cef7ac3ef9aedaa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemit2setgenericparamprops-method"></a><span data-ttu-id="66df5-102">IMetaDataEmit2::SetGenericParamProps メソッド</span><span class="sxs-lookup"><span data-stu-id="66df5-102">IMetaDataEmit2::SetGenericParamProps Method</span></span>
<span data-ttu-id="66df5-103">指定したトークンによって参照されるジェネリック パラメーターの定義のプロパティの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="66df5-103">Sets property values for the generic parameter definition referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66df5-104">構文</span><span class="sxs-lookup"><span data-stu-id="66df5-104">Syntax</span></span>  
  
```  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,   
    [in] DWORD            dwParamFlags,   
    [in] LPCWSTR          szName,   
    [in] DWORD            reserved,   
    [in] mdToken          rtkConstraints[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="66df5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="66df5-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="66df5-106">[in]定義については、ジェネリック パラメーターの値を設定する対象のトークンです。</span><span class="sxs-lookup"><span data-stu-id="66df5-106">[in] The token for the generic parameter definition for which to set values.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="66df5-107">[in]値、 [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md)ジェネリック パラメーターの型を表す列挙体です。</span><span class="sxs-lookup"><span data-stu-id="66df5-107">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="66df5-108">[in] オプション。</span><span class="sxs-lookup"><span data-stu-id="66df5-108">[in] Optional.</span></span> <span data-ttu-id="66df5-109">値を設定する対象のパラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="66df5-109">The name of the parameter for which to set values.</span></span>  
  
 `reserved`  
 <span data-ttu-id="66df5-110">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="66df5-110">[in] Reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="66df5-111">[in] オプション。</span><span class="sxs-lookup"><span data-stu-id="66df5-111">[in] Optional.</span></span> <span data-ttu-id="66df5-112">型の制約 0 で終わる配列。</span><span class="sxs-lookup"><span data-stu-id="66df5-112">A zero-terminated array of type constraints.</span></span> <span data-ttu-id="66df5-113">配列のメンバーである必要があります、 `mdTypeDef`、 `mdTypeRef`、または`mdTypeSpec`メタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="66df5-113">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66df5-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="66df5-114">Requirements</span></span>  
 <span data-ttu-id="66df5-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="66df5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66df5-116">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="66df5-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="66df5-117">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="66df5-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="66df5-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66df5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66df5-119">参照</span><span class="sxs-lookup"><span data-stu-id="66df5-119">See Also</span></span>  
 [<span data-ttu-id="66df5-120">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="66df5-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="66df5-121">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="66df5-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
