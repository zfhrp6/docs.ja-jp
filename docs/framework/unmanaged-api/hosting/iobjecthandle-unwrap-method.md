---
title: "IObjectHandle::Unwrap メソッド"
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
- IObjectHandle.Unwrap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Unwrap
helpviewer_keywords:
- Unwrap method [.NET Framework hosting]
- IObjectHandle::Unwrap method [.NET Framework hosting]
ms.assetid: 794c6f8e-ed58-416b-b756-e864f2c958f7
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6b14483279e4416c898a836ae87c6bca180b4736
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iobjecthandleunwrap-method"></a><span data-ttu-id="b558e-102">IObjectHandle::Unwrap メソッド</span><span class="sxs-lookup"><span data-stu-id="b558e-102">IObjectHandle::Unwrap Method</span></span>
<span data-ttu-id="b558e-103">間接参照から値渡しでマーシャ リング オブジェクトがアンラップされます。</span><span class="sxs-lookup"><span data-stu-id="b558e-103">Unwraps a marshal-by-value object from indirection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b558e-104">構文</span><span class="sxs-lookup"><span data-stu-id="b558e-104">Syntax</span></span>  
  
```  
HRESULT Unwrap (  
    [out, retval] VARIANT *ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b558e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b558e-105">Parameters</span></span>  
 `ppv`  
 <span data-ttu-id="b558e-106">[out]ラップ解除するオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b558e-106">[out] A pointer to the object to be unwrapped.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b558e-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="b558e-107">Requirements</span></span>  
 <span data-ttu-id="b558e-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b558e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b558e-109">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b558e-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b558e-110">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="b558e-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b558e-111">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b558e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b558e-112">参照</span><span class="sxs-lookup"><span data-stu-id="b558e-112">See Also</span></span>  
 
