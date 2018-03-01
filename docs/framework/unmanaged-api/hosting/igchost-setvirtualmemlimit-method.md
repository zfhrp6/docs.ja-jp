---
title: "IGCHost::SetVirtualMemLimit メソッド"
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
- IGCHost.SetVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetVirtualMemLimit
helpviewer_keywords:
- IGCHost::SetVirtualMemLimit method [.NET Framework hosting]
- SetVirtualMemLimit method [.NET Framework hosting]
ms.assetid: c7e7c2d0-e58c-4650-b40c-47b2be2cda45
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5fca9ee8473ed70ca5da3b5607d38f4123fd47e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="igchostsetvirtualmemlimit-method"></a><span data-ttu-id="d9d4f-102">IGCHost::SetVirtualMemLimit メソッド</span><span class="sxs-lookup"><span data-stu-id="d9d4f-102">IGCHost::SetVirtualMemLimit Method</span></span>
<span data-ttu-id="d9d4f-103">ランタイムの仮想メモリの最大サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="d9d4f-103">Sets the maximum size of the runtime's virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9d4f-104">構文</span><span class="sxs-lookup"><span data-stu-id="d9d4f-104">Syntax</span></span>  
  
```  
HRESULT SetVirtualMemLimit (  
    [in] SIZE_T sztMaxVirtualMemMB  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d9d4f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d9d4f-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="d9d4f-106">[in]ランタイムの仮想メモリのメガバイト単位で最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="d9d4f-106">[in] The maximum size, in megabytes, of the runtime's virtual memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9d4f-107">コメント</span><span class="sxs-lookup"><span data-stu-id="d9d4f-107">Remarks</span></span>  
 <span data-ttu-id="d9d4f-108">ランタイムの仮想メモリの最大サイズを動的に変更することができます。</span><span class="sxs-lookup"><span data-stu-id="d9d4f-108">The maximum size of the runtime's virtual memory can be changed dynamically.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9d4f-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="d9d4f-109">Requirements</span></span>  
 <span data-ttu-id="d9d4f-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d9d4f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9d4f-111">**ヘッダー:** GCHost.idl、GCHost.h</span><span class="sxs-lookup"><span data-stu-id="d9d4f-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="d9d4f-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="d9d4f-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9d4f-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9d4f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9d4f-114">参照</span><span class="sxs-lookup"><span data-stu-id="d9d4f-114">See Also</span></span>  
 [<span data-ttu-id="d9d4f-115">IGCHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d9d4f-115">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
