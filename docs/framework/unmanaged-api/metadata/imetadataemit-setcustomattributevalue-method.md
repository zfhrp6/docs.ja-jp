---
title: "IMetaDataEmit::SetCustomAttributeValue メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetCustomAttributeValue
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetCustomAttributeValue
helpviewer_keywords:
- SetCustomAttributeValue method [.NET Framework metadata]
- IMetaDataEmit::SetCustomAttributeValue method [.NET Framework metadata]
ms.assetid: f721c863-9642-4e64-917a-65f9e55c25b9
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6900fe9edd8c551952691ab02042e5172a39d626
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsetcustomattributevalue-method"></a><span data-ttu-id="cf5e0-102">IMetaDataEmit::SetCustomAttributeValue メソッド</span><span class="sxs-lookup"><span data-stu-id="cf5e0-102">IMetaDataEmit::SetCustomAttributeValue Method</span></span>
<span data-ttu-id="cf5e0-103">設定または前回の呼び出しによって定義されたカスタム属性の値を更新[imetadataemit::definecustomattribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="cf5e0-103">Sets or updates the value of a custom attribute defined by a prior call to [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf5e0-104">構文</span><span class="sxs-lookup"><span data-stu-id="cf5e0-104">Syntax</span></span>  
  
```  
HRESULT SetCustomAttributeValue (   
    [in]  mdCustomAttribute       pcv,   
    [in]  void const              *pCustomAttribute,    
    [in]  ULONG                   cbCustomAttribute   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cf5e0-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cf5e0-105">Parameters</span></span>  
 `pcv`  
 <span data-ttu-id="cf5e0-106">[in]対象のカスタム属性のトークンです。</span><span class="sxs-lookup"><span data-stu-id="cf5e0-106">[in] The token of the target custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="cf5e0-107">[in]カスタム属性を格納している配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="cf5e0-107">[in] A pointer to the array that contains the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="cf5e0-108">[in]カスタム属性のバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="cf5e0-108">[in] The size, in bytes, of the custom attribute.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf5e0-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="cf5e0-109">Requirements</span></span>  
 <span data-ttu-id="cf5e0-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cf5e0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf5e0-111">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cf5e0-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cf5e0-112">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="cf5e0-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf5e0-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf5e0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf5e0-114">参照</span><span class="sxs-lookup"><span data-stu-id="cf5e0-114">See Also</span></span>  
 [<span data-ttu-id="cf5e0-115">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cf5e0-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="cf5e0-116">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cf5e0-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
