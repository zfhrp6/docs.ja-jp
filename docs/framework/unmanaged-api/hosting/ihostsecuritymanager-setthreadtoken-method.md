---
title: "IHostSecurityManager::SetThreadToken メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager.SetThreadToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager::SetThreadToken
helpviewer_keywords:
- SetThreadToken method [.NET Framework hosting]
- IHostSecurityManager::SetThreadToken method [.NET Framework hosting]
ms.assetid: e951c345-8a86-4587-911b-a1a57bc6428a
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 35418907c2b3c75fef689e53b9d6b86ded1f2570
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsecuritymanagersetthreadtoken-method"></a><span data-ttu-id="d98ff-102">IHostSecurityManager::SetThreadToken メソッド</span><span class="sxs-lookup"><span data-stu-id="d98ff-102">IHostSecurityManager::SetThreadToken Method</span></span>
<span data-ttu-id="d98ff-103">現在実行中のスレッドのハンドルを設定します。</span><span class="sxs-lookup"><span data-stu-id="d98ff-103">Sets a handle for the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d98ff-104">構文</span><span class="sxs-lookup"><span data-stu-id="d98ff-104">Syntax</span></span>  
  
```  
HRESULT SetThreadToken (  
    [in] HANDLE hToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d98ff-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d98ff-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="d98ff-106">[in]現在実行中のスレッドに設定するトークンへのハンドル。</span><span class="sxs-lookup"><span data-stu-id="d98ff-106">[in] A handle to the token to set for the currently executing thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d98ff-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="d98ff-107">Return Value</span></span>  
  
|<span data-ttu-id="d98ff-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d98ff-108">HRESULT</span></span>|<span data-ttu-id="d98ff-109">説明</span><span class="sxs-lookup"><span data-stu-id="d98ff-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d98ff-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d98ff-110">S_OK</span></span>|<span data-ttu-id="d98ff-111">`SetThreadToken`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="d98ff-111">`SetThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="d98ff-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d98ff-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d98ff-113">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="d98ff-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d98ff-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d98ff-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d98ff-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="d98ff-115">The call timed out.</span></span>|  
|<span data-ttu-id="d98ff-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d98ff-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d98ff-117">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="d98ff-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d98ff-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d98ff-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d98ff-119">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="d98ff-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d98ff-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d98ff-120">E_FAIL</span></span>|<span data-ttu-id="d98ff-121">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="d98ff-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d98ff-122">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="d98ff-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d98ff-123">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="d98ff-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d98ff-124">コメント</span><span class="sxs-lookup"><span data-stu-id="d98ff-124">Remarks</span></span>  
 <span data-ttu-id="d98ff-125">`IHostSecurityManager::SetThreadToken`動作は同様に、同じ名前の対応する Win32 関数に Win32 関数には、任意のスレッドに、ハンドルに渡す、呼び出し元がで使用できる、する点を除いて while`IHostSecurityManager::SetThreadToken`実行中のスレッドでのみ、トークンを関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="d98ff-125">`IHostSecurityManager::SetThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::SetThreadToken` can associate a token only with the currently executing thread.</span></span>  
  
 <span data-ttu-id="d98ff-126">`HANDLE`型は COM に準拠です。 つまり、そのサイズは、オペレーティング システムに固有、カスタム マーシャ リングが必要です。</span><span class="sxs-lookup"><span data-stu-id="d98ff-126">The `HANDLE` type is not COM-compliant; that is, its size is specific to an operating system and it requires custom marshaling.</span></span> <span data-ttu-id="d98ff-127">したがって、このトークンは、CLR とホスト間のプロセス内でのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="d98ff-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d98ff-128">必要条件</span><span class="sxs-lookup"><span data-stu-id="d98ff-128">Requirements</span></span>  
 <span data-ttu-id="d98ff-129">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d98ff-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d98ff-130">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d98ff-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d98ff-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="d98ff-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d98ff-132">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d98ff-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d98ff-133">参照</span><span class="sxs-lookup"><span data-stu-id="d98ff-133">See Also</span></span>  
 [<span data-ttu-id="d98ff-134">IHostSecurityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d98ff-134">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="d98ff-135">IHostThreadPoolManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d98ff-135">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
