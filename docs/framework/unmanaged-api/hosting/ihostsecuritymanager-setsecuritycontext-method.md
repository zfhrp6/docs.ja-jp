---
title: "IHostSecurityManager::SetSecurityContext メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager.SetSecurityContext
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager::SetSecurityContext
helpviewer_keywords:
- SetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::SetSecurityContext method [.NET Framework hosting]
ms.assetid: e4372384-ee69-48d7-97e0-8fab7866597a
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c25b8bb0effb4e5e1e61447c74c9729989d04702
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsecuritymanagersetsecuritycontext-method"></a><span data-ttu-id="627ea-102">IHostSecurityManager::SetSecurityContext メソッド</span><span class="sxs-lookup"><span data-stu-id="627ea-102">IHostSecurityManager::SetSecurityContext Method</span></span>
<span data-ttu-id="627ea-103">現在実行中のスレッドのセキュリティ コンテキストを設定します。</span><span class="sxs-lookup"><span data-stu-id="627ea-103">Sets the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="627ea-104">構文</span><span class="sxs-lookup"><span data-stu-id="627ea-104">Syntax</span></span>  
  
```  
HRESULT SetSecurityContext (  
    [in]  EContextType eContextType,  
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="627ea-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="627ea-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="627ea-106">[in]1 つ、 [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)値はホストに配置することは、共通言語ランタイム (CLR) のコンテキストの種類を示すです。</span><span class="sxs-lookup"><span data-stu-id="627ea-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of context the common language runtime (CLR) is placing on the host.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="627ea-107">[out]新しいアドレスへのポインター [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="627ea-107">[out] A pointer to the address of a new [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="627ea-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="627ea-108">Return Value</span></span>  
  
|<span data-ttu-id="627ea-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="627ea-109">HRESULT</span></span>|<span data-ttu-id="627ea-110">説明</span><span class="sxs-lookup"><span data-stu-id="627ea-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="627ea-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="627ea-111">S_OK</span></span>|<span data-ttu-id="627ea-112">`SetSecurityContext`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="627ea-112">`SetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="627ea-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="627ea-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="627ea-114">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="627ea-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="627ea-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="627ea-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="627ea-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="627ea-116">The call timed out.</span></span>|  
|<span data-ttu-id="627ea-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="627ea-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="627ea-118">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="627ea-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="627ea-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="627ea-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="627ea-120">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="627ea-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="627ea-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="627ea-121">E_FAIL</span></span>|<span data-ttu-id="627ea-122">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="627ea-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="627ea-123">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="627ea-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="627ea-124">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="627ea-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="627ea-125">コメント</span><span class="sxs-lookup"><span data-stu-id="627ea-125">Remarks</span></span>  
 <span data-ttu-id="627ea-126">CLR 呼び出し`SetSecurityContext`いくつかのシナリオでします。</span><span class="sxs-lookup"><span data-stu-id="627ea-126">The CLR calls `SetSecurityContext` in several scenarios.</span></span> <span data-ttu-id="627ea-127">クラスとモジュール コンス トラクターとファイナライザーを実行する前に、CLR は呼び出し`SetSecurityContext`実行の失敗からホストを保護します。</span><span class="sxs-lookup"><span data-stu-id="627ea-127">Before it executes class and module constructors and finalizers, the CLR calls `SetSecurityContext` to protect the host from execution failures.</span></span> <span data-ttu-id="627ea-128">リセットされますセキュリティ コンテキストを元の状態にコンス トラクターまたはファイナライザーの実行後に別の呼び出しを使用して`SetSecurityContext`です。</span><span class="sxs-lookup"><span data-stu-id="627ea-128">It then resets the security context to its original state after execution of the constructor or finalizer, by using another call to `SetSecurityContext`.</span></span> <span data-ttu-id="627ea-129">同様のパターンは、I/O 完了と発生します。</span><span class="sxs-lookup"><span data-stu-id="627ea-129">A similar pattern occurs with I/O completion.</span></span> <span data-ttu-id="627ea-130">ホストを実装する場合[IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)、CLR 呼び出し`SetSecurityContext`ホスト呼び出しの後に[iclriocompletionmanager::oncomplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="627ea-130">If the host implements [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md), the CLR calls `SetSecurityContext` after the host calls [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
 <span data-ttu-id="627ea-131">CLR は呼び出し、ワーカー スレッドで非同期ポイントで`SetSecurityContext`内<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType>内、または[ihostthreadpoolmanager::queueuserworkitem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)ホストか、CLR がスレッド プールを実装するかどうかに応じて、します。</span><span class="sxs-lookup"><span data-stu-id="627ea-131">At asynchronous points in worker threads, the CLR calls `SetSecurityContext` within <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> or within [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md), depending on whether the host or the CLR is implementing the thread pool.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="627ea-132">要件</span><span class="sxs-lookup"><span data-stu-id="627ea-132">Requirements</span></span>  
 <span data-ttu-id="627ea-133">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="627ea-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="627ea-134">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="627ea-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="627ea-135">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="627ea-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="627ea-136">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="627ea-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="627ea-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="627ea-137">See Also</span></span>  
 <xref:System.Threading.ThreadPool?displayProperty=nameWithType>  
 [<span data-ttu-id="627ea-138">EContextType 列挙型</span><span class="sxs-lookup"><span data-stu-id="627ea-138">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)  
 [<span data-ttu-id="627ea-139">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="627ea-139">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="627ea-140">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="627ea-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 [<span data-ttu-id="627ea-141">IHostSecurityContext インターフェイス</span><span class="sxs-lookup"><span data-stu-id="627ea-141">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="627ea-142">IHostSecurityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="627ea-142">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="627ea-143">IHostThreadPoolManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="627ea-143">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
