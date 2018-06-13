---
title: IMetaDataEmit::GetTokenFromTypeSpec メソッド
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b0b7d0364b6f58579ee8573d168d6c8180ac9dff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444578"
---
# <a name="imetadataemitgettokenfromtypespec-method"></a><span data-ttu-id="7a18c-102">IMetaDataEmit::GetTokenFromTypeSpec メソッド</span><span class="sxs-lookup"><span data-stu-id="7a18c-102">IMetaDataEmit::GetTokenFromTypeSpec Method</span></span>
<span data-ttu-id="7a18c-103">指定したメタデータ シグネチャを持つ型のメタデータ トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="7a18c-103">Gets a metadata token for the type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a18c-104">構文</span><span class="sxs-lookup"><span data-stu-id="7a18c-104">Syntax</span></span>  
  
```  
HRESULT GetTokenFromTypeSpec (   
    [in]  PCCOR_SIGNATURE       pvSig,   
    [in]  ULONG                 cbSig,   
    [out] mdTypeSpec            *ptypespec   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7a18c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7a18c-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="7a18c-106">[in]定義されている署名します。</span><span class="sxs-lookup"><span data-stu-id="7a18c-106">[in] The signature being defined.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="7a18c-107">[in]内のバイト数`pvSig`です。</span><span class="sxs-lookup"><span data-stu-id="7a18c-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `ptypespec`  
 <span data-ttu-id="7a18c-108">[out]`mdTypeSpec`トークンが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="7a18c-108">[out] The `mdTypeSpec` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a18c-109">要件</span><span class="sxs-lookup"><span data-stu-id="7a18c-109">Requirements</span></span>  
 <span data-ttu-id="7a18c-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7a18c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a18c-111">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7a18c-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7a18c-112">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="7a18c-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7a18c-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a18c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a18c-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="7a18c-114">See Also</span></span>  
 [<span data-ttu-id="7a18c-115">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7a18c-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="7a18c-116">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7a18c-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
