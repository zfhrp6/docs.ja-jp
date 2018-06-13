---
title: IHostTaskManager::EndThreadAffinity メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndThreadAffinity
helpviewer_keywords:
- EndThreadAffinity method [.NET Framework hosting]
- IHostTaskManager::EndThreadAffinity method [.NET Framework hosting]
ms.assetid: 7738a904-0cd7-4fde-a3eb-2323a5533157
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb07e38542893b26595b67d6cf0fa77c522b4def
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442814"
---
# <a name="ihosttaskmanagerendthreadaffinity-method"></a><span data-ttu-id="101e1-102">IHostTaskManager::EndThreadAffinity メソッド</span><span class="sxs-lookup"><span data-stu-id="101e1-102">IHostTaskManager::EndThreadAffinity Method</span></span>
<span data-ttu-id="101e1-103">マネージ コードをホストが終了する、現在のタスクを別のオペレーティング システム スレッドに移動できない期間を以前の呼び出しに通知[ihosttaskmanager::beginthreadaffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="101e1-103">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to [IHostTaskManager::BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="101e1-104">構文</span><span class="sxs-lookup"><span data-stu-id="101e1-104">Syntax</span></span>  
  
```  
HRESULT EndThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="101e1-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="101e1-105">Return Value</span></span>  
  
|<span data-ttu-id="101e1-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="101e1-106">HRESULT</span></span>|<span data-ttu-id="101e1-107">説明</span><span class="sxs-lookup"><span data-stu-id="101e1-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="101e1-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="101e1-108">S_OK</span></span>|<span data-ttu-id="101e1-109">`EndThreadAffinity` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="101e1-109">`EndThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="101e1-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="101e1-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="101e1-111">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="101e1-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="101e1-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="101e1-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="101e1-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="101e1-113">The call timed out.</span></span>|  
|<span data-ttu-id="101e1-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="101e1-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="101e1-115">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="101e1-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="101e1-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="101e1-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="101e1-117">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="101e1-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="101e1-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="101e1-118">E_FAIL</span></span>|<span data-ttu-id="101e1-119">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="101e1-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="101e1-120">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="101e1-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="101e1-121">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="101e1-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="101e1-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="101e1-122">E_UNEXPECTED</span></span>|<span data-ttu-id="101e1-123">`EndThreadAffinity` 対応する以前の呼び出しなしで呼び出されました`BeginThreadAffinity`です。</span><span class="sxs-lookup"><span data-stu-id="101e1-123">`EndThreadAffinity` was called without an earlier corresponding call to `BeginThreadAffinity`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="101e1-124">コメント</span><span class="sxs-lookup"><span data-stu-id="101e1-124">Remarks</span></span>  
 <span data-ttu-id="101e1-125">CLR は、対応する呼び出し`BeginThreadAffinity`呼び出す前に現在のタスクで`EndThreadAffinity`です。</span><span class="sxs-lookup"><span data-stu-id="101e1-125">The CLR makes a corresponding call to `BeginThreadAffinity` on the current task before calling `EndThreadAffinity`.</span></span> <span data-ttu-id="101e1-126">このような対応する呼び出しがない場合のホストの実装[IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) E_UNEXPECTED を返し、何もしない必要があります。</span><span class="sxs-lookup"><span data-stu-id="101e1-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) should return E_UNEXPECTED, and take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="101e1-127">要件</span><span class="sxs-lookup"><span data-stu-id="101e1-127">Requirements</span></span>  
 <span data-ttu-id="101e1-128">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="101e1-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="101e1-129">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="101e1-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="101e1-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="101e1-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="101e1-131">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="101e1-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="101e1-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="101e1-132">See Also</span></span>  
 <xref:System.Threading>  
 [<span data-ttu-id="101e1-133">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="101e1-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="101e1-134">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="101e1-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="101e1-135">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="101e1-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="101e1-136">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="101e1-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
