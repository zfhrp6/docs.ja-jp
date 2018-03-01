---
title: "IHostPolicyManager::OnDefaultAction メソッド"
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
- IHostPolicyManager.OnDefaultAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnDefaultAction
helpviewer_keywords:
- OnDefaultAction method [.NET Framework hosting]
- IHostPolicyManager::OnDefaultAction method [.NET Framework hosting]
ms.assetid: 071e73bd-4795-470f-9373-cfaef553b7f2
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d1fded3d986e6505d0a321c47b03b5cdf9d881a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostpolicymanagerondefaultaction-method"></a><span data-ttu-id="30eba-102">IHostPolicyManager::OnDefaultAction メソッド</span><span class="sxs-lookup"><span data-stu-id="30eba-102">IHostPolicyManager::OnDefaultAction Method</span></span>
<span data-ttu-id="30eba-103">共通言語ランタイム (CLR) がへの呼び出しによって設定された既定のアクションを実行しようとしていますが、ホストに通知、 [iclrpolicymanager::setdefaultaction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md)スレッドの中止への応答でメソッドまたは<xref:System.AppDomain>をアンロードします。</span><span class="sxs-lookup"><span data-stu-id="30eba-103">Notifies the host that the common language runtime (CLR) is about to take the default action that was set by a call to the [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) method in response to a thread abort or <xref:System.AppDomain> unload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30eba-104">構文</span><span class="sxs-lookup"><span data-stu-id="30eba-104">Syntax</span></span>  
  
```  
HRESULT OnDefaultAction (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="30eba-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="30eba-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="30eba-106">[in]1 つ、 [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) CLR が応答してイベントの種類を示す値。</span><span class="sxs-lookup"><span data-stu-id="30eba-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of event to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="30eba-107">[in]1 つ、 [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) CLR は、イベントに応答するアクションを示す値。</span><span class="sxs-lookup"><span data-stu-id="30eba-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action that the CLR is taking in response to the event.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30eba-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="30eba-108">Return Value</span></span>  
  
|<span data-ttu-id="30eba-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="30eba-109">HRESULT</span></span>|<span data-ttu-id="30eba-110">説明</span><span class="sxs-lookup"><span data-stu-id="30eba-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="30eba-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="30eba-111">S_OK</span></span>|<span data-ttu-id="30eba-112">`OnDefaultAction`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="30eba-112">`OnDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="30eba-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="30eba-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="30eba-114">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しを実行します。</span><span class="sxs-lookup"><span data-stu-id="30eba-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="30eba-115">正常に</span><span class="sxs-lookup"><span data-stu-id="30eba-115">successfully</span></span>|  
|<span data-ttu-id="30eba-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="30eba-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="30eba-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="30eba-117">The call timed out.</span></span>|  
|<span data-ttu-id="30eba-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="30eba-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="30eba-119">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="30eba-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="30eba-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="30eba-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="30eba-121">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="30eba-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="30eba-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="30eba-122">E_FAIL</span></span>|<span data-ttu-id="30eba-123">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="30eba-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="30eba-124">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="30eba-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="30eba-125">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="30eba-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="30eba-126">必要条件</span><span class="sxs-lookup"><span data-stu-id="30eba-126">Requirements</span></span>  
 <span data-ttu-id="30eba-127">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="30eba-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30eba-128">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="30eba-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="30eba-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="30eba-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="30eba-130">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30eba-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30eba-131">参照</span><span class="sxs-lookup"><span data-stu-id="30eba-131">See Also</span></span>  
 [<span data-ttu-id="30eba-132">EClrOperation 列挙型</span><span class="sxs-lookup"><span data-stu-id="30eba-132">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="30eba-133">EPolicyAction 列挙型</span><span class="sxs-lookup"><span data-stu-id="30eba-133">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="30eba-134">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="30eba-134">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="30eba-135">IHostPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="30eba-135">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
