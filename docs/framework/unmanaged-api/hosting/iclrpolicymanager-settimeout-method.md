---
title: ICLRPolicyManager::SetTimeout メソッド
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetTimeout
helpviewer_keywords:
- SetTimeout method [.NET Framework hosting]
- ICLRPolicyManager::SetTimeout method [.NET Framework hosting]
ms.assetid: 954404fd-d52d-4e68-b582-8692f3a5f608
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b5a389af718322d1e0fffebae046bf28731877b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435778"
---
# <a name="iclrpolicymanagersettimeout-method"></a><span data-ttu-id="62de3-102">ICLRPolicyManager::SetTimeout メソッド</span><span class="sxs-lookup"><span data-stu-id="62de3-102">ICLRPolicyManager::SetTimeout Method</span></span>
<span data-ttu-id="62de3-103">指定された操作のタイムアウト値を設定します。</span><span class="sxs-lookup"><span data-stu-id="62de3-103">Sets a timeout value for the specified operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62de3-104">構文</span><span class="sxs-lookup"><span data-stu-id="62de3-104">Syntax</span></span>  
  
```  
HRESULT SetTimeout (  
    [in] EClrOperation operation,  
    [in] DWORD dsMilliseconds  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62de3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="62de3-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="62de3-106">[in]1 つ、 [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)タイムアウトを設定する対象の共通言語ランタイム (CLR) 操作を示す値。</span><span class="sxs-lookup"><span data-stu-id="62de3-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the common language runtime (CLR) operation for which to set a timeout.</span></span> <span data-ttu-id="62de3-107">次の値がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="62de3-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="62de3-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="62de3-108">OPR_AppDomainUnload</span></span>  
  
-   <span data-ttu-id="62de3-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="62de3-109">OPR_ProcessExit</span></span>  
  
-   <span data-ttu-id="62de3-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="62de3-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
-   <span data-ttu-id="62de3-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="62de3-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="62de3-112">[in]新しいタイムアウト値 (ミリ秒単位)。</span><span class="sxs-lookup"><span data-stu-id="62de3-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="62de3-113">無限を指定すると、操作はタイムアウトが発生することはありません。</span><span class="sxs-lookup"><span data-stu-id="62de3-113">A value of INFINITE causes the operation never to time out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="62de3-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="62de3-114">Return Value</span></span>  
  
|<span data-ttu-id="62de3-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="62de3-115">HRESULT</span></span>|<span data-ttu-id="62de3-116">説明</span><span class="sxs-lookup"><span data-stu-id="62de3-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="62de3-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="62de3-117">S_OK</span></span>|<span data-ttu-id="62de3-118">`SetTimeout` 正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="62de3-118">`SetTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="62de3-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="62de3-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="62de3-120">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="62de3-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="62de3-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="62de3-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="62de3-122">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="62de3-122">The call timed out.</span></span>|  
|<span data-ttu-id="62de3-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="62de3-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="62de3-124">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="62de3-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="62de3-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="62de3-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="62de3-126">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="62de3-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="62de3-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="62de3-127">E_FAIL</span></span>|<span data-ttu-id="62de3-128">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="62de3-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="62de3-129">メソッドには、E_FAIL が返された、後に、CLR はプロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="62de3-129">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="62de3-130">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="62de3-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="62de3-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="62de3-131">E_INVALIDARG</span></span>|<span data-ttu-id="62de3-132">タイムアウトを設定することはできません、指定された`operation`の無効な値が指定されてまたは`operation`です。</span><span class="sxs-lookup"><span data-stu-id="62de3-132">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="62de3-133">要件</span><span class="sxs-lookup"><span data-stu-id="62de3-133">Requirements</span></span>  
 <span data-ttu-id="62de3-134">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="62de3-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62de3-135">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="62de3-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="62de3-136">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="62de3-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="62de3-137">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62de3-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62de3-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="62de3-138">See Also</span></span>  
 [<span data-ttu-id="62de3-139">EClrOperation 列挙型</span><span class="sxs-lookup"><span data-stu-id="62de3-139">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="62de3-140">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="62de3-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="62de3-141">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="62de3-141">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
