---
title: "IHostSecurityManager::RevertToSelf メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager.RevertToSelf
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager::RevertToSelf
helpviewer_keywords:
- RevertToSelf method [.NET Framework hosting]
- IHostSecurityManager::RevertToSelf method [.NET Framework hosting]
ms.assetid: 189f28f8-f9a1-4192-aedc-91084e4f8b99
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0fad325bc3df54f412a797e9944f5b1f38615786
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsecuritymanagerreverttoself-method"></a><span data-ttu-id="919dd-102">IHostSecurityManager::RevertToSelf メソッド</span><span class="sxs-lookup"><span data-stu-id="919dd-102">IHostSecurityManager::RevertToSelf Method</span></span>
<span data-ttu-id="919dd-103">現在のユーザー id の権限の借用を終了し、元のスレッド トークンを返します。</span><span class="sxs-lookup"><span data-stu-id="919dd-103">Terminates impersonation of the current user identity and returns the original thread token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="919dd-104">構文</span><span class="sxs-lookup"><span data-stu-id="919dd-104">Syntax</span></span>  
  
```  
HRESULT RevertToSelf ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="919dd-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="919dd-105">Return Value</span></span>  
  
|<span data-ttu-id="919dd-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="919dd-106">HRESULT</span></span>|<span data-ttu-id="919dd-107">説明</span><span class="sxs-lookup"><span data-stu-id="919dd-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="919dd-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="919dd-108">S_OK</span></span>|<span data-ttu-id="919dd-109">`RevertToSelf`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="919dd-109">`RevertToSelf` returned successfully.</span></span>|  
|<span data-ttu-id="919dd-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="919dd-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="919dd-111">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="919dd-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="919dd-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="919dd-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="919dd-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="919dd-113">The call timed out.</span></span>|  
|<span data-ttu-id="919dd-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="919dd-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="919dd-115">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="919dd-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="919dd-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="919dd-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="919dd-117">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="919dd-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="919dd-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="919dd-118">E_FAIL</span></span>|<span data-ttu-id="919dd-119">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="919dd-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="919dd-120">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="919dd-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="919dd-121">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="919dd-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="919dd-122">コメント</span><span class="sxs-lookup"><span data-stu-id="919dd-122">Remarks</span></span>  
 <span data-ttu-id="919dd-123">`RevertToSelf`事前に呼び出した後、元のスレッド トークンを返すために呼び出される、 [ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="919dd-123">`RevertToSelf` is called to return to the original thread token, after an earlier call to the [ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="919dd-124">要件</span><span class="sxs-lookup"><span data-stu-id="919dd-124">Requirements</span></span>  
 <span data-ttu-id="919dd-125">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="919dd-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="919dd-126">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="919dd-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="919dd-127">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="919dd-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="919dd-128">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="919dd-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="919dd-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="919dd-129">See Also</span></span>  
 [<span data-ttu-id="919dd-130">IHostSecurityContext インターフェイス</span><span class="sxs-lookup"><span data-stu-id="919dd-130">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="919dd-131">IHostSecurityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="919dd-131">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="919dd-132">ImpersonateLoggedOnUser メソッド</span><span class="sxs-lookup"><span data-stu-id="919dd-132">ImpersonateLoggedOnUser Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)
