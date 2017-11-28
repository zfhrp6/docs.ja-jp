---
title: "ICLRTask::ExitTask メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.ExitTask
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::ExitTask
helpviewer_keywords:
- ExitTask method [.NET Framework hosting]
- ICLRTask::ExitTask method [.NET Framework hosting]
ms.assetid: 746c85a6-4b33-4f72-a2e9-379fdf2e96af
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4a954987e3a4c63827dafd5145ddb33aae22fa27
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtaskexittask-method"></a><span data-ttu-id="f4034-102">ICLRTask::ExitTask メソッド</span><span class="sxs-lookup"><span data-stu-id="f4034-102">ICLRTask::ExitTask Method</span></span>
<span data-ttu-id="f4034-103">現在のタスクが表す共通言語ランタイム (CLR) に通知[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)インスタンスが終了し、タスクを正常にシャット ダウンしようとしています。</span><span class="sxs-lookup"><span data-stu-id="f4034-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance is ending, and attempts to shut the task down gracefully.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4034-104">構文</span><span class="sxs-lookup"><span data-stu-id="f4034-104">Syntax</span></span>  
  
```  
HRESULT ExitTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f4034-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="f4034-105">Return Value</span></span>  
  
|<span data-ttu-id="f4034-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f4034-106">HRESULT</span></span>|<span data-ttu-id="f4034-107">説明</span><span class="sxs-lookup"><span data-stu-id="f4034-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f4034-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="f4034-108">S_OK</span></span>|<span data-ttu-id="f4034-109">`ExitTask`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="f4034-109">`ExitTask` returned successfully.</span></span>|  
|<span data-ttu-id="f4034-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f4034-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f4034-111">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="f4034-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f4034-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f4034-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f4034-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="f4034-113">The call timed out.</span></span>|  
|<span data-ttu-id="f4034-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f4034-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f4034-115">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="f4034-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f4034-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f4034-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f4034-117">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="f4034-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f4034-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f4034-118">E_FAIL</span></span>|<span data-ttu-id="f4034-119">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="f4034-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f4034-120">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="f4034-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f4034-121">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="f4034-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4034-122">コメント</span><span class="sxs-lookup"><span data-stu-id="f4034-122">Remarks</span></span>  
 <span data-ttu-id="f4034-123">`ExitTask`アンマネージ型ライブラリから、スレッドのデタッチとほぼ同じ方法で、タスクのクリーン シャット ダウンを試行します。</span><span class="sxs-lookup"><span data-stu-id="f4034-123">`ExitTask` attempts a clean shutdown of a task, in a manner analogous to detaching a thread from an unmanaged type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4034-124">要件</span><span class="sxs-lookup"><span data-stu-id="f4034-124">Requirements</span></span>  
 <span data-ttu-id="f4034-125">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f4034-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4034-126">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f4034-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f4034-127">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="f4034-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f4034-128">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4034-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4034-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="f4034-129">See Also</span></span>  
 [<span data-ttu-id="f4034-130">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f4034-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="f4034-131">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f4034-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="f4034-132">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f4034-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="f4034-133">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f4034-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
