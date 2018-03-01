---
title: "IApartmentCallback::DoCallback メソッド"
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
- IApartmentCallback.DoCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- DoCallback
helpviewer_keywords:
- IApartmentCallback::DoCallback method [.NET Framework hosting]
- DoCallback method [.NET Framework hosting]
ms.assetid: 8edad30c-30ff-4bee-813c-75525a82fc93
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 06aaab6d4ad7d33bbdc52a38c999cc925eee1666
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iapartmentcallbackdocallback-method"></a><span data-ttu-id="d6ee7-102">IApartmentCallback::DoCallback メソッド</span><span class="sxs-lookup"><span data-stu-id="d6ee7-102">IApartmentCallback::DoCallback Method</span></span>
<span data-ttu-id="d6ee7-103">アパートメント内で指定された関数を実行します。</span><span class="sxs-lookup"><span data-stu-id="d6ee7-103">Executes the specified function within an apartment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6ee7-104">構文</span><span class="sxs-lookup"><span data-stu-id="d6ee7-104">Syntax</span></span>  
  
```  
HRESULT _stdcall DoCallback(  
    [in] SIZE_T pFunc,  
    [in] SIZE_T pData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6ee7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d6ee7-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="d6ee7-106">[in]アパートメント内で実行される関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="d6ee7-106">[in] A pointer to the function to be executed within the apartment.</span></span>  
  
 `pData`  
 <span data-ttu-id="d6ee7-107">[in]関数の引数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="d6ee7-107">[in] A pointer to the function's argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6ee7-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="d6ee7-108">Requirements</span></span>  
 <span data-ttu-id="d6ee7-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d6ee7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6ee7-110">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d6ee7-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d6ee7-111">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="d6ee7-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6ee7-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6ee7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6ee7-113">参照</span><span class="sxs-lookup"><span data-stu-id="d6ee7-113">See Also</span></span>  
 [<span data-ttu-id="d6ee7-114">IApartmentCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d6ee7-114">IApartmentCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)
