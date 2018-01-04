---
title: "ICLRMemoryNotificationCallback::OnMemoryNotification メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMemoryNotificationCallback.OnMemoryNotification
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMemoryNotificationCallback::OnMemoryNotification
helpviewer_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification method [.NET Framework hosting]
- OnMemoryNotification method [.NET Framework hosting]
ms.assetid: 5612a44d-56cc-4f34-af31-8c9809ba9431
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 651dcd6380702a392d2dd06cf899ea567b004ce1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmemorynotificationcallbackonmemorynotification-method"></a><span data-ttu-id="2b170-102">ICLRMemoryNotificationCallback::OnMemoryNotification メソッド</span><span class="sxs-lookup"><span data-stu-id="2b170-102">ICLRMemoryNotificationCallback::OnMemoryNotification Method</span></span>
<span data-ttu-id="2b170-103">コンピューター上のメモリ負荷の共通言語ランタイム (CLR) に通知します。</span><span class="sxs-lookup"><span data-stu-id="2b170-103">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b170-104">構文</span><span class="sxs-lookup"><span data-stu-id="2b170-104">Syntax</span></span>  
  
```  
HRESULT OnMemoryNotification (  
    [in] EMemoryAvailable eMemoryAvailable  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2b170-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2b170-105">Parameters</span></span>  
 `eMemoryAvailable`  
 <span data-ttu-id="2b170-106">[in]1 つ、 [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md)値、メモリ不足、コンピューターを示すが現在発生しています。</span><span class="sxs-lookup"><span data-stu-id="2b170-106">[in] One of the [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) values, indicating the memory pressure the computer is currently experiencing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b170-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="2b170-107">Return Value</span></span>  
  
|<span data-ttu-id="2b170-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2b170-108">HRESULT</span></span>|<span data-ttu-id="2b170-109">説明</span><span class="sxs-lookup"><span data-stu-id="2b170-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2b170-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2b170-110">S_OK</span></span>|<span data-ttu-id="2b170-111">`OnMemoryNotification`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="2b170-111">`OnMemoryNotification` returned successfully.</span></span>|  
|<span data-ttu-id="2b170-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2b170-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2b170-113">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="2b170-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2b170-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2b170-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2b170-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="2b170-115">The call timed out.</span></span>|  
|<span data-ttu-id="2b170-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2b170-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2b170-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="2b170-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2b170-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2b170-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2b170-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="2b170-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2b170-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2b170-120">E_FAIL</span></span>|<span data-ttu-id="2b170-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="2b170-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2b170-122">メソッドには、E_FAIL が返された、後に、CLR はプロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="2b170-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2b170-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="2b170-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b170-124">コメント</span><span class="sxs-lookup"><span data-stu-id="2b170-124">Remarks</span></span>  
 <span data-ttu-id="2b170-125">CLR がコールバックを登録`OnMemoryNotification`への呼び出しを使用して、 [ihostmemorymanager::registermemorynotificationcallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="2b170-125">The CLR registers a callback to `OnMemoryNotification` by using a call to the [IHostMemoryManager::RegisterMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) method.</span></span> <span data-ttu-id="2b170-126">ランタイムでは、コールバックに返される情報を使用して、ホストは、メモリがリソース不足していることを報告したときに、追加のメモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="2b170-126">The runtime uses the information returned in the callback to free additional memory when the host reports that memory resources are running low.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2b170-127">呼び出す`OnMemoryNotification`ブロックことはありません。</span><span class="sxs-lookup"><span data-stu-id="2b170-127">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="2b170-128">常に返すすぐにします。</span><span class="sxs-lookup"><span data-stu-id="2b170-128">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b170-129">必要条件</span><span class="sxs-lookup"><span data-stu-id="2b170-129">Requirements</span></span>  
 <span data-ttu-id="2b170-130">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2b170-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b170-131">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2b170-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2b170-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="2b170-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2b170-133">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b170-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b170-134">参照</span><span class="sxs-lookup"><span data-stu-id="2b170-134">See Also</span></span>  
 [<span data-ttu-id="2b170-135">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2b170-135">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="2b170-136">RegisterMemoryNotificationCallback メソッド</span><span class="sxs-lookup"><span data-stu-id="2b170-136">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)  
 [<span data-ttu-id="2b170-137">ICLRMemoryNotificationCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2b170-137">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
