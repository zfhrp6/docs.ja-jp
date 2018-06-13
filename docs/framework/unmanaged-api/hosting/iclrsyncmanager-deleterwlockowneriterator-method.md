---
title: ICLRSyncManager::DeleteRWLockOwnerIterator メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ee4a09902be093bdbfe0b367f4add35bdda571c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434068"
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="e70f6-102">ICLRSyncManager::DeleteRWLockOwnerIterator メソッド</span><span class="sxs-lookup"><span data-stu-id="e70f6-102">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>
<span data-ttu-id="e70f6-103">共通言語ランタイム (CLR) がへの呼び出しによって作成された反復子を破棄することを要求[iclrsyncmanager::createrwlockowneriterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="e70f6-103">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e70f6-104">構文</span><span class="sxs-lookup"><span data-stu-id="e70f6-104">Syntax</span></span>  
  
```  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e70f6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e70f6-105">Parameters</span></span>  
 `Iterator`  
 <span data-ttu-id="e70f6-106">[in]反復子への呼び出しを使用して作成された`CreateRWLockOwnerIterator`です。</span><span class="sxs-lookup"><span data-stu-id="e70f6-106">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e70f6-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="e70f6-107">Return Value</span></span>  
  
|<span data-ttu-id="e70f6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e70f6-108">HRESULT</span></span>|<span data-ttu-id="e70f6-109">説明</span><span class="sxs-lookup"><span data-stu-id="e70f6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e70f6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e70f6-110">S_OK</span></span>|<span data-ttu-id="e70f6-111">`DeleteRWLockOwnerIterator` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="e70f6-111">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="e70f6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e70f6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e70f6-113">CLR をプロセスに読み込まれていないか状態にあるには、マネージ コードを実行か、呼び出しを正常に処理ができません。</span><span class="sxs-lookup"><span data-stu-id="e70f6-113">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="e70f6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e70f6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e70f6-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="e70f6-115">The call timed out.</span></span>|  
|<span data-ttu-id="e70f6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e70f6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e70f6-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="e70f6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e70f6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e70f6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e70f6-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="e70f6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e70f6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e70f6-120">E_FAIL</span></span>|<span data-ttu-id="e70f6-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="e70f6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e70f6-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="e70f6-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e70f6-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="e70f6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e70f6-124">コメント</span><span class="sxs-lookup"><span data-stu-id="e70f6-124">Remarks</span></span>  
 <span data-ttu-id="e70f6-125">ホストは、このメソッドを呼び出すことができ、`CreateRWLockOwnerIterator`そのスレッディングの実装の同期を保つためです。</span><span class="sxs-lookup"><span data-stu-id="e70f6-125">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e70f6-126">要件</span><span class="sxs-lookup"><span data-stu-id="e70f6-126">Requirements</span></span>  
 <span data-ttu-id="e70f6-127">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e70f6-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e70f6-128">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e70f6-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e70f6-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="e70f6-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e70f6-130">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e70f6-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e70f6-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="e70f6-131">See Also</span></span>  
 [<span data-ttu-id="e70f6-132">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e70f6-132">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="e70f6-133">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e70f6-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
