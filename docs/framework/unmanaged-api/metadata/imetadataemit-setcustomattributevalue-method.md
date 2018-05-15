---
title: IMetaDataEmit::SetCustomAttributeValue メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetCustomAttributeValue
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetCustomAttributeValue
helpviewer_keywords:
- SetCustomAttributeValue method [.NET Framework metadata]
- IMetaDataEmit::SetCustomAttributeValue method [.NET Framework metadata]
ms.assetid: f721c863-9642-4e64-917a-65f9e55c25b9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6b699539df52bda9206191dd89c0f95de69140a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitsetcustomattributevalue-method"></a><span data-ttu-id="14113-102">IMetaDataEmit::SetCustomAttributeValue メソッド</span><span class="sxs-lookup"><span data-stu-id="14113-102">IMetaDataEmit::SetCustomAttributeValue Method</span></span>
<span data-ttu-id="14113-103">設定または前回の呼び出しによって定義されたカスタム属性の値を更新[imetadataemit::definecustomattribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="14113-103">Sets or updates the value of a custom attribute defined by a prior call to [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14113-104">構文</span><span class="sxs-lookup"><span data-stu-id="14113-104">Syntax</span></span>  
  
```  
HRESULT SetCustomAttributeValue (   
    [in]  mdCustomAttribute       pcv,   
    [in]  void const              *pCustomAttribute,    
    [in]  ULONG                   cbCustomAttribute   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="14113-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="14113-105">Parameters</span></span>  
 `pcv`  
 <span data-ttu-id="14113-106">[in]対象のカスタム属性のトークンです。</span><span class="sxs-lookup"><span data-stu-id="14113-106">[in] The token of the target custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="14113-107">[in]カスタム属性を格納している配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="14113-107">[in] A pointer to the array that contains the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="14113-108">[in]カスタム属性のバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="14113-108">[in] The size, in bytes, of the custom attribute.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14113-109">要件</span><span class="sxs-lookup"><span data-stu-id="14113-109">Requirements</span></span>  
 <span data-ttu-id="14113-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="14113-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14113-111">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="14113-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="14113-112">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="14113-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="14113-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14113-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14113-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="14113-114">See Also</span></span>  
 [<span data-ttu-id="14113-115">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="14113-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="14113-116">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="14113-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
