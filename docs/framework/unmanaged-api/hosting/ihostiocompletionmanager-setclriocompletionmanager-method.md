---
title: "IHostIoCompletionManager::SetCLRIoCompletionManager メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostIoCompletionManager.SetCLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager method [.NET Framework hosting]
- SetCLRIoCompletionManager method [.NET Framework hosting]
ms.assetid: 4254bb01-3a14-4f34-a3be-60ff1f5072b5
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4fde1045fd0f15e7255a163c1f1b041800e85921
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagersetclriocompletionmanager-method"></a><span data-ttu-id="f8ece-102">IHostIoCompletionManager::SetCLRIoCompletionManager メソッド</span><span class="sxs-lookup"><span data-stu-id="f8ece-102">IHostIoCompletionManager::SetCLRIoCompletionManager Method</span></span>
<span data-ttu-id="f8ece-103">により、ホストへのインターフェイス ポインターで、 [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)共通言語ランタイム (CLR) によって実装されているインスタンス。</span><span class="sxs-lookup"><span data-stu-id="f8ece-103">Provides the host with an interface pointer to the [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8ece-104">構文</span><span class="sxs-lookup"><span data-stu-id="f8ece-104">Syntax</span></span>  
  
```  
HRESULT SetCLRIoCompletionManager (  
    [in] ICLRIoCompletionManager *pManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f8ece-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f8ece-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="f8ece-106">[in]インターフェイス ポインター、 `ICLRIoCompletionManager` CLR によって指定されたインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="f8ece-106">[in] An interface pointer to an `ICLRIoCompletionManager` instance provided by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f8ece-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="f8ece-107">Return Value</span></span>  
  
|<span data-ttu-id="f8ece-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f8ece-108">HRESULT</span></span>|<span data-ttu-id="f8ece-109">説明</span><span class="sxs-lookup"><span data-stu-id="f8ece-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f8ece-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f8ece-110">S_OK</span></span>|<span data-ttu-id="f8ece-111">`SetCLRIoCompletionManager`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="f8ece-111">`SetCLRIoCompletionManager` returned successfully.</span></span>|  
|<span data-ttu-id="f8ece-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f8ece-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f8ece-113">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="f8ece-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f8ece-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f8ece-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f8ece-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="f8ece-115">The call timed out.</span></span>|  
|<span data-ttu-id="f8ece-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f8ece-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f8ece-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="f8ece-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f8ece-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f8ece-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f8ece-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="f8ece-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f8ece-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f8ece-120">E_FAIL</span></span>|<span data-ttu-id="f8ece-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="f8ece-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f8ece-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="f8ece-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f8ece-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="f8ece-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8ece-124">コメント</span><span class="sxs-lookup"><span data-stu-id="f8ece-124">Remarks</span></span>  
 <span data-ttu-id="f8ece-125">CLR が呼び出された後に`SetCLRIoCompletionManager`、ホストを呼び出す必要があります[iclriocompletionmanager::oncomplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)が I/O 要求が完了したときに CLR に通知します。</span><span class="sxs-lookup"><span data-stu-id="f8ece-125">After the CLR has called `SetCLRIoCompletionManager`, the host must call [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) to notify the CLR when an I/O request has been completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8ece-126">必要条件</span><span class="sxs-lookup"><span data-stu-id="f8ece-126">Requirements</span></span>  
 <span data-ttu-id="f8ece-127">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f8ece-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8ece-128">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f8ece-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f8ece-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="f8ece-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f8ece-130">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8ece-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8ece-131">参照</span><span class="sxs-lookup"><span data-stu-id="f8ece-131">See Also</span></span>  
 [<span data-ttu-id="f8ece-132">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f8ece-132">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="f8ece-133">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f8ece-133">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
