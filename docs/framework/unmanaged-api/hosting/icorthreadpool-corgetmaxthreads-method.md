---
title: ICorThreadpool::CorGetMaxThreads メソッド
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorGetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGetMaxThreads
helpviewer_keywords:
- CorGetMaxThreads method [.NET Framework hosting]
- ICorThreadpool::CorGetMaxThreads method [.NET Framework hosting]
ms.assetid: 2861533a-cda0-47b3-b716-0d363505289b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c25f39cf64f462ac319803354e6a2a54ea482b9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436937"
---
# <a name="icorthreadpoolcorgetmaxthreads-method"></a><span data-ttu-id="5e886-102">ICorThreadpool::CorGetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="5e886-102">ICorThreadpool::CorGetMaxThreads Method</span></span>
<span data-ttu-id="5e886-103">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="5e886-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e886-104">構文</span><span class="sxs-lookup"><span data-stu-id="5e886-104">Syntax</span></span>  
  
```  
HRESULT CorGetMaxThreads (  
    [out] DWORD *MaxWorkerThreads,  
    [out] DWORD *MaxIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="5e886-105">要件</span><span class="sxs-lookup"><span data-stu-id="5e886-105">Requirements</span></span>  
 <span data-ttu-id="5e886-106">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5e886-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e886-107">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5e886-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5e886-108">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="5e886-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5e886-109">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e886-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e886-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="5e886-110">See Also</span></span>  
 [<span data-ttu-id="5e886-111">ICorThreadpool インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5e886-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
