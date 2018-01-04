---
title: "IHostPolicyManager::OnTimeout メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostPolicyManager.OnTimeout
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostPolicyManager::OnTimeout
helpviewer_keywords:
- IHostPolicyManager::OnTimeout method [.NET Framework hosting]
- OnTimeout method [.NET Framework hosting]
ms.assetid: 0a313b51-5e4d-4714-a86b-af75cf3902e6
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b8c29bc281b64368e8b310e2b13f3fcb1bdc6ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostpolicymanagerontimeout-method"></a><span data-ttu-id="63aec-102">IHostPolicyManager::OnTimeout メソッド</span><span class="sxs-lookup"><span data-stu-id="63aec-102">IHostPolicyManager::OnTimeout Method</span></span>
<span data-ttu-id="63aec-103">共通言語ランタイム (CLR) がへの呼び出しで指定されたアクションを実行しようとしていますが、ホストに通知、 [iclrpolicymanager::setactionontimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)メソッドがタイムアウトに応答します。</span><span class="sxs-lookup"><span data-stu-id="63aec-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) method in response to a timeout.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63aec-104">構文</span><span class="sxs-lookup"><span data-stu-id="63aec-104">Syntax</span></span>  
  
```  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="63aec-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="63aec-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="63aec-106">[in]1 つ、 [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)タイムアウトしました。 操作の種類を示す値。</span><span class="sxs-lookup"><span data-stu-id="63aec-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of operation that timed out.</span></span>  
  
 `action`  
 <span data-ttu-id="63aec-107">[in]1 つ、 [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)値をタイムアウトへの応答時間が、CLR のアクションを示すです。</span><span class="sxs-lookup"><span data-stu-id="63aec-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to the timeout.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63aec-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="63aec-108">Return Value</span></span>  
  
|<span data-ttu-id="63aec-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="63aec-109">HRESULT</span></span>|<span data-ttu-id="63aec-110">説明</span><span class="sxs-lookup"><span data-stu-id="63aec-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="63aec-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="63aec-111">S_OK</span></span>|<span data-ttu-id="63aec-112">`OnTimeout`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="63aec-112">`OnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="63aec-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="63aec-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="63aec-114">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="63aec-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="63aec-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="63aec-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="63aec-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="63aec-116">The call timed out.</span></span>|  
|<span data-ttu-id="63aec-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="63aec-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="63aec-118">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="63aec-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="63aec-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="63aec-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="63aec-120">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="63aec-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="63aec-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="63aec-121">E_FAIL</span></span>|<span data-ttu-id="63aec-122">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="63aec-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="63aec-123">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="63aec-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="63aec-124">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="63aec-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="63aec-125">必要条件</span><span class="sxs-lookup"><span data-stu-id="63aec-125">Requirements</span></span>  
 <span data-ttu-id="63aec-126">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="63aec-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63aec-127">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="63aec-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="63aec-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="63aec-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="63aec-129">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63aec-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63aec-130">参照</span><span class="sxs-lookup"><span data-stu-id="63aec-130">See Also</span></span>  
 [<span data-ttu-id="63aec-131">EClrOperation 列挙型</span><span class="sxs-lookup"><span data-stu-id="63aec-131">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="63aec-132">EPolicyAction 列挙型</span><span class="sxs-lookup"><span data-stu-id="63aec-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="63aec-133">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="63aec-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="63aec-134">IHostPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="63aec-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
