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
ms.workload: dotnet
ms.openlocfilehash: ff2adafa41ce68a824f6b01888c3565bf054c031
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskexittask-method"></a><span data-ttu-id="0a281-102">ICLRTask::ExitTask メソッド</span><span class="sxs-lookup"><span data-stu-id="0a281-102">ICLRTask::ExitTask Method</span></span>
<span data-ttu-id="0a281-103">現在のタスクが表す共通言語ランタイム (CLR) に通知[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)インスタンスが終了し、タスクを正常にシャット ダウンしようとしています。</span><span class="sxs-lookup"><span data-stu-id="0a281-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance is ending, and attempts to shut the task down gracefully.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a281-104">構文</span><span class="sxs-lookup"><span data-stu-id="0a281-104">Syntax</span></span>  
  
```  
HRESULT ExitTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="0a281-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="0a281-105">Return Value</span></span>  
  
|<span data-ttu-id="0a281-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0a281-106">HRESULT</span></span>|<span data-ttu-id="0a281-107">説明</span><span class="sxs-lookup"><span data-stu-id="0a281-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0a281-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="0a281-108">S_OK</span></span>|<span data-ttu-id="0a281-109">`ExitTask`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="0a281-109">`ExitTask` returned successfully.</span></span>|  
|<span data-ttu-id="0a281-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0a281-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0a281-111">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="0a281-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0a281-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0a281-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0a281-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="0a281-113">The call timed out.</span></span>|  
|<span data-ttu-id="0a281-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0a281-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0a281-115">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="0a281-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0a281-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0a281-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0a281-117">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="0a281-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0a281-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0a281-118">E_FAIL</span></span>|<span data-ttu-id="0a281-119">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="0a281-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0a281-120">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="0a281-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0a281-121">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="0a281-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a281-122">コメント</span><span class="sxs-lookup"><span data-stu-id="0a281-122">Remarks</span></span>  
 <span data-ttu-id="0a281-123">`ExitTask`アンマネージ型ライブラリから、スレッドのデタッチとほぼ同じ方法で、タスクのクリーン シャット ダウンを試行します。</span><span class="sxs-lookup"><span data-stu-id="0a281-123">`ExitTask` attempts a clean shutdown of a task, in a manner analogous to detaching a thread from an unmanaged type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a281-124">必要条件</span><span class="sxs-lookup"><span data-stu-id="0a281-124">Requirements</span></span>  
 <span data-ttu-id="0a281-125">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0a281-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a281-126">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0a281-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0a281-127">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="0a281-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0a281-128">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a281-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a281-129">参照</span><span class="sxs-lookup"><span data-stu-id="0a281-129">See Also</span></span>  
 [<span data-ttu-id="0a281-130">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0a281-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="0a281-131">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0a281-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="0a281-132">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0a281-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="0a281-133">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0a281-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
