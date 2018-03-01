---
title: "EMemoryAvailable 列挙型"
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
- EMemoryAvailable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryAvailable
helpviewer_keywords:
- EMemoryAvailable enumeration [.NET Framework hosting]
ms.assetid: 38e72a06-dbed-473b-a59b-7e0b3ea4f2af
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 596b174fa4ebac7e54e2f6b5f3ed044686fa515f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="b170d-102">EMemoryAvailable 列挙型</span><span class="sxs-lookup"><span data-stu-id="b170d-102">EMemoryAvailable Enumeration</span></span>
<span data-ttu-id="b170d-103">コンピューター上の物理メモリの空き容量を示す値を含みます。</span><span class="sxs-lookup"><span data-stu-id="b170d-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="b170d-104">これらの値論理的にマップする、イベントから返されるメモリの高値と安値の`CreateMemoryResourceNotification`Win32 API の関数。</span><span class="sxs-lookup"><span data-stu-id="b170d-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Win32 API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b170d-105">構文</span><span class="sxs-lookup"><span data-stu-id="b170d-105">Syntax</span></span>  
  
```  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3   
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="b170d-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="b170d-106">Members</span></span>  
  
|<span data-ttu-id="b170d-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="b170d-107">Member</span></span>|<span data-ttu-id="b170d-108">説明</span><span class="sxs-lookup"><span data-stu-id="b170d-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="b170d-109">十分な物理メモリは、使用できます。</span><span class="sxs-lookup"><span data-stu-id="b170d-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="b170d-110">ほとんどの物理メモリは使用できます。</span><span class="sxs-lookup"><span data-stu-id="b170d-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="b170d-111">使用可能な物理メモリは、ニュートラルです。</span><span class="sxs-lookup"><span data-stu-id="b170d-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b170d-112">コメント</span><span class="sxs-lookup"><span data-stu-id="b170d-112">Remarks</span></span>  
 <span data-ttu-id="b170d-113">呼び出しを使用して、共通言語ランタイム (CLR) によってホストによってこの値が渡される、 [iclrmemorynotificationcallback::onmemorynotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="b170d-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b170d-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="b170d-114">Requirements</span></span>  
 <span data-ttu-id="b170d-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b170d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b170d-116">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b170d-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b170d-117">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b170d-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b170d-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b170d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b170d-119">参照</span><span class="sxs-lookup"><span data-stu-id="b170d-119">See Also</span></span>  
 [<span data-ttu-id="b170d-120">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="b170d-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
