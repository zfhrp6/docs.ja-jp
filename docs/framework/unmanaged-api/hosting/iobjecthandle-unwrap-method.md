---
title: IObjectHandle::Unwrap メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d9a8f9aa910054a4541e4ff8c1f7cad63077ba8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439951"
---
# <a name="iobjecthandleunwrap-method"></a><span data-ttu-id="d9b4b-102">IObjectHandle::Unwrap メソッド</span><span class="sxs-lookup"><span data-stu-id="d9b4b-102">IObjectHandle::Unwrap Method</span></span>
<span data-ttu-id="d9b4b-103">間接参照から値渡しでマーシャ リング オブジェクトがアンラップされます。</span><span class="sxs-lookup"><span data-stu-id="d9b4b-103">Unwraps a marshal-by-value object from indirection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9b4b-104">構文</span><span class="sxs-lookup"><span data-stu-id="d9b4b-104">Syntax</span></span>  
  
```  
HRESULT Unwrap (  
    [out, retval] VARIANT *ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d9b4b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d9b4b-105">Parameters</span></span>  
 `ppv`  
 <span data-ttu-id="d9b4b-106">[out]ラップ解除するオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d9b4b-106">[out] A pointer to the object to be unwrapped.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9b4b-107">要件</span><span class="sxs-lookup"><span data-stu-id="d9b4b-107">Requirements</span></span>  
 <span data-ttu-id="d9b4b-108">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d9b4b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9b4b-109">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d9b4b-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d9b4b-110">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="d9b4b-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9b4b-111">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9b4b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9b4b-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="d9b4b-112">See Also</span></span>  
 
