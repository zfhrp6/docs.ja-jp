---
title: "EMemoryAvailable 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EMemoryAvailable
api_location: mscoree.dll
api_type: COM
f1_keywords: EMemoryAvailable
helpviewer_keywords: EMemoryAvailable enumeration [.NET Framework hosting]
ms.assetid: 38e72a06-dbed-473b-a59b-7e0b3ea4f2af
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c378f2cd9b033e578ff15472a10a6dc295ad6539
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ememoryavailable-enumeration"></a><span data-ttu-id="267e1-102">EMemoryAvailable 列挙型</span><span class="sxs-lookup"><span data-stu-id="267e1-102">EMemoryAvailable Enumeration</span></span>
<span data-ttu-id="267e1-103">コンピューター上の物理メモリの空き容量を示す値を含みます。</span><span class="sxs-lookup"><span data-stu-id="267e1-103">Contains values that indicate the amount of free physical memory on the computer.</span></span> <span data-ttu-id="267e1-104">これらの値論理的にマップする、イベントから返されるメモリの高値と安値の`CreateMemoryResourceNotification`Win32 API の関数。</span><span class="sxs-lookup"><span data-stu-id="267e1-104">These values logically map to the events for high and low memory returned from the `CreateMemoryResourceNotification` function in the Win32 API.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="267e1-105">構文</span><span class="sxs-lookup"><span data-stu-id="267e1-105">Syntax</span></span>  
  
```  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3   
} EMemoryAvailable;  
```  
  
## <a name="members"></a><span data-ttu-id="267e1-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="267e1-106">Members</span></span>  
  
|<span data-ttu-id="267e1-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="267e1-107">Member</span></span>|<span data-ttu-id="267e1-108">説明</span><span class="sxs-lookup"><span data-stu-id="267e1-108">Description</span></span>|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|<span data-ttu-id="267e1-109">十分な物理メモリは、使用できます。</span><span class="sxs-lookup"><span data-stu-id="267e1-109">Plenty of physical memory is available.</span></span>|  
|`eMemoryAvailableLow`|<span data-ttu-id="267e1-110">ほとんどの物理メモリは使用できます。</span><span class="sxs-lookup"><span data-stu-id="267e1-110">Very little physical memory is available.</span></span>|  
|`eMemoryAvailableNeutral`|<span data-ttu-id="267e1-111">使用可能な物理メモリは、ニュートラルです。</span><span class="sxs-lookup"><span data-stu-id="267e1-111">The available physical memory is neutral.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="267e1-112">コメント</span><span class="sxs-lookup"><span data-stu-id="267e1-112">Remarks</span></span>  
 <span data-ttu-id="267e1-113">呼び出しを使用して、共通言語ランタイム (CLR) によってホストによってこの値が渡される、 [iclrmemorynotificationcallback::onmemorynotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="267e1-113">This value is passed by the host to the common language runtime (CLR) by using a call to the [ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="267e1-114">要件</span><span class="sxs-lookup"><span data-stu-id="267e1-114">Requirements</span></span>  
 <span data-ttu-id="267e1-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="267e1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="267e1-116">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="267e1-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="267e1-117">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="267e1-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="267e1-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="267e1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="267e1-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="267e1-119">See Also</span></span>  
 [<span data-ttu-id="267e1-120">ホスティングの列挙体</span><span class="sxs-lookup"><span data-stu-id="267e1-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
