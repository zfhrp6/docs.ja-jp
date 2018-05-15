---
title: ICorThreadpool::CorUnregisterWait メソッド
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorUnregisterWait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorUnregisterWait
helpviewer_keywords:
- CorUnregisterWait method [.NET Framework hosting]
- ICorThreadpool::CorUnregisterWait method [.NET Framework hosting]
ms.assetid: 42c933f1-30a8-4011-bdea-e117f3c3265e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c3c5d4425b4851bbc0dbf1d98a0e3eec40b87a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icorthreadpoolcorunregisterwait-method"></a><span data-ttu-id="66e5e-102">ICorThreadpool::CorUnregisterWait メソッド</span><span class="sxs-lookup"><span data-stu-id="66e5e-102">ICorThreadpool::CorUnregisterWait Method</span></span>
<span data-ttu-id="66e5e-103">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="66e5e-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66e5e-104">構文</span><span class="sxs-lookup"><span data-stu-id="66e5e-104">Syntax</span></span>  
  
```  
HRESULT CorUnregisterWait (  
    [in] HANDLE hWaitObject,  
    [in] HANDLE CompletionEvent,  
    [out] BOOL* result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="66e5e-105">要件</span><span class="sxs-lookup"><span data-stu-id="66e5e-105">Requirements</span></span>  
 <span data-ttu-id="66e5e-106">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="66e5e-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66e5e-107">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="66e5e-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="66e5e-108">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="66e5e-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="66e5e-109">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66e5e-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66e5e-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="66e5e-110">See Also</span></span>  
 [<span data-ttu-id="66e5e-111">ICorThreadpool インターフェイス</span><span class="sxs-lookup"><span data-stu-id="66e5e-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
