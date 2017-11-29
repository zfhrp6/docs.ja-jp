---
title: "ICLRSyncManager::DeleteRWLockOwnerIterator メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRSyncManager.DeleteRWLockOwnerIterator
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRSyncManager::DeleteRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator method [.NET Framework hosting]
- DeleteRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: fcfd340a-b7d6-44e4-8167-2c05b789d483
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3df37a9572c47ce4b4a5080f6aed3f307adba360
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="37838-102">ICLRSyncManager::DeleteRWLockOwnerIterator メソッド</span><span class="sxs-lookup"><span data-stu-id="37838-102">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>
<span data-ttu-id="37838-103">共通言語ランタイム (CLR) がへの呼び出しによって作成された反復子を破棄することを要求[iclrsyncmanager::createrwlockowneriterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="37838-103">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37838-104">構文</span><span class="sxs-lookup"><span data-stu-id="37838-104">Syntax</span></span>  
  
```  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="37838-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="37838-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="37838-106">[in]反復子への呼び出しを使用して作成された`CreateRWLockOwnerIterator`です。</span><span class="sxs-lookup"><span data-stu-id="37838-106">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37838-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="37838-107">Return Value</span></span>  
  
|<span data-ttu-id="37838-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="37838-108">HRESULT</span></span>|<span data-ttu-id="37838-109">説明</span><span class="sxs-lookup"><span data-stu-id="37838-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="37838-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="37838-110">S_OK</span></span>|<span data-ttu-id="37838-111">`DeleteRWLockOwnerIterator`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="37838-111">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="37838-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="37838-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="37838-113">CLR をプロセスに読み込まれていないか状態にあるには、マネージ コードを実行か、呼び出しを正常に処理ができません。</span><span class="sxs-lookup"><span data-stu-id="37838-113">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="37838-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="37838-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="37838-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="37838-115">The call timed out.</span></span>|  
|<span data-ttu-id="37838-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="37838-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="37838-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="37838-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="37838-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="37838-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="37838-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="37838-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="37838-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="37838-120">E_FAIL</span></span>|<span data-ttu-id="37838-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="37838-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="37838-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="37838-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="37838-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="37838-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37838-124">コメント</span><span class="sxs-lookup"><span data-stu-id="37838-124">Remarks</span></span>  
 <span data-ttu-id="37838-125">ホストは、このメソッドを呼び出すことができ、`CreateRWLockOwnerIterator`そのスレッディングの実装の同期を保つためです。</span><span class="sxs-lookup"><span data-stu-id="37838-125">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37838-126">要件</span><span class="sxs-lookup"><span data-stu-id="37838-126">Requirements</span></span>  
 <span data-ttu-id="37838-127">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="37838-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37838-128">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="37838-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="37838-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="37838-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="37838-130">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37838-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37838-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="37838-131">See Also</span></span>  
 [<span data-ttu-id="37838-132">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="37838-132">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="37838-133">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="37838-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
