---
title: IMetaDataEmit::SetRVA メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetRVA
helpviewer_keywords:
- IMetaDataEmit::SetRVA method [.NET Framework metadata]
- SetRVA method [.NET Framework metadata]
ms.assetid: 4d69fb6d-ee35-4318-8224-5eea2bd16818
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 371eed84883e2816892c0a6a212a4a89a287cc58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitsetrva-method"></a><span data-ttu-id="5cedc-102">IMetaDataEmit::SetRVA メソッド</span><span class="sxs-lookup"><span data-stu-id="5cedc-102">IMetaDataEmit::SetRVA Method</span></span>
<span data-ttu-id="5cedc-103">指定したメソッドの相対仮想アドレスを設定します。</span><span class="sxs-lookup"><span data-stu-id="5cedc-103">Sets the relative virtual address of the specified method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cedc-104">構文</span><span class="sxs-lookup"><span data-stu-id="5cedc-104">Syntax</span></span>  
  
```  
HRESULT SetRVA (  
    [in]  mdMethodDef  md,   
    [in]  ULONG        ulRVA   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5cedc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5cedc-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="5cedc-106">[in]対象のメソッドまたはメソッドの実装のトークンです。</span><span class="sxs-lookup"><span data-stu-id="5cedc-106">[in] The token for the target method or method implementation.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="5cedc-107">[in]コードまたはデータ領域のアドレス。</span><span class="sxs-lookup"><span data-stu-id="5cedc-107">[in] The address of the code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cedc-108">要件</span><span class="sxs-lookup"><span data-stu-id="5cedc-108">Requirements</span></span>  
 <span data-ttu-id="5cedc-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5cedc-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cedc-110">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5cedc-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5cedc-111">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="5cedc-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5cedc-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cedc-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cedc-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="5cedc-113">See Also</span></span>  
 [<span data-ttu-id="5cedc-114">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5cedc-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="5cedc-115">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5cedc-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
