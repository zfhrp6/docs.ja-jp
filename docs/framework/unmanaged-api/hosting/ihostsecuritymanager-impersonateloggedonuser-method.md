---
title: "IHostSecurityManager::ImpersonateLoggedOnUser メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager.ImpersonateLoggedOnUser
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager::ImpersonateLoggedOnUser
helpviewer_keywords:
- ImpersonateLoggedOnUser method [.NET Framework hosting]
- IHostSecurityManager::ImpersonateLoggedOnUser method [.NET Framework hosting]
ms.assetid: acc49ba0-f1d9-45ad-871f-9d053a89dcbe
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8c5956dcad6908f0117de7f5ff0c6632ad3bb925
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsecuritymanagerimpersonateloggedonuser-method"></a><span data-ttu-id="eab68-102">IHostSecurityManager::ImpersonateLoggedOnUser メソッド</span><span class="sxs-lookup"><span data-stu-id="eab68-102">IHostSecurityManager::ImpersonateLoggedOnUser Method</span></span>
<span data-ttu-id="eab68-103">要求の現在のユーザー id の資格情報を使用してコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="eab68-103">Requests that code be executed using the credentials of the current user identity.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eab68-104">構文</span><span class="sxs-lookup"><span data-stu-id="eab68-104">Syntax</span></span>  
  
```  
HRESULT ImpersonateLoggedOnUser (  
    [in] HANDLE hToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eab68-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eab68-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="eab68-106">[in]権限を借用するユーザーの資格情報を表すトークンです。</span><span class="sxs-lookup"><span data-stu-id="eab68-106">[in] A token representing the credentials of the user to be impersonated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eab68-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="eab68-107">Return Value</span></span>  
  
|<span data-ttu-id="eab68-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eab68-108">HRESULT</span></span>|<span data-ttu-id="eab68-109">説明</span><span class="sxs-lookup"><span data-stu-id="eab68-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eab68-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="eab68-110">S_OK</span></span>|<span data-ttu-id="eab68-111">`ImpersonateLoggedOnUser`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="eab68-111">`ImpersonateLoggedOnUser` returned successfully.</span></span>|  
|<span data-ttu-id="eab68-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="eab68-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="eab68-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="eab68-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="eab68-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="eab68-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="eab68-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="eab68-115">The call timed out.</span></span>|  
|<span data-ttu-id="eab68-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="eab68-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="eab68-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="eab68-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="eab68-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="eab68-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="eab68-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="eab68-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="eab68-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="eab68-120">E_FAIL</span></span>|<span data-ttu-id="eab68-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="eab68-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="eab68-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="eab68-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="eab68-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="eab68-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eab68-124">コメント</span><span class="sxs-lookup"><span data-stu-id="eab68-124">Remarks</span></span>  
 <span data-ttu-id="eab68-125">呼び出す`LogonUser`または関連する Win32 関数を現在のユーザー id の資格情報へのハンドルを取得します。</span><span class="sxs-lookup"><span data-stu-id="eab68-125">Call `LogonUser` or a related Win32 function to get a handle to the credentials of the current user identity.</span></span>  
  
 <span data-ttu-id="eab68-126">`HANDLE`型が COM に準拠していない、つまり、そのサイズは、オペレーティング システムに固有、カスタム マーシャ リングが必要です。</span><span class="sxs-lookup"><span data-stu-id="eab68-126">The `HANDLE` type is not COM-compliant, that is, its size is specific to an operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="eab68-127">したがって、このトークンは、CLR とホスト間のプロセス内でのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="eab68-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eab68-128">要件</span><span class="sxs-lookup"><span data-stu-id="eab68-128">Requirements</span></span>  
 <span data-ttu-id="eab68-129">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="eab68-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eab68-130">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="eab68-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eab68-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="eab68-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eab68-132">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eab68-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eab68-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="eab68-133">See Also</span></span>  
 [<span data-ttu-id="eab68-134">IHostSecurityContext インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eab68-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="eab68-135">IHostSecurityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eab68-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="eab68-136">RevertToSelf メソッド</span><span class="sxs-lookup"><span data-stu-id="eab68-136">RevertToSelf Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)
