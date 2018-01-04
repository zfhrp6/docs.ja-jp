---
title: "IHostTask::Alert メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask.Alert
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask::Alert
helpviewer_keywords:
- IHostTask::Alert method [.NET Framework hosting]
- Alert method, IHostTask interface [.NET Framework hosting]
ms.assetid: 5245d4b5-b6c3-48df-9cb9-8caf059f43fb
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 10dc8b9894c6f5444ccfcfd17f749df1a3fb5d05
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskalert-method"></a><span data-ttu-id="ef07c-102">IHostTask::Alert メソッド</span><span class="sxs-lookup"><span data-stu-id="ef07c-102">IHostTask::Alert Method</span></span>
<span data-ttu-id="ef07c-103">要求のホストが現在のタスクを wake [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)インスタンス、タスクを中止できるようにします。</span><span class="sxs-lookup"><span data-stu-id="ef07c-103">Requests that the host wake the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance, so the task can be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef07c-104">構文</span><span class="sxs-lookup"><span data-stu-id="ef07c-104">Syntax</span></span>  
  
```  
HRESULT Alert ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ef07c-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="ef07c-105">Return Value</span></span>  
  
|<span data-ttu-id="ef07c-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ef07c-106">HRESULT</span></span>|<span data-ttu-id="ef07c-107">説明</span><span class="sxs-lookup"><span data-stu-id="ef07c-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ef07c-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="ef07c-108">S_OK</span></span>|<span data-ttu-id="ef07c-109">メソッドが正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="ef07c-109">The method returned successfully.</span></span>|  
|<span data-ttu-id="ef07c-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ef07c-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ef07c-111">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="ef07c-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ef07c-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ef07c-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ef07c-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="ef07c-113">The call timed out.</span></span>|  
|<span data-ttu-id="ef07c-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ef07c-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ef07c-115">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="ef07c-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ef07c-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ef07c-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ef07c-117">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="ef07c-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ef07c-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ef07c-118">E_FAIL</span></span>|<span data-ttu-id="ef07c-119">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="ef07c-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ef07c-120">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="ef07c-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ef07c-121">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="ef07c-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef07c-122">コメント</span><span class="sxs-lookup"><span data-stu-id="ef07c-122">Remarks</span></span>  
 <span data-ttu-id="ef07c-123">CLR 呼び出し、`Alert`メソッドと<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>ユーザー コードから呼び出される場合や、<xref:System.AppDomain>に現在関連付けられている<xref:System.Threading.Thread>がシャット ダウンします。</span><span class="sxs-lookup"><span data-stu-id="ef07c-123">The CLR calls the `Alert` method when <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is called from user code, or when the <xref:System.AppDomain> associated with the current <xref:System.Threading.Thread> shuts down.</span></span> <span data-ttu-id="ef07c-124">ホストは、呼び出しが非同期に行われるので、すぐに返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef07c-124">The host must return immediately, because the call is made asynchronously.</span></span> <span data-ttu-id="ef07c-125">ホストは、タスクをすぐに警告ことはできません、次に、アラート、状態に入るときに復帰する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef07c-125">If the host cannot alert the task immediately, it must wake up the next time it enters a state in which it can be alerted.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef07c-126">`Alert`ランタイムが経過するタスクだけに影響を与える、 [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) WAIT_ALERTABLE の値などのメソッドを[参加](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="ef07c-126">`Alert` affects only those tasks to which the runtime has passed a [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) value of WAIT_ALERTABLE to methods such as [Join](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef07c-127">必要条件</span><span class="sxs-lookup"><span data-stu-id="ef07c-127">Requirements</span></span>  
 <span data-ttu-id="ef07c-128">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ef07c-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef07c-129">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ef07c-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ef07c-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="ef07c-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ef07c-131">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef07c-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef07c-132">参照</span><span class="sxs-lookup"><span data-stu-id="ef07c-132">See Also</span></span>  
 [<span data-ttu-id="ef07c-133">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ef07c-133">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="ef07c-134">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ef07c-134">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="ef07c-135">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ef07c-135">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="ef07c-136">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ef07c-136">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
