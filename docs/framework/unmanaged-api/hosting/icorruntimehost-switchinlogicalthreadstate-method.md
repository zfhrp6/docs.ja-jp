---
title: "ICorRuntimeHost::SwitchInLogicalThreadState メソッド"
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
- ICorRuntimeHost.SwitchInLogicalThreadState
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::SwitchInLogicalThreadState
helpviewer_keywords:
- ICorRuntimeHost::SwitchInLogicalThreadState method [.NET Framework hosting]
- SwitchInLogicalThreadState method [.NET Framework hosting]
ms.assetid: 7df1e492-8014-43ea-80d1-a4743e9b1c17
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 065a2347be2587265471d707988e90a01482c5a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostswitchinlogicalthreadstate-method"></a><span data-ttu-id="40486-102">ICorRuntimeHost::SwitchInLogicalThreadState メソッド</span><span class="sxs-lookup"><span data-stu-id="40486-102">ICorRuntimeHost::SwitchInLogicalThreadState Method</span></span>
<span data-ttu-id="40486-103">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="40486-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40486-104">構文</span><span class="sxs-lookup"><span data-stu-id="40486-104">Syntax</span></span>  
  
```  
HRESULT SwitchInLogicalThreadState(  
    [in] DWORD *pFiberCookie  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="40486-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="40486-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="40486-106">[in]使用するファイバーを示すクッキー。</span><span class="sxs-lookup"><span data-stu-id="40486-106">[in] Cookie that indicates the fiber to use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40486-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="40486-107">Requirements</span></span>  
 <span data-ttu-id="40486-108">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="40486-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40486-109">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="40486-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="40486-110">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="40486-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="40486-111">**.NET framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="40486-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40486-112">参照</span><span class="sxs-lookup"><span data-stu-id="40486-112">See Also</span></span>  
 [<span data-ttu-id="40486-113">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="40486-113">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
