---
title: "ICLRTaskManager::SetLocale メソッド"
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
- ICLRTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: ed16bb7f-4206-43a8-b9e9-c5737b69e3af
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bbed6bff52d7ccad38eb45d12a31d08dc8b1b774
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskmanagersetlocale-method"></a><span data-ttu-id="3dd76-102">ICLRTaskManager::SetLocale メソッド</span><span class="sxs-lookup"><span data-stu-id="3dd76-102">ICLRTaskManager::SetLocale Method</span></span>
<span data-ttu-id="3dd76-103">ホストが現在実行中のタスクのロケール識別子 (地理的なカルチャや言語にマップする) の値を変更したことを共通言語ランタイム (CLR) に通知します。</span><span class="sxs-lookup"><span data-stu-id="3dd76-103">Notifies the common language runtime (CLR) that the host has modified the value of the locale identifier (which maps to the geographical culture and language) on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dd76-104">構文</span><span class="sxs-lookup"><span data-stu-id="3dd76-104">Syntax</span></span>  
  
```  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3dd76-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3dd76-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="3dd76-106">[in]新しく割り当てられた地理的なカルチャや言語にマップされるロケール識別子の値。</span><span class="sxs-lookup"><span data-stu-id="3dd76-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3dd76-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="3dd76-107">Return Value</span></span>  
  
|<span data-ttu-id="3dd76-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3dd76-108">HRESULT</span></span>|<span data-ttu-id="3dd76-109">説明</span><span class="sxs-lookup"><span data-stu-id="3dd76-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3dd76-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3dd76-110">S_OK</span></span>|<span data-ttu-id="3dd76-111">メソッドが正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="3dd76-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="3dd76-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3dd76-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3dd76-113">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="3dd76-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3dd76-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3dd76-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3dd76-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="3dd76-115">The call timed out.</span></span>|  
|<span data-ttu-id="3dd76-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3dd76-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3dd76-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="3dd76-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3dd76-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3dd76-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3dd76-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="3dd76-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3dd76-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3dd76-120">E_FAIL</span></span>|<span data-ttu-id="3dd76-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="3dd76-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3dd76-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="3dd76-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3dd76-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="3dd76-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3dd76-124">コメント</span><span class="sxs-lookup"><span data-stu-id="3dd76-124">Remarks</span></span>  
 <span data-ttu-id="3dd76-125">`SetLocale`ホスト、ロケールを同期するための任意の機構いる可能性がありますを実行できます。</span><span class="sxs-lookup"><span data-stu-id="3dd76-125">`SetLocale` gives the host an opportunity to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dd76-126">必要条件</span><span class="sxs-lookup"><span data-stu-id="3dd76-126">Requirements</span></span>  
 <span data-ttu-id="3dd76-127">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3dd76-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dd76-128">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3dd76-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3dd76-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="3dd76-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3dd76-130">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3dd76-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dd76-131">参照</span><span class="sxs-lookup"><span data-stu-id="3dd76-131">See Also</span></span>  
 [<span data-ttu-id="3dd76-132">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3dd76-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="3dd76-133">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3dd76-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="3dd76-134">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3dd76-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="3dd76-135">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3dd76-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
