---
title: ICLRTaskManager::GetCurrentTask メソッド
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: c0b82a9f-edc6-4878-9c81-48de53c02142
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d447bd9712fc925cd738bd0c530d8329f510a5f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437379"
---
# <a name="iclrtaskmanagergetcurrenttask-method"></a><span data-ttu-id="51ca9-102">ICLRTaskManager::GetCurrentTask メソッド</span><span class="sxs-lookup"><span data-stu-id="51ca9-102">ICLRTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="51ca9-103">取得、 [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)メソッドの呼び出しの発生元となるオペレーティング システムのスレッドで現在実行されているインスタンス。</span><span class="sxs-lookup"><span data-stu-id="51ca9-103">Gets the [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance that is currently running on the operating system thread from which the method call originated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51ca9-104">構文</span><span class="sxs-lookup"><span data-stu-id="51ca9-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTask (  
    [out] ICLRTask **ppTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="51ca9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="51ca9-105">Parameters</span></span>  
 `ppTask`  
 <span data-ttu-id="51ca9-106">[out]アドレスへのポインター、`ICLRTask`呼び出し元である、オペレーティング システムのスレッドで現在実行中のインスタンスまたはこのスレッドで現在実行しているタスクがなくなる場合は null です。</span><span class="sxs-lookup"><span data-stu-id="51ca9-106">[out] A pointer to the address of an `ICLRTask` instance that is currently executing on the operating system thread from which the call originated, or null if no task is currently executing on this thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="51ca9-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="51ca9-107">Return Value</span></span>  
  
|<span data-ttu-id="51ca9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="51ca9-108">HRESULT</span></span>|<span data-ttu-id="51ca9-109">説明</span><span class="sxs-lookup"><span data-stu-id="51ca9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="51ca9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="51ca9-110">S_OK</span></span>|<span data-ttu-id="51ca9-111">メソッドが正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="51ca9-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="51ca9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="51ca9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="51ca9-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="51ca9-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="51ca9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="51ca9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="51ca9-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="51ca9-115">The call timed out.</span></span>|  
|<span data-ttu-id="51ca9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="51ca9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="51ca9-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="51ca9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="51ca9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="51ca9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="51ca9-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="51ca9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="51ca9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="51ca9-120">E_FAIL</span></span>|<span data-ttu-id="51ca9-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="51ca9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="51ca9-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="51ca9-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="51ca9-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="51ca9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51ca9-124">コメント</span><span class="sxs-lookup"><span data-stu-id="51ca9-124">Remarks</span></span>  
 <span data-ttu-id="51ca9-125">`ICLRTask`インスタンスが、`ppTask`パラメーターが指し示すは現在実行中のタスク、CLR のです。</span><span class="sxs-lookup"><span data-stu-id="51ca9-125">The `ICLRTask` instance that the `ppTask` parameter points to represents the currently executing task for the CLR.</span></span> <span data-ttu-id="51ca9-126">`ICLRTask`インスタンスが、対応する関連付け[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)タスクを表すホストのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="51ca9-126">The `ICLRTask` instance is associated with a corresponding [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the task for the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51ca9-127">要件</span><span class="sxs-lookup"><span data-stu-id="51ca9-127">Requirements</span></span>  
 <span data-ttu-id="51ca9-128">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="51ca9-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51ca9-129">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="51ca9-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="51ca9-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="51ca9-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="51ca9-131">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51ca9-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51ca9-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="51ca9-132">See Also</span></span>  
 [<span data-ttu-id="51ca9-133">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="51ca9-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="51ca9-134">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="51ca9-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="51ca9-135">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="51ca9-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="51ca9-136">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="51ca9-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
