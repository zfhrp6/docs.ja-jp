---
title: ICLRTaskManager::SetLocale メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab6b13c6b7dba34f5ea82d05f483b36bf96aab1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="iclrtaskmanagersetlocale-method"></a><span data-ttu-id="0484b-102">ICLRTaskManager::SetLocale メソッド</span><span class="sxs-lookup"><span data-stu-id="0484b-102">ICLRTaskManager::SetLocale Method</span></span>
<span data-ttu-id="0484b-103">ホストが現在実行中のタスクのロケール識別子 (地理的なカルチャや言語にマップする) の値を変更したことを共通言語ランタイム (CLR) に通知します。</span><span class="sxs-lookup"><span data-stu-id="0484b-103">Notifies the common language runtime (CLR) that the host has modified the value of the locale identifier (which maps to the geographical culture and language) on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0484b-104">構文</span><span class="sxs-lookup"><span data-stu-id="0484b-104">Syntax</span></span>  
  
```  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0484b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0484b-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="0484b-106">[in]新しく割り当てられた地理的なカルチャや言語にマップされるロケール識別子の値。</span><span class="sxs-lookup"><span data-stu-id="0484b-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0484b-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="0484b-107">Return Value</span></span>  
  
|<span data-ttu-id="0484b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0484b-108">HRESULT</span></span>|<span data-ttu-id="0484b-109">説明</span><span class="sxs-lookup"><span data-stu-id="0484b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0484b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0484b-110">S_OK</span></span>|<span data-ttu-id="0484b-111">メソッドが正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="0484b-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="0484b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0484b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0484b-113">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="0484b-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0484b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0484b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0484b-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="0484b-115">The call timed out.</span></span>|  
|<span data-ttu-id="0484b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0484b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0484b-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="0484b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0484b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0484b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0484b-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="0484b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0484b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0484b-120">E_FAIL</span></span>|<span data-ttu-id="0484b-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="0484b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0484b-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="0484b-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0484b-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="0484b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0484b-124">コメント</span><span class="sxs-lookup"><span data-stu-id="0484b-124">Remarks</span></span>  
 <span data-ttu-id="0484b-125">`SetLocale` ホスト、ロケールを同期するための任意の機構いる可能性がありますを実行できます。</span><span class="sxs-lookup"><span data-stu-id="0484b-125">`SetLocale` gives the host an opportunity to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0484b-126">要件</span><span class="sxs-lookup"><span data-stu-id="0484b-126">Requirements</span></span>  
 <span data-ttu-id="0484b-127">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0484b-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0484b-128">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0484b-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0484b-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="0484b-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0484b-130">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0484b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0484b-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="0484b-131">See Also</span></span>  
 [<span data-ttu-id="0484b-132">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0484b-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="0484b-133">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0484b-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="0484b-134">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0484b-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="0484b-135">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0484b-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
