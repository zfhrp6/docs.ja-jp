---
title: "IMetaDataEmit::GetTokenFromTypeSpec メソッド"
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
- IMetaDataEmit.GetTokenFromTypeSpec
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetTokenFromTypeSpec
helpviewer_keywords:
- GetTokenFromTypeSpec method [.NET Framework metadata]
- IMetaDataEmit::GetTokenFromTypeSpec method [.NET Framework metadata]
ms.assetid: 7de6447a-a751-49d8-87e2-951cee77b536
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6acb9d340aa1dc8df5d0b9dc3b0c0dd9c159257e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitgettokenfromtypespec-method"></a><span data-ttu-id="d542f-102">IMetaDataEmit::GetTokenFromTypeSpec メソッド</span><span class="sxs-lookup"><span data-stu-id="d542f-102">IMetaDataEmit::GetTokenFromTypeSpec Method</span></span>
<span data-ttu-id="d542f-103">指定したメタデータ シグネチャを持つ型のメタデータ トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="d542f-103">Gets a metadata token for the type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d542f-104">構文</span><span class="sxs-lookup"><span data-stu-id="d542f-104">Syntax</span></span>  
  
```  
HRESULT GetTokenFromTypeSpec (   
    [in]  PCCOR_SIGNATURE       pvSig,   
    [in]  ULONG                 cbSig,   
    [out] mdTypeSpec            *ptypespec   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d542f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d542f-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="d542f-106">[in]定義されている署名します。</span><span class="sxs-lookup"><span data-stu-id="d542f-106">[in] The signature being defined.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="d542f-107">[in]内のバイト数`pvSig`です。</span><span class="sxs-lookup"><span data-stu-id="d542f-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `ptypespec`  
 <span data-ttu-id="d542f-108">[out]`mdTypeSpec`トークンが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="d542f-108">[out] The `mdTypeSpec` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d542f-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="d542f-109">Requirements</span></span>  
 <span data-ttu-id="d542f-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d542f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d542f-111">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d542f-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d542f-112">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="d542f-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d542f-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d542f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d542f-114">参照</span><span class="sxs-lookup"><span data-stu-id="d542f-114">See Also</span></span>  
 [<span data-ttu-id="d542f-115">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d542f-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="d542f-116">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d542f-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
