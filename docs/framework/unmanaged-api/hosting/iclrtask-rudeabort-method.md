---
title: "ICLRTask::RudeAbort メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.RudeAbort
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::RudeAbort
helpviewer_keywords:
- RudeAbort method, ICLRTask interface [.NET Framework hosting]
- ICLRTask::RudeAbort method [.NET Framework hosting]
ms.assetid: b5785468-fcd7-4cc3-8a5d-8796337b53fc
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: df1f688ec3f58ae7317a4fed0dd70cffc1647045
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="8c12d-102">ICLRTask::RudeAbort メソッド</span><span class="sxs-lookup"><span data-stu-id="8c12d-102">ICLRTask::RudeAbort Method</span></span>
<span data-ttu-id="8c12d-103">共通言語ランタイム (CLR) を現在のタスクを中止するように指示[ICLRTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)インスタンス直ちにおよび無条件にします。</span><span class="sxs-lookup"><span data-stu-id="8c12d-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c12d-104">構文</span><span class="sxs-lookup"><span data-stu-id="8c12d-104">Syntax</span></span>  
  
```  
HRESULT RudeAbort ();   
```  
  
## <a name="return-value"></a><span data-ttu-id="8c12d-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="8c12d-105">Return Value</span></span>  
  
|<span data-ttu-id="8c12d-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8c12d-106">HRESULT</span></span>|<span data-ttu-id="8c12d-107">説明</span><span class="sxs-lookup"><span data-stu-id="8c12d-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8c12d-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="8c12d-108">S_OK</span></span>|<span data-ttu-id="8c12d-109">`RudeAbort`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="8c12d-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="8c12d-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8c12d-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8c12d-111">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="8c12d-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8c12d-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8c12d-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8c12d-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="8c12d-113">The call timed out.</span></span>|  
|<span data-ttu-id="8c12d-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8c12d-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8c12d-115">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="8c12d-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8c12d-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8c12d-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8c12d-117">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="8c12d-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8c12d-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8c12d-118">E_FAIL</span></span>|<span data-ttu-id="8c12d-119">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="8c12d-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8c12d-120">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="8c12d-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8c12d-121">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="8c12d-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c12d-122">コメント</span><span class="sxs-lookup"><span data-stu-id="8c12d-122">Remarks</span></span>  
 <span data-ttu-id="8c12d-123">ホストは`RudeAbort`タスクをすぐに中止します。</span><span class="sxs-lookup"><span data-stu-id="8c12d-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="8c12d-124">ファイナライザーおよび例外処理ルーチンは、実行される保証はありません。</span><span class="sxs-lookup"><span data-stu-id="8c12d-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c12d-125">要件</span><span class="sxs-lookup"><span data-stu-id="8c12d-125">Requirements</span></span>  
 <span data-ttu-id="8c12d-126">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8c12d-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c12d-127">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8c12d-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8c12d-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="8c12d-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c12d-129">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c12d-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c12d-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="8c12d-130">See Also</span></span>  
 [<span data-ttu-id="8c12d-131">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c12d-131">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="8c12d-132">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c12d-132">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="8c12d-133">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c12d-133">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="8c12d-134">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c12d-134">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
