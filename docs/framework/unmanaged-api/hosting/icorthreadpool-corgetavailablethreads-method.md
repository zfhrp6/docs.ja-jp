---
title: ICorThreadpool::CorGetAvailableThreads メソッド
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorGetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGetAvailableThreads
helpviewer_keywords:
- CorGetAvailableThreads method [.NET Framework hosting]
- ICorThreadpool::CorGetAvailableThreads method [.NET Framework hosting]
ms.assetid: 0b09b750-0b86-4ba4-9621-041857cfe8ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c4867760807af1bc16f7935923cc2b89c1bfba6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436895"
---
# <a name="icorthreadpoolcorgetavailablethreads-method"></a><span data-ttu-id="03df3-102">ICorThreadpool::CorGetAvailableThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="03df3-102">ICorThreadpool::CorGetAvailableThreads Method</span></span>
<span data-ttu-id="03df3-103">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="03df3-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03df3-104">構文</span><span class="sxs-lookup"><span data-stu-id="03df3-104">Syntax</span></span>  
  
```  
HRESULT CorGetAvailableThreads (  
    [out] DWORD *AvailableWorkerThreads,  
    [out] DWORD *AvailableIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="03df3-105">要件</span><span class="sxs-lookup"><span data-stu-id="03df3-105">Requirements</span></span>  
 <span data-ttu-id="03df3-106">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="03df3-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03df3-107">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="03df3-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="03df3-108">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="03df3-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="03df3-109">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03df3-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03df3-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="03df3-110">See Also</span></span>  
 [<span data-ttu-id="03df3-111">ICorThreadpool インターフェイス</span><span class="sxs-lookup"><span data-stu-id="03df3-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
