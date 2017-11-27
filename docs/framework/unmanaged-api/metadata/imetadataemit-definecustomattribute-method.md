---
title: "IMetaDataEmit::DefineCustomAttribute メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineCustomAttribute
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineCustomAttribute
helpviewer_keywords:
- DefineCustomAttribute method [.NET Framework metadata]
- IMetaDataEmit::DefineCustomAttribute method [.NET Framework metadata]
ms.assetid: 7dd14854-b756-4401-b167-88ca576dc8f0
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1c4c00480571b4160d7442aeafea088fe8d04ba6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="aac9e-102">IMetaDataEmit::DefineCustomAttribute メソッド</span><span class="sxs-lookup"><span data-stu-id="aac9e-102">IMetaDataEmit::DefineCustomAttribute Method</span></span>
<span data-ttu-id="aac9e-103">指定したオブジェクトにアタッチされている、指定したメタデータ シグネチャを持つカスタム属性の定義を作成し、そのカスタム属性定義トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="aac9e-103">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aac9e-104">構文</span><span class="sxs-lookup"><span data-stu-id="aac9e-104">Syntax</span></span>  
  
```  
HRESULT DefineCustomAttribute (   
    [in]  mdToken     tkObj,   
    [in]  mdToken     tkType,   
    [in]  void const  *pCustomAttribute,   
    [in]  ULONG       cbCustomAttribute,   
    [out] mdCustomAttribute *pcv   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aac9e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aac9e-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="aac9e-106">[in]所有者アイテムのトークンです。</span><span class="sxs-lookup"><span data-stu-id="aac9e-106">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="aac9e-107">[in]カスタム属性を識別するトークン。</span><span class="sxs-lookup"><span data-stu-id="aac9e-107">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="aac9e-108">[in]カスタム属性へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aac9e-108">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="aac9e-109">[in]内のバイト数`pCustomAttribute`です。</span><span class="sxs-lookup"><span data-stu-id="aac9e-109">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="aac9e-110">[out]`mdCustomAttribute`トークンが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="aac9e-110">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aac9e-111">要件</span><span class="sxs-lookup"><span data-stu-id="aac9e-111">Requirements</span></span>  
 <span data-ttu-id="aac9e-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="aac9e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aac9e-113">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="aac9e-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aac9e-114">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="aac9e-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aac9e-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aac9e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aac9e-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="aac9e-116">See Also</span></span>  
 [<span data-ttu-id="aac9e-117">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aac9e-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="aac9e-118">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aac9e-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
