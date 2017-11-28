---
title: "ICLRPolicyManager::SetTimeout メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager.SetTimeout
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager::SetTimeout
helpviewer_keywords:
- SetTimeout method [.NET Framework hosting]
- ICLRPolicyManager::SetTimeout method [.NET Framework hosting]
ms.assetid: 954404fd-d52d-4e68-b582-8692f3a5f608
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 31dfd4654f849d01958be2690afed0f31c736dfd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrpolicymanagersettimeout-method"></a><span data-ttu-id="b90a5-102">ICLRPolicyManager::SetTimeout メソッド</span><span class="sxs-lookup"><span data-stu-id="b90a5-102">ICLRPolicyManager::SetTimeout Method</span></span>
<span data-ttu-id="b90a5-103">指定された操作のタイムアウト値を設定します。</span><span class="sxs-lookup"><span data-stu-id="b90a5-103">Sets a timeout value for the specified operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b90a5-104">構文</span><span class="sxs-lookup"><span data-stu-id="b90a5-104">Syntax</span></span>  
  
```  
HRESULT SetTimeout (  
    [in] EClrOperation operation,  
    [in] DWORD dsMilliseconds  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b90a5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b90a5-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="b90a5-106">[in]1 つ、 [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)タイムアウトを設定する対象の共通言語ランタイム (CLR) 操作を示す値。</span><span class="sxs-lookup"><span data-stu-id="b90a5-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the common language runtime (CLR) operation for which to set a timeout.</span></span> <span data-ttu-id="b90a5-107">次の値がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b90a5-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="b90a5-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="b90a5-108">OPR_AppDomainUnload</span></span>  
  
-   <span data-ttu-id="b90a5-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="b90a5-109">OPR_ProcessExit</span></span>  
  
-   <span data-ttu-id="b90a5-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="b90a5-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
-   <span data-ttu-id="b90a5-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="b90a5-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="b90a5-112">[in]新しいタイムアウト値 (ミリ秒単位)。</span><span class="sxs-lookup"><span data-stu-id="b90a5-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="b90a5-113">無限を指定すると、操作はタイムアウトが発生することはありません。</span><span class="sxs-lookup"><span data-stu-id="b90a5-113">A value of INFINITE causes the operation never to time out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b90a5-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="b90a5-114">Return Value</span></span>  
  
|<span data-ttu-id="b90a5-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b90a5-115">HRESULT</span></span>|<span data-ttu-id="b90a5-116">説明</span><span class="sxs-lookup"><span data-stu-id="b90a5-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b90a5-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="b90a5-117">S_OK</span></span>|<span data-ttu-id="b90a5-118">`SetTimeout`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="b90a5-118">`SetTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="b90a5-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b90a5-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b90a5-120">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="b90a5-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b90a5-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b90a5-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b90a5-122">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="b90a5-122">The call timed out.</span></span>|  
|<span data-ttu-id="b90a5-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b90a5-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b90a5-124">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="b90a5-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b90a5-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b90a5-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b90a5-126">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="b90a5-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b90a5-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b90a5-127">E_FAIL</span></span>|<span data-ttu-id="b90a5-128">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="b90a5-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b90a5-129">メソッドには、E_FAIL が返された、後に、CLR はプロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="b90a5-129">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b90a5-130">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="b90a5-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b90a5-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b90a5-131">E_INVALIDARG</span></span>|<span data-ttu-id="b90a5-132">タイムアウトを設定することはできません、指定された`operation`の無効な値が指定されてまたは`operation`です。</span><span class="sxs-lookup"><span data-stu-id="b90a5-132">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b90a5-133">要件</span><span class="sxs-lookup"><span data-stu-id="b90a5-133">Requirements</span></span>  
 <span data-ttu-id="b90a5-134">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b90a5-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b90a5-135">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b90a5-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b90a5-136">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="b90a5-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b90a5-137">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b90a5-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b90a5-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="b90a5-138">See Also</span></span>  
 [<span data-ttu-id="b90a5-139">EClrOperation 列挙型</span><span class="sxs-lookup"><span data-stu-id="b90a5-139">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="b90a5-140">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b90a5-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="b90a5-141">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b90a5-141">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
