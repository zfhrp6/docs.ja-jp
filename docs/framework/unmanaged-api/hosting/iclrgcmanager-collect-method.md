---
title: ICLRGCManager::Collect メソッド
ms.date: 03/30/2017
api_name:
- ICLRGCManager.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::Collect
helpviewer_keywords:
- ICLRGCManager::Collect method [.NET Framework hosting]
- Collect method, ICLRGCManager interface [.NET Framework hosting]
ms.assetid: 0c6cbbea-c27c-4695-bda3-17c1910d8ddb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b9c3899c4319c623bc991d0775945f0a4dc09e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="iclrgcmanagercollect-method"></a><span data-ttu-id="26c2a-102">ICLRGCManager::Collect メソッド</span><span class="sxs-lookup"><span data-stu-id="26c2a-102">ICLRGCManager::Collect Method</span></span>
<span data-ttu-id="26c2a-103">指定したジェネレーションのガベージ コレクションを強制的にします。</span><span class="sxs-lookup"><span data-stu-id="26c2a-103">Forces a garbage collection for the specified generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26c2a-104">構文</span><span class="sxs-lookup"><span data-stu-id="26c2a-104">Syntax</span></span>  
  
```  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="26c2a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26c2a-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="26c2a-106">[in]収集を生成します。</span><span class="sxs-lookup"><span data-stu-id="26c2a-106">[in] The generation to collect.</span></span> <span data-ttu-id="26c2a-107">-1 の値には、すべてのジェネレーションのコレクションが強制実行します。</span><span class="sxs-lookup"><span data-stu-id="26c2a-107">A value of -1 forces a collection of all generations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="26c2a-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="26c2a-108">Return Value</span></span>  
  
|<span data-ttu-id="26c2a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="26c2a-109">HRESULT</span></span>|<span data-ttu-id="26c2a-110">説明</span><span class="sxs-lookup"><span data-stu-id="26c2a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="26c2a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="26c2a-111">S_OK</span></span>|<span data-ttu-id="26c2a-112">`Collect` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="26c2a-112">`Collect` returned successfully.</span></span>|  
|<span data-ttu-id="26c2a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="26c2a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="26c2a-114">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="26c2a-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="26c2a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="26c2a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="26c2a-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="26c2a-116">The call timed out.</span></span>|  
|<span data-ttu-id="26c2a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="26c2a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="26c2a-118">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="26c2a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="26c2a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="26c2a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="26c2a-120">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="26c2a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="26c2a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="26c2a-121">E_FAIL</span></span>|<span data-ttu-id="26c2a-122">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="26c2a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="26c2a-123">メソッドには、E_FAIL が返された、後に、CLR はプロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="26c2a-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="26c2a-124">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="26c2a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26c2a-125">コメント</span><span class="sxs-lookup"><span data-stu-id="26c2a-125">Remarks</span></span>  
 <span data-ttu-id="26c2a-126">`Collect`メソッドは、現在の状態に関係なくコレクションを実行する CLR のガベージ コレクターを強制します。</span><span class="sxs-lookup"><span data-stu-id="26c2a-126">The `Collect` method forces the CLR's garbage collector to perform a collection regardless of its current state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26c2a-127">要件</span><span class="sxs-lookup"><span data-stu-id="26c2a-127">Requirements</span></span>  
 <span data-ttu-id="26c2a-128">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="26c2a-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26c2a-129">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="26c2a-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="26c2a-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="26c2a-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="26c2a-131">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26c2a-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26c2a-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="26c2a-132">See Also</span></span>  
 [<span data-ttu-id="26c2a-133">自動メモリ管理</span><span class="sxs-lookup"><span data-stu-id="26c2a-133">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="26c2a-134">ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="26c2a-134">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)  
 [<span data-ttu-id="26c2a-135">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="26c2a-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="26c2a-136">ICLRGCManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="26c2a-136">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 [<span data-ttu-id="26c2a-137">CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="26c2a-137">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [<span data-ttu-id="26c2a-138">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="26c2a-138">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="26c2a-139">ホスティング</span><span class="sxs-lookup"><span data-stu-id="26c2a-139">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
