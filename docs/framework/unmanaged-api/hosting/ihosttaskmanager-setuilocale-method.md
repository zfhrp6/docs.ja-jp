---
title: IHostTaskManager::SetUILocale メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetUILocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetUILocale
helpviewer_keywords:
- SetUILocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetUILocale method [.NET Framework hosting]
ms.assetid: d0c87a9c-ea81-4237-a16b-c22b36ec9dc8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f929dceafc72af89cfd85b1617de7bbd0bc0dfff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="ihosttaskmanagersetuilocale-method"></a><span data-ttu-id="16bc7-102">IHostTaskManager::SetUILocale メソッド</span><span class="sxs-lookup"><span data-stu-id="16bc7-102">IHostTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="16bc7-103">ユーザー インターフェイス (UI) のロケール、または現在実行中のタスクで、カルチャ、共通言語ランタイム (CLR) が変更されたことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="16bc7-103">Notifies the host that the common language runtime (CLR) has changed the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16bc7-104">構文</span><span class="sxs-lookup"><span data-stu-id="16bc7-104">Syntax</span></span>  
  
```  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="16bc7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="16bc7-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="16bc7-106">[in]新しく割り当てられた地理的なカルチャや言語にマップされるロケール識別子の値。</span><span class="sxs-lookup"><span data-stu-id="16bc7-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="16bc7-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="16bc7-107">Return Value</span></span>  
  
|<span data-ttu-id="16bc7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="16bc7-108">HRESULT</span></span>|<span data-ttu-id="16bc7-109">説明</span><span class="sxs-lookup"><span data-stu-id="16bc7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="16bc7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="16bc7-110">S_OK</span></span>|<span data-ttu-id="16bc7-111">`SetUILocale` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="16bc7-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="16bc7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="16bc7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="16bc7-113">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="16bc7-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="16bc7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="16bc7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="16bc7-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="16bc7-115">The call timed out.</span></span>|  
|<span data-ttu-id="16bc7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="16bc7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="16bc7-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="16bc7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="16bc7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="16bc7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="16bc7-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="16bc7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="16bc7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="16bc7-120">E_FAIL</span></span>|<span data-ttu-id="16bc7-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="16bc7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="16bc7-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="16bc7-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="16bc7-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="16bc7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="16bc7-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="16bc7-124">E_NOTIMPL</span></span>|<span data-ttu-id="16bc7-125">ホストには、マネージ ユーザー コードの UI カルチャを変更するのにはできません。</span><span class="sxs-lookup"><span data-stu-id="16bc7-125">The host does not allow managed user code to change the UI culture.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16bc7-126">コメント</span><span class="sxs-lookup"><span data-stu-id="16bc7-126">Remarks</span></span>  
 <span data-ttu-id="16bc7-127">ランタイム呼び出し`SetUILocale`ときの値、<xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType>マネージ コードでプロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="16bc7-127">The runtime calls `SetUILocale` when the value of the <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="16bc7-128">このメソッドは、ロケールの同期のための任意の機構いる可能性がありますを実行するホストの機会を提供します。</span><span class="sxs-lookup"><span data-stu-id="16bc7-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="16bc7-129">ホストは、マネージ コードに変更する UI 言語を許可しないまたはロケールを同期するためのメカニズムを実装していません、このメソッドから E_NOTIMPL を返します。</span><span class="sxs-lookup"><span data-stu-id="16bc7-129">If a host does not allow the UI locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16bc7-130">要件</span><span class="sxs-lookup"><span data-stu-id="16bc7-130">Requirements</span></span>  
 <span data-ttu-id="16bc7-131">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="16bc7-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16bc7-132">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="16bc7-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="16bc7-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="16bc7-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="16bc7-134">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16bc7-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16bc7-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="16bc7-135">See Also</span></span>  
 [<span data-ttu-id="16bc7-136">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="16bc7-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="16bc7-137">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="16bc7-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="16bc7-138">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="16bc7-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="16bc7-139">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="16bc7-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="16bc7-140">SetLocale メソッド</span><span class="sxs-lookup"><span data-stu-id="16bc7-140">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)
