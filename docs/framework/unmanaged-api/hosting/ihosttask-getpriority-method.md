---
title: IHostTask::GetPriority メソッド
ms.date: 03/30/2017
api_name:
- IHostTask.GetPriority
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::GetPriority
helpviewer_keywords:
- GetPriority method [.NET Framework hosting]
- IHostTask::GetPriority method [.NET Framework hosting]
ms.assetid: 4b463cd6-77c1-4f9a-8518-346ad8fc4b70
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 317223b1ce42924fcd20c44f791b0a24836a3ff8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442190"
---
# <a name="ihosttaskgetpriority-method"></a><span data-ttu-id="85068-102">IHostTask::GetPriority メソッド</span><span class="sxs-lookup"><span data-stu-id="85068-102">IHostTask::GetPriority Method</span></span>
<span data-ttu-id="85068-103">現在で表されるタスクのスレッド優先度レベルを取得[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="85068-103">Gets the thread priority level of the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85068-104">構文</span><span class="sxs-lookup"><span data-stu-id="85068-104">Syntax</span></span>  
  
```  
HRESULT GetPriority (  
    [out] int *pPriority  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="85068-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="85068-105">Parameters</span></span>  
 `pPriority`  
 <span data-ttu-id="85068-106">[out]現在で表されるタスクのスレッドの優先順位を示す整数を指すポインター`IHostTask`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="85068-106">[out] A pointer to an integer that indicates the thread priority level of the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85068-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="85068-107">Return Value</span></span>  
  
|<span data-ttu-id="85068-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="85068-108">HRESULT</span></span>|<span data-ttu-id="85068-109">説明</span><span class="sxs-lookup"><span data-stu-id="85068-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="85068-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="85068-110">S_OK</span></span>|<span data-ttu-id="85068-111">`GetPriority` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="85068-111">`GetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="85068-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="85068-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="85068-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="85068-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="85068-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="85068-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="85068-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="85068-115">The call timed out.</span></span>|  
|<span data-ttu-id="85068-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="85068-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="85068-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="85068-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="85068-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="85068-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="85068-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="85068-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="85068-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="85068-120">E_FAIL</span></span>|<span data-ttu-id="85068-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="85068-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="85068-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="85068-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="85068-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="85068-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85068-124">コメント</span><span class="sxs-lookup"><span data-stu-id="85068-124">Remarks</span></span>  
 <span data-ttu-id="85068-125">によって Win32 スレッド優先度レベルの値が定義されている`SetThreadPriority`関数。</span><span class="sxs-lookup"><span data-stu-id="85068-125">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85068-126">要件</span><span class="sxs-lookup"><span data-stu-id="85068-126">Requirements</span></span>  
 <span data-ttu-id="85068-127">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="85068-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85068-128">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="85068-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="85068-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="85068-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="85068-130">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85068-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85068-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="85068-131">See Also</span></span>  
 [<span data-ttu-id="85068-132">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="85068-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="85068-133">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="85068-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="85068-134">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="85068-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="85068-135">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="85068-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
