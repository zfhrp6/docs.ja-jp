---
title: IHostSecurityManager::SetThreadToken メソッド
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.SetThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::SetThreadToken
helpviewer_keywords:
- SetThreadToken method [.NET Framework hosting]
- IHostSecurityManager::SetThreadToken method [.NET Framework hosting]
ms.assetid: e951c345-8a86-4587-911b-a1a57bc6428a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71f5cdfaf47c55107980edf089f8964c5936fb23
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440987"
---
# <a name="ihostsecuritymanagersetthreadtoken-method"></a><span data-ttu-id="1ce28-102">IHostSecurityManager::SetThreadToken メソッド</span><span class="sxs-lookup"><span data-stu-id="1ce28-102">IHostSecurityManager::SetThreadToken Method</span></span>
<span data-ttu-id="1ce28-103">現在実行中のスレッドのハンドルを設定します。</span><span class="sxs-lookup"><span data-stu-id="1ce28-103">Sets a handle for the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ce28-104">構文</span><span class="sxs-lookup"><span data-stu-id="1ce28-104">Syntax</span></span>  
  
```  
HRESULT SetThreadToken (  
    [in] HANDLE hToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1ce28-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1ce28-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="1ce28-106">[in]現在実行中のスレッドに設定するトークンへのハンドル。</span><span class="sxs-lookup"><span data-stu-id="1ce28-106">[in] A handle to the token to set for the currently executing thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ce28-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="1ce28-107">Return Value</span></span>  
  
|<span data-ttu-id="1ce28-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1ce28-108">HRESULT</span></span>|<span data-ttu-id="1ce28-109">説明</span><span class="sxs-lookup"><span data-stu-id="1ce28-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1ce28-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1ce28-110">S_OK</span></span>|<span data-ttu-id="1ce28-111">`SetThreadToken` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="1ce28-111">`SetThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="1ce28-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1ce28-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1ce28-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="1ce28-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1ce28-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1ce28-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1ce28-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="1ce28-115">The call timed out.</span></span>|  
|<span data-ttu-id="1ce28-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1ce28-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1ce28-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="1ce28-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1ce28-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1ce28-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1ce28-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="1ce28-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1ce28-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1ce28-120">E_FAIL</span></span>|<span data-ttu-id="1ce28-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="1ce28-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1ce28-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="1ce28-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1ce28-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="1ce28-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ce28-124">コメント</span><span class="sxs-lookup"><span data-stu-id="1ce28-124">Remarks</span></span>  
 <span data-ttu-id="1ce28-125">`IHostSecurityManager::SetThreadToken` 動作は同様に、同じ名前の対応する Win32 関数に Win32 関数には、任意のスレッドに、ハンドルに渡す、呼び出し元がで使用できる、する点を除いて while`IHostSecurityManager::SetThreadToken`実行中のスレッドでのみ、トークンを関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="1ce28-125">`IHostSecurityManager::SetThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::SetThreadToken` can associate a token only with the currently executing thread.</span></span>  
  
 <span data-ttu-id="1ce28-126">`HANDLE`型は COM に準拠です。 つまり、そのサイズは、オペレーティング システムに固有、カスタム マーシャ リングが必要です。</span><span class="sxs-lookup"><span data-stu-id="1ce28-126">The `HANDLE` type is not COM-compliant; that is, its size is specific to an operating system and it requires custom marshaling.</span></span> <span data-ttu-id="1ce28-127">したがって、このトークンは、CLR とホスト間のプロセス内でのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="1ce28-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ce28-128">要件</span><span class="sxs-lookup"><span data-stu-id="1ce28-128">Requirements</span></span>  
 <span data-ttu-id="1ce28-129">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1ce28-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ce28-130">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1ce28-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1ce28-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="1ce28-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1ce28-132">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ce28-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ce28-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="1ce28-133">See Also</span></span>  
 [<span data-ttu-id="1ce28-134">IHostSecurityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1ce28-134">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="1ce28-135">IHostThreadPoolManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1ce28-135">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
