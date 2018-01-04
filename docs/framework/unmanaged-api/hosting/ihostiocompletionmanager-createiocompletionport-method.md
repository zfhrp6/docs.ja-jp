---
title: "IHostIoCompletionManager::CreateIoCompletionPort メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.CreateIoCompletionPort
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::CreateIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CreateIoCompletionPort method [.NET Framework hosting]
- CreateIoCompletionPort method [.NET Framework hosting]
ms.assetid: 907a2b43-68db-44a7-acac-89e792e7bb3c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 230d6446460af92dbc4356977c0df4556d0229a0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagercreateiocompletionport-method"></a><span data-ttu-id="54378-102">IHostIoCompletionManager::CreateIoCompletionPort メソッド</span><span class="sxs-lookup"><span data-stu-id="54378-102">IHostIoCompletionManager::CreateIoCompletionPort Method</span></span>
<span data-ttu-id="54378-103">要求のホストが新しい I/O 完了ポートを作成することです。</span><span class="sxs-lookup"><span data-stu-id="54378-103">Requests that the host create a new I/O completion port.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54378-104">構文</span><span class="sxs-lookup"><span data-stu-id="54378-104">Syntax</span></span>  
  
```  
HRESULT CreateIoCompletionPort (  
    [out] HANDLE *phPort  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="54378-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="54378-105">Parameters</span></span>  
 `phPort`  
 <span data-ttu-id="54378-106">[out]0 (ゼロ)、ポートを作成できませんでしたが、新しく作成された I/O 完了ポートへのハンドルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="54378-106">[out] A pointer to a handle to the newly created I/O completion port, or 0 (zero), if the port could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="54378-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="54378-107">Return Value</span></span>  
  
|<span data-ttu-id="54378-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="54378-108">HRESULT</span></span>|<span data-ttu-id="54378-109">説明</span><span class="sxs-lookup"><span data-stu-id="54378-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="54378-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="54378-110">S_OK</span></span>|<span data-ttu-id="54378-111">`CreateIoCompletionPort`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="54378-111">`CreateIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="54378-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="54378-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="54378-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="54378-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="54378-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="54378-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="54378-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="54378-115">The call timed out.</span></span>|  
|<span data-ttu-id="54378-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="54378-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="54378-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="54378-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="54378-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="54378-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="54378-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="54378-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="54378-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="54378-120">E_FAIL</span></span>|<span data-ttu-id="54378-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="54378-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="54378-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="54378-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="54378-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="54378-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="54378-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="54378-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="54378-125">十分なメモリは、要求されたリソースを割り当てることができませんでした。</span><span class="sxs-lookup"><span data-stu-id="54378-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54378-126">コメント</span><span class="sxs-lookup"><span data-stu-id="54378-126">Remarks</span></span>  
 <span data-ttu-id="54378-127">CLR の呼び出し、`CreateIoCompletionPort`ホストが新しい I/O 完了ポートを作成することを要求するメソッド。</span><span class="sxs-lookup"><span data-stu-id="54378-127">The CLR calls the `CreateIoCompletionPort` method to request that the host create a new I/O completion port.</span></span> <span data-ttu-id="54378-128">I/O 操作を呼び出すことによって、このポートにバインドされて、 [ihostiocompletionmanager::bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="54378-128">It binds I/O operations to this port through a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span> <span data-ttu-id="54378-129">ホストの状態に報告、CLR を呼び出して[iclriocompletionmanager::oncomplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="54378-129">The host reports status back to the CLR by calling [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54378-130">必要条件</span><span class="sxs-lookup"><span data-stu-id="54378-130">Requirements</span></span>  
 <span data-ttu-id="54378-131">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="54378-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54378-132">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="54378-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="54378-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="54378-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="54378-134">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54378-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54378-135">参照</span><span class="sxs-lookup"><span data-stu-id="54378-135">See Also</span></span>  
 [<span data-ttu-id="54378-136">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="54378-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="54378-137">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="54378-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
