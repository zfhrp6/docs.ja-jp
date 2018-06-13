---
title: IGCHost::SetVirtualMemLimit メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1d61c8aeaf458d8cbbd2976fa83aaa0eeb0f834
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437740"
---
# <a name="igchostsetvirtualmemlimit-method"></a><span data-ttu-id="35038-102">IGCHost::SetVirtualMemLimit メソッド</span><span class="sxs-lookup"><span data-stu-id="35038-102">IGCHost::SetVirtualMemLimit Method</span></span>
<span data-ttu-id="35038-103">ランタイムの仮想メモリの最大サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="35038-103">Sets the maximum size of the runtime's virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35038-104">構文</span><span class="sxs-lookup"><span data-stu-id="35038-104">Syntax</span></span>  
  
```  
HRESULT SetVirtualMemLimit (  
    [in] SIZE_T sztMaxVirtualMemMB  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="35038-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="35038-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="35038-106">[in]ランタイムの仮想メモリのメガバイト単位で最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="35038-106">[in] The maximum size, in megabytes, of the runtime's virtual memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35038-107">コメント</span><span class="sxs-lookup"><span data-stu-id="35038-107">Remarks</span></span>  
 <span data-ttu-id="35038-108">ランタイムの仮想メモリの最大サイズを動的に変更することができます。</span><span class="sxs-lookup"><span data-stu-id="35038-108">The maximum size of the runtime's virtual memory can be changed dynamically.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35038-109">要件</span><span class="sxs-lookup"><span data-stu-id="35038-109">Requirements</span></span>  
 <span data-ttu-id="35038-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="35038-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35038-111">**ヘッダー:** GCHost.idl、GCHost.h</span><span class="sxs-lookup"><span data-stu-id="35038-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="35038-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="35038-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="35038-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35038-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35038-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="35038-114">See Also</span></span>  
 [<span data-ttu-id="35038-115">IGCHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="35038-115">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
