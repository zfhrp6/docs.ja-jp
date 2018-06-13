---
title: ICLRMemoryNotificationCallback インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback
helpviewer_keywords:
- ICLRMemoryNotificationCallback interface [.NET Framework hosting]
ms.assetid: 873639e2-4837-4568-83b3-4493e67e4174
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c5cf7e17989f3c083c7c4e52fa8cfc09c00bc7d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431520"
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="c1c83-102">ICLRMemoryNotificationCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c1c83-102">ICLRMemoryNotificationCallback Interface</span></span>
<span data-ttu-id="c1c83-103">ホストが、Win32 のような方法を使用してメモリ不足の状態を報告できるように`CreateMemoryResourceNotification`関数。</span><span class="sxs-lookup"><span data-stu-id="c1c83-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c1c83-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="c1c83-104">Methods</span></span>  
  
|<span data-ttu-id="c1c83-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="c1c83-105">Method</span></span>|<span data-ttu-id="c1c83-106">説明</span><span class="sxs-lookup"><span data-stu-id="c1c83-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c1c83-107">OnMemoryNotification メソッド</span><span class="sxs-lookup"><span data-stu-id="c1c83-107">OnMemoryNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="c1c83-108">コンピューター上のメモリ負荷の共通言語ランタイム (CLR) に通知します。</span><span class="sxs-lookup"><span data-stu-id="c1c83-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1c83-109">コメント</span><span class="sxs-lookup"><span data-stu-id="c1c83-109">Remarks</span></span>  
 <span data-ttu-id="c1c83-110">ホストを使用して、 `ICLRMemoryNotificationCallback` CLR がメモリ リソースを解放することを要求するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="c1c83-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1c83-111">要件</span><span class="sxs-lookup"><span data-stu-id="c1c83-111">Requirements</span></span>  
 <span data-ttu-id="c1c83-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c1c83-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1c83-113">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c1c83-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c1c83-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="c1c83-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c1c83-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1c83-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1c83-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="c1c83-116">See Also</span></span>  
 [<span data-ttu-id="c1c83-117">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c1c83-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="c1c83-118">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c1c83-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
