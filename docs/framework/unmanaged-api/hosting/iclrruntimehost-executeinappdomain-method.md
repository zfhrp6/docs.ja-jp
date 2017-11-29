---
title: "ICLRRuntimeHost::ExecuteInAppDomain メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.ExecuteInAppDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::ExecuteInAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain method [.NET Framework hosting]
- ExecuteInAppDomain method [.NET Framework hosting]
ms.assetid: e2b0e2db-3fae-4b56-844e-d30a125a660c
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: da6e9b52c0ea6f2935aad70779e159db91a4f501
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="5da06-102">ICLRRuntimeHost::ExecuteInAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="5da06-102">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>
<span data-ttu-id="5da06-103">指定します、<xref:System.AppDomain>指定したマネージ コードを実行するためです。</span><span class="sxs-lookup"><span data-stu-id="5da06-103">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5da06-104">構文</span><span class="sxs-lookup"><span data-stu-id="5da06-104">Syntax</span></span>  
  
```  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,   
    [in] FExecuteInDomainCallback pCallback,   
    [in] void* cookie  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5da06-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5da06-105">Parameters</span></span>  
 `AppDomainId`  
 <span data-ttu-id="5da06-106">[in]数値 ID、<xref:System.AppDomain>指定したメソッドを実行するためです。</span><span class="sxs-lookup"><span data-stu-id="5da06-106">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="5da06-107">[in]指定した内で実行する関数へのポインター<xref:System.AppDomain>です。</span><span class="sxs-lookup"><span data-stu-id="5da06-107">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="5da06-108">[in]非透過の呼び出し元が割り当てたメモリへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5da06-108">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="5da06-109">このパラメーターは、共通言語ランタイム (CLR) でドメインのコールバックに渡されます。</span><span class="sxs-lookup"><span data-stu-id="5da06-109">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="5da06-110">ランタイムで管理されたヒープ メモリではありません。割り当てとこのメモリの有効期間は、呼び出し元によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="5da06-110">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5da06-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="5da06-111">Return Value</span></span>  
  
|<span data-ttu-id="5da06-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5da06-112">HRESULT</span></span>|<span data-ttu-id="5da06-113">説明</span><span class="sxs-lookup"><span data-stu-id="5da06-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5da06-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="5da06-114">S_OK</span></span>|<span data-ttu-id="5da06-115">`ExecuteInAppDomain`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="5da06-115">`ExecuteInAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="5da06-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5da06-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5da06-117">CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="5da06-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5da06-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5da06-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5da06-119">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="5da06-119">The call timed out.</span></span>|  
|<span data-ttu-id="5da06-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5da06-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5da06-121">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="5da06-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5da06-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5da06-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5da06-123">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="5da06-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5da06-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5da06-124">E_FAIL</span></span>|<span data-ttu-id="5da06-125">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="5da06-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5da06-126">メソッドには、E_FAIL が返された場合、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="5da06-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5da06-127">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="5da06-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5da06-128">コメント</span><span class="sxs-lookup"><span data-stu-id="5da06-128">Remarks</span></span>  
 <span data-ttu-id="5da06-129">`ExecuteInAppDomain`ホストが制御できるように管理 over<xref:System.AppDomain>で、指定したマネージ メソッドを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5da06-129">`ExecuteInAppDomain` allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="5da06-130">値に対応するアプリケーション ドメインの識別子の値を取得することができます、<xref:System.AppDomain.Id%2A>プロパティを呼び出すことによって[GetCurrentAppDomainId メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="5da06-130">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5da06-131">要件</span><span class="sxs-lookup"><span data-stu-id="5da06-131">Requirements</span></span>  
 <span data-ttu-id="5da06-132">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5da06-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5da06-133">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5da06-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5da06-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="5da06-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5da06-135">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5da06-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5da06-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="5da06-136">See Also</span></span>  
 [<span data-ttu-id="5da06-137">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5da06-137">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
