---
title: "ICLRTask::Abort メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.Abort
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::Abort
helpviewer_keywords:
- ICLRTask::Abort method [.NET Framework hosting]
- Abort method, ICLRTask interface [.NET Framework hosting]
ms.assetid: b3594b5f-2e41-4e36-9096-3586276a138c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e789afc8f570d647fd44f8f43c23c2cc33ba8f70
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtaskabort-method"></a><span data-ttu-id="64de8-102">ICLRTask::Abort メソッド</span><span class="sxs-lookup"><span data-stu-id="64de8-102">ICLRTask::Abort Method</span></span>
<span data-ttu-id="64de8-103">共通言語ランタイム (CLR) が、タスクを中止する要求を現在[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)インスタンスが表すです。</span><span class="sxs-lookup"><span data-stu-id="64de8-103">Requests that the common language runtime (CLR) abort the task that the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64de8-104">構文</span><span class="sxs-lookup"><span data-stu-id="64de8-104">Syntax</span></span>  
  
```  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="64de8-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="64de8-105">Return Value</span></span>  
  
|<span data-ttu-id="64de8-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="64de8-106">HRESULT</span></span>|<span data-ttu-id="64de8-107">説明</span><span class="sxs-lookup"><span data-stu-id="64de8-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="64de8-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="64de8-108">S_OK</span></span>|<span data-ttu-id="64de8-109">`Abort`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="64de8-109">`Abort` returned successfully.</span></span>|  
|<span data-ttu-id="64de8-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="64de8-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="64de8-111">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="64de8-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="64de8-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="64de8-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="64de8-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="64de8-113">The call timed out.</span></span>|  
|<span data-ttu-id="64de8-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="64de8-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="64de8-115">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="64de8-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="64de8-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="64de8-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="64de8-117">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="64de8-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="64de8-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="64de8-118">E_FAIL</span></span>|<span data-ttu-id="64de8-119">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="64de8-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="64de8-120">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="64de8-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="64de8-121">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="64de8-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64de8-122">コメント</span><span class="sxs-lookup"><span data-stu-id="64de8-122">Remarks</span></span>  
 <span data-ttu-id="64de8-123">CLR を発生させる、<xref:System.Threading.ThreadAbortException>ホストが呼び出したとき`Abort`です。</span><span class="sxs-lookup"><span data-stu-id="64de8-123">The CLR raises a <xref:System.Threading.ThreadAbortException> when the host calls `Abort`.</span></span> <span data-ttu-id="64de8-124">実行するには、ファイナライザーや例外処理機構などのユーザー コードを待たずに、例外情報が初期化された直後後を返します。</span><span class="sxs-lookup"><span data-stu-id="64de8-124">It returns immediately after the exception information is initialized, without waiting for user code, such as finalizers or exception handling mechanisms, to execute.</span></span> <span data-ttu-id="64de8-125">呼び出す`Abort`のためです。</span><span class="sxs-lookup"><span data-stu-id="64de8-125">Calls to `Abort` thus return quickly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64de8-126">要件</span><span class="sxs-lookup"><span data-stu-id="64de8-126">Requirements</span></span>  
 <span data-ttu-id="64de8-127">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="64de8-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64de8-128">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="64de8-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="64de8-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="64de8-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="64de8-130">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64de8-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64de8-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="64de8-131">See Also</span></span>  
 [<span data-ttu-id="64de8-132">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="64de8-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="64de8-133">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="64de8-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="64de8-134">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="64de8-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="64de8-135">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="64de8-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
