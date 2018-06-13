---
title: ICorThreadpool::CorDeleteTimer メソッド
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorDeleteTimer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorDeleteTimer
helpviewer_keywords:
- ICorThreadpool::CorDeleteTimer method [.NET Framework hosting]
- CorDeleteTimer method [.NET Framework hosting]
ms.assetid: 74847c35-7ca1-466a-b750-b25e7b03d100
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6870af271f7169d9f0ad1bff99dffe4ea4cf3a62
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437223"
---
# <a name="icorthreadpoolcordeletetimer-method"></a><span data-ttu-id="a5d0a-102">ICorThreadpool::CorDeleteTimer メソッド</span><span class="sxs-lookup"><span data-stu-id="a5d0a-102">ICorThreadpool::CorDeleteTimer Method</span></span>
<span data-ttu-id="a5d0a-103">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="a5d0a-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5d0a-104">構文</span><span class="sxs-lookup"><span data-stu-id="a5d0a-104">Syntax</span></span>  
  
```  
HRESULT CorDeleteTimer (  
    [in]  HANDLE Timer,  
    [in]  HANDLE CompletionEvent,  
    [out] BOOL*  result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="a5d0a-105">要件</span><span class="sxs-lookup"><span data-stu-id="a5d0a-105">Requirements</span></span>  
 <span data-ttu-id="a5d0a-106">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a5d0a-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5d0a-107">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a5d0a-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a5d0a-108">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="a5d0a-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a5d0a-109">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5d0a-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5d0a-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="a5d0a-110">See Also</span></span>  
 [<span data-ttu-id="a5d0a-111">ICorThreadpool インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a5d0a-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
