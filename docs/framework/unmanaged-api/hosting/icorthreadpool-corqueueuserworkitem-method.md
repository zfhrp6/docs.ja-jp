---
title: ICorThreadpool::CorQueueUserWorkItem メソッド
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorQueueUserWorkItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorQueueUserWorkItem
helpviewer_keywords:
- ICorThreadpool::CorQueueUserWorkItem method [.NET Framework hosting]
- CorQueueUserWorkItem method [.NET Framework hosting]
ms.assetid: 29ac7898-a7c7-433e-8f79-cd5237e0bab8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eae9180ddf05cbeae8ddfea600f0cc0aeef54d55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icorthreadpoolcorqueueuserworkitem-method"></a><span data-ttu-id="1f6af-102">ICorThreadpool::CorQueueUserWorkItem メソッド</span><span class="sxs-lookup"><span data-stu-id="1f6af-102">ICorThreadpool::CorQueueUserWorkItem Method</span></span>
<span data-ttu-id="1f6af-103">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="1f6af-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f6af-104">構文</span><span class="sxs-lookup"><span data-stu-id="1f6af-104">Syntax</span></span>  
  
```  
HRESULT CorQueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID                  Context,  
    [in] BOOL                   executeOnlyOnce,  
    [out] BOOL*                 result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="1f6af-105">要件</span><span class="sxs-lookup"><span data-stu-id="1f6af-105">Requirements</span></span>  
 <span data-ttu-id="1f6af-106">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1f6af-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f6af-107">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1f6af-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1f6af-108">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="1f6af-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1f6af-109">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f6af-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f6af-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="1f6af-110">See Also</span></span>  
 [<span data-ttu-id="1f6af-111">ICorThreadpool インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1f6af-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
