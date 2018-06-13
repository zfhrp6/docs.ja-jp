---
title: IHostSecurityManager::RevertToSelf メソッド
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.RevertToSelf
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::RevertToSelf
helpviewer_keywords:
- RevertToSelf method [.NET Framework hosting]
- IHostSecurityManager::RevertToSelf method [.NET Framework hosting]
ms.assetid: 189f28f8-f9a1-4192-aedc-91084e4f8b99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c34d9243e4ed7ed2492784154b157189c7d22cd2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440581"
---
# <a name="ihostsecuritymanagerreverttoself-method"></a><span data-ttu-id="8008e-102">IHostSecurityManager::RevertToSelf メソッド</span><span class="sxs-lookup"><span data-stu-id="8008e-102">IHostSecurityManager::RevertToSelf Method</span></span>
<span data-ttu-id="8008e-103">現在のユーザー id の権限の借用を終了し、元のスレッド トークンを返します。</span><span class="sxs-lookup"><span data-stu-id="8008e-103">Terminates impersonation of the current user identity and returns the original thread token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8008e-104">構文</span><span class="sxs-lookup"><span data-stu-id="8008e-104">Syntax</span></span>  
  
```  
HRESULT RevertToSelf ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8008e-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="8008e-105">Return Value</span></span>  
  
|<span data-ttu-id="8008e-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8008e-106">HRESULT</span></span>|<span data-ttu-id="8008e-107">説明</span><span class="sxs-lookup"><span data-stu-id="8008e-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8008e-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="8008e-108">S_OK</span></span>|<span data-ttu-id="8008e-109">`RevertToSelf` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="8008e-109">`RevertToSelf` returned successfully.</span></span>|  
|<span data-ttu-id="8008e-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8008e-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8008e-111">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="8008e-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8008e-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8008e-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8008e-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="8008e-113">The call timed out.</span></span>|  
|<span data-ttu-id="8008e-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8008e-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8008e-115">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="8008e-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8008e-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8008e-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8008e-117">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="8008e-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8008e-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8008e-118">E_FAIL</span></span>|<span data-ttu-id="8008e-119">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="8008e-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8008e-120">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="8008e-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8008e-121">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="8008e-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8008e-122">コメント</span><span class="sxs-lookup"><span data-stu-id="8008e-122">Remarks</span></span>  
 <span data-ttu-id="8008e-123">`RevertToSelf` 事前に呼び出した後、元のスレッド トークンを返すために呼び出される、 [ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="8008e-123">`RevertToSelf` is called to return to the original thread token, after an earlier call to the [ImpersonateLoggedOnUser](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8008e-124">要件</span><span class="sxs-lookup"><span data-stu-id="8008e-124">Requirements</span></span>  
 <span data-ttu-id="8008e-125">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8008e-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8008e-126">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8008e-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8008e-127">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="8008e-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8008e-128">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8008e-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8008e-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="8008e-129">See Also</span></span>  
 [<span data-ttu-id="8008e-130">IHostSecurityContext インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8008e-130">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="8008e-131">IHostSecurityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8008e-131">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="8008e-132">ImpersonateLoggedOnUser メソッド</span><span class="sxs-lookup"><span data-stu-id="8008e-132">ImpersonateLoggedOnUser Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)
