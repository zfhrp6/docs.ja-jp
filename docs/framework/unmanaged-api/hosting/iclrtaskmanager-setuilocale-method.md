---
title: ICLRTaskManager::SetUILocale メソッド
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.SetUILocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::SetUILocale
helpviewer_keywords:
- ICLRTaskManager::SetUILocale method [.NET Framework hosting]
- SetUILocale method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 03adaa9a-2beb-49b3-b2c4-6b4fc3f10715
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1380864a66d904c26ece14899de78b1b5b7f0408
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437145"
---
# <a name="iclrtaskmanagersetuilocale-method"></a><span data-ttu-id="94ac2-102">ICLRTaskManager::SetUILocale メソッド</span><span class="sxs-lookup"><span data-stu-id="94ac2-102">ICLRTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="94ac2-103">現在実行中のタスクに共通言語ランタイム (CLR) ユーザー インターフェイス (UI) のロケール、または、カルチャ、ホストを変更したことを通知します。</span><span class="sxs-lookup"><span data-stu-id="94ac2-103">Notifies the common language runtime (CLR) that the host has modified the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94ac2-104">構文</span><span class="sxs-lookup"><span data-stu-id="94ac2-104">Syntax</span></span>  
  
```  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="94ac2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="94ac2-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="94ac2-106">[in]新しく割り当てられた地理的なカルチャおよび言語のユーザー インターフェイスにマップされるロケール識別子の値。</span><span class="sxs-lookup"><span data-stu-id="94ac2-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language for the user interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="94ac2-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="94ac2-107">Return Value</span></span>  
  
|<span data-ttu-id="94ac2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="94ac2-108">HRESULT</span></span>|<span data-ttu-id="94ac2-109">説明</span><span class="sxs-lookup"><span data-stu-id="94ac2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="94ac2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="94ac2-110">S_OK</span></span>|<span data-ttu-id="94ac2-111">`SetUILocale` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="94ac2-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="94ac2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="94ac2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="94ac2-113">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="94ac2-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="94ac2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="94ac2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="94ac2-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="94ac2-115">The call timed out.</span></span>|  
|<span data-ttu-id="94ac2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="94ac2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="94ac2-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="94ac2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="94ac2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="94ac2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="94ac2-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="94ac2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="94ac2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="94ac2-120">E_FAIL</span></span>|<span data-ttu-id="94ac2-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="94ac2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="94ac2-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="94ac2-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="94ac2-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="94ac2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94ac2-124">コメント</span><span class="sxs-lookup"><span data-stu-id="94ac2-124">Remarks</span></span>  
 <span data-ttu-id="94ac2-125">`SetUILocale` ロケールを同期するための任意の機構いる可能性がありますを実行するホストの機会を提供します。</span><span class="sxs-lookup"><span data-stu-id="94ac2-125">`SetUILocale` provides an opportunity for the host to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94ac2-126">要件</span><span class="sxs-lookup"><span data-stu-id="94ac2-126">Requirements</span></span>  
 <span data-ttu-id="94ac2-127">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="94ac2-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94ac2-128">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="94ac2-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="94ac2-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="94ac2-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="94ac2-130">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94ac2-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94ac2-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="94ac2-131">See Also</span></span>  
 [<span data-ttu-id="94ac2-132">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="94ac2-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="94ac2-133">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="94ac2-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="94ac2-134">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="94ac2-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="94ac2-135">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="94ac2-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
