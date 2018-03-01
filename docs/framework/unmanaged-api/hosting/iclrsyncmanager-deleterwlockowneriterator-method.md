---
title: "ICLRSyncManager::DeleteRWLockOwnerIterator メソッド"
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
- ICLRSyncManager.DeleteRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator method [.NET Framework hosting]
- DeleteRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: fcfd340a-b7d6-44e4-8167-2c05b789d483
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dce6699dc625c5c867befe1bc2e307cfaea7719a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="d5b92-102">ICLRSyncManager::DeleteRWLockOwnerIterator メソッド</span><span class="sxs-lookup"><span data-stu-id="d5b92-102">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>
<span data-ttu-id="d5b92-103">共通言語ランタイム (CLR) がへの呼び出しによって作成された反復子を破棄することを要求[iclrsyncmanager::createrwlockowneriterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="d5b92-103">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5b92-104">構文</span><span class="sxs-lookup"><span data-stu-id="d5b92-104">Syntax</span></span>  
  
```  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d5b92-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d5b92-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="d5b92-106">[in]反復子への呼び出しを使用して作成された`CreateRWLockOwnerIterator`です。</span><span class="sxs-lookup"><span data-stu-id="d5b92-106">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5b92-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="d5b92-107">Return Value</span></span>  
  
|<span data-ttu-id="d5b92-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d5b92-108">HRESULT</span></span>|<span data-ttu-id="d5b92-109">説明</span><span class="sxs-lookup"><span data-stu-id="d5b92-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d5b92-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d5b92-110">S_OK</span></span>|<span data-ttu-id="d5b92-111">`DeleteRWLockOwnerIterator`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="d5b92-111">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="d5b92-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d5b92-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d5b92-113">CLR をプロセスに読み込まれていないか状態にあるには、マネージ コードを実行か、呼び出しを正常に処理ができません。</span><span class="sxs-lookup"><span data-stu-id="d5b92-113">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="d5b92-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d5b92-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d5b92-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="d5b92-115">The call timed out.</span></span>|  
|<span data-ttu-id="d5b92-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d5b92-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d5b92-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="d5b92-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d5b92-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d5b92-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d5b92-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="d5b92-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d5b92-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d5b92-120">E_FAIL</span></span>|<span data-ttu-id="d5b92-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="d5b92-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d5b92-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="d5b92-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d5b92-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="d5b92-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5b92-124">コメント</span><span class="sxs-lookup"><span data-stu-id="d5b92-124">Remarks</span></span>  
 <span data-ttu-id="d5b92-125">ホストは、このメソッドを呼び出すことができ、`CreateRWLockOwnerIterator`そのスレッディングの実装の同期を保つためです。</span><span class="sxs-lookup"><span data-stu-id="d5b92-125">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5b92-126">必要条件</span><span class="sxs-lookup"><span data-stu-id="d5b92-126">Requirements</span></span>  
 <span data-ttu-id="d5b92-127">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d5b92-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5b92-128">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d5b92-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d5b92-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="d5b92-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d5b92-130">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5b92-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5b92-131">参照</span><span class="sxs-lookup"><span data-stu-id="d5b92-131">See Also</span></span>  
 [<span data-ttu-id="d5b92-132">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d5b92-132">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="d5b92-133">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d5b92-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
