---
title: "IMetaDataEmit::SetMethodImplFlags メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetMethodImplFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetMethodImplFlags
helpviewer_keywords:
- IMetaDataEmit::SetMethodImplFlags method [.NET Framework metadata]
- SetMethodImpFlags method [.NET Framework metadata]
ms.assetid: 4bc82d9b-9544-4be3-ba51-a2d4d806158a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8026ec666e853b5a0ccd98e5ba75a3e04ffea9a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsetmethodimplflags-method"></a><span data-ttu-id="6ac2e-102">IMetaDataEmit::SetMethodImplFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="6ac2e-102">IMetaDataEmit::SetMethodImplFlags Method</span></span>
<span data-ttu-id="6ac2e-103">設定または指定したトークンによって参照されている継承されたメソッドの実装のメタデータ シグネチャを更新します。</span><span class="sxs-lookup"><span data-stu-id="6ac2e-103">Sets or updates the metadata signature of the inherited method implementation that is referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ac2e-104">構文</span><span class="sxs-lookup"><span data-stu-id="6ac2e-104">Syntax</span></span>  
  
```  
HRESULT SetMethodImplFlags (   
    [in]  mdMethodDef   md,   
    [in]  DWORD         dwImplFlags   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6ac2e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6ac2e-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="6ac2e-106">[in]変更するメソッドのトークン。</span><span class="sxs-lookup"><span data-stu-id="6ac2e-106">[in] The token for the method to be changed.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="6ac2e-107">[in]値の組み合わせ、 [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md)メソッド実装の機能を指定する列挙です。</span><span class="sxs-lookup"><span data-stu-id="6ac2e-107">[in] A combination of the values of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the method implementation features.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ac2e-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="6ac2e-108">Requirements</span></span>  
 <span data-ttu-id="6ac2e-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6ac2e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ac2e-110">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6ac2e-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6ac2e-111">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="6ac2e-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6ac2e-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ac2e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ac2e-113">参照</span><span class="sxs-lookup"><span data-stu-id="6ac2e-113">See Also</span></span>  
 [<span data-ttu-id="6ac2e-114">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6ac2e-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="6ac2e-115">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6ac2e-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
