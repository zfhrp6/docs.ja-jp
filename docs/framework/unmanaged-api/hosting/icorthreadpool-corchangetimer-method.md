---
title: "ICorThreadpool::CorChangeTimer メソッド"
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
- ICorThreadpool.CorChangeTimer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorChangeTimer
helpviewer_keywords:
- CorChangeTimer method [.NET Framework hosting]
- ICorThreadpool::CorChangeTimer method [.NET Framework hosting]
ms.assetid: 82b03a59-5a87-43ed-9b75-e04b256e1a46
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 004db96ac1d90403174641aecb5e7dda96509e9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorthreadpoolcorchangetimer-method"></a><span data-ttu-id="7ee4b-102">ICorThreadpool::CorChangeTimer メソッド</span><span class="sxs-lookup"><span data-stu-id="7ee4b-102">ICorThreadpool::CorChangeTimer Method</span></span>
<span data-ttu-id="7ee4b-103">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="7ee4b-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ee4b-104">構文</span><span class="sxs-lookup"><span data-stu-id="7ee4b-104">Syntax</span></span>  
  
```  
HRESULT CorChangeTimer (  
    [in]  HANDLE Timer,   
    [in]  ULONG  DueTime,   
    [in]  ULONG  Period,  
    [out] BOOL*  result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="7ee4b-105">必要条件</span><span class="sxs-lookup"><span data-stu-id="7ee4b-105">Requirements</span></span>  
 <span data-ttu-id="7ee4b-106">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7ee4b-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ee4b-107">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7ee4b-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7ee4b-108">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="7ee4b-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7ee4b-109">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ee4b-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ee4b-110">参照</span><span class="sxs-lookup"><span data-stu-id="7ee4b-110">See Also</span></span>  
 [<span data-ttu-id="7ee4b-111">ICorThreadpool インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7ee4b-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
