---
title: "ICLRRuntimeHost::ExecuteApplication メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.ExecuteApplication
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::ExecuteApplication
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteApplication method [.NET Framework hosting]
- ExecuteApplication method [.NET Framework hosting]
ms.assetid: 5f28cc4e-7176-4e00-aa1f-58ae6ee52fe4
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3b43365ad208dae5b28b31cf494de37ca670d791
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimehostexecuteapplication-method"></a><span data-ttu-id="56ef1-102">ICLRRuntimeHost::ExecuteApplication メソッド</span><span class="sxs-lookup"><span data-stu-id="56ef1-102">ICLRRuntimeHost::ExecuteApplication Method</span></span>
<span data-ttu-id="56ef1-103">新しいドメインでアクティブにするアプリケーションを指定するマニフェストに基づく ClickOnce の配置シナリオに使用されます。</span><span class="sxs-lookup"><span data-stu-id="56ef1-103">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span> <span data-ttu-id="56ef1-104">これらのシナリオの詳細については、次を参照してください。 [ClickOnce のセキュリティと配置](/visualstudio/deployment/clickonce-security-and-deployment)です。</span><span class="sxs-lookup"><span data-stu-id="56ef1-104">For more information about these scenarios, see [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56ef1-105">構文</span><span class="sxs-lookup"><span data-stu-id="56ef1-105">Syntax</span></span>  
  
```  
HRESULT ExecuteApplication(  
    [in] LPCWSTR   pwzAppFullName,  
    [in] DWORD     dwManifestPaths,  
    [in] LPCWSTR   *ppwzManifestPaths,  
    [in] DWORD     dwActivationData,  
    [in] LPCWSTR   *ppwzActivationData,  
    [out] int      *pReturnValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="56ef1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="56ef1-106">Parameters</span></span>  
 `pwzAppFullName`  
 <span data-ttu-id="56ef1-107">[in]に対して定義されていると、アプリケーションの完全名<xref:System.ApplicationIdentity>です。</span><span class="sxs-lookup"><span data-stu-id="56ef1-107">[in] The full name of the application, as defined for <xref:System.ApplicationIdentity>.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="56ef1-108">[in]含まれる文字列の数、`ppwzManifestPaths`配列。</span><span class="sxs-lookup"><span data-stu-id="56ef1-108">[in] The number of strings contained in the `ppwzManifestPaths` array.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="56ef1-109">[in] オプション。</span><span class="sxs-lookup"><span data-stu-id="56ef1-109">[in] Optional.</span></span> <span data-ttu-id="56ef1-110">アプリケーションのマニフェストのパスを格納する文字列配列。</span><span class="sxs-lookup"><span data-stu-id="56ef1-110">A string array that contains manifest paths for the application.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="56ef1-111">[in]含まれる文字列の数、`ppwzActivationData`配列。</span><span class="sxs-lookup"><span data-stu-id="56ef1-111">[in] The number of strings contained in the `ppwzActivationData` array.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="56ef1-112">[in] オプション。</span><span class="sxs-lookup"><span data-stu-id="56ef1-112">[in] Optional.</span></span> <span data-ttu-id="56ef1-113">Web 経由で配置されたアプリケーションの URL のクエリ文字列部分などのアプリケーションのライセンス認証データを格納する文字列配列。</span><span class="sxs-lookup"><span data-stu-id="56ef1-113">A string array that contains the application's activation data, such as the query string portion of the URL for applications deployed over the Web.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="56ef1-114">[out]アプリケーションのエントリ ポイントから返される値。</span><span class="sxs-lookup"><span data-stu-id="56ef1-114">[out] The value returned from the entry point of the application.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56ef1-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="56ef1-115">Return Value</span></span>  
  
|<span data-ttu-id="56ef1-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="56ef1-116">HRESULT</span></span>|<span data-ttu-id="56ef1-117">説明</span><span class="sxs-lookup"><span data-stu-id="56ef1-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="56ef1-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="56ef1-118">S_OK</span></span>|<span data-ttu-id="56ef1-119">`ExecuteApplication`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="56ef1-119">`ExecuteApplication` returned successfully.</span></span>|  
|<span data-ttu-id="56ef1-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="56ef1-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="56ef1-121">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="56ef1-121">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="56ef1-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="56ef1-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="56ef1-123">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="56ef1-123">The call timed out.</span></span>|  
|<span data-ttu-id="56ef1-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="56ef1-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="56ef1-125">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="56ef1-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="56ef1-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="56ef1-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="56ef1-127">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="56ef1-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="56ef1-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="56ef1-128">E_FAIL</span></span>|<span data-ttu-id="56ef1-129">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="56ef1-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="56ef1-130">メソッドには、E_FAIL が返された場合、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="56ef1-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="56ef1-131">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="56ef1-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56ef1-132">コメント</span><span class="sxs-lookup"><span data-stu-id="56ef1-132">Remarks</span></span>  
 <span data-ttu-id="56ef1-133">`ExecuteApplication`新しく作成されたアプリケーション ドメインで ClickOnce アプリケーションをアクティブ化に使用されます。</span><span class="sxs-lookup"><span data-stu-id="56ef1-133">`ExecuteApplication` is used to activate ClickOnce applications in a newly created application domain.</span></span>  
  
 <span data-ttu-id="56ef1-134">`pReturnValue`出力パラメーターは、アプリケーションによって返される値に設定します。</span><span class="sxs-lookup"><span data-stu-id="56ef1-134">The `pReturnValue` output parameter is set to the value returned by the application.</span></span> <span data-ttu-id="56ef1-135">場合は null の値を指定する場合`pReturnValue`、`ExecuteApplication`は失敗しませんが、値を返しません。</span><span class="sxs-lookup"><span data-stu-id="56ef1-135">If you supply a value of null for `pReturnValue`, `ExecuteApplication` does not fail, but it does not return a value.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="56ef1-136">呼び出す必要はありません、 [Start メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)メソッドを呼び出す前に、`ExecuteApplication`マニフェスト ベースのアプリケーションをアクティブ化するメソッド。</span><span class="sxs-lookup"><span data-stu-id="56ef1-136">Do not call the [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method before calling the `ExecuteApplication` method to activate a manifest-based application.</span></span> <span data-ttu-id="56ef1-137">場合、`Start`メソッドが最初と呼ばれる、`ExecuteApplication`メソッドの呼び出しは失敗します。</span><span class="sxs-lookup"><span data-stu-id="56ef1-137">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56ef1-138">要件</span><span class="sxs-lookup"><span data-stu-id="56ef1-138">Requirements</span></span>  
 <span data-ttu-id="56ef1-139">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="56ef1-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56ef1-140">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="56ef1-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="56ef1-141">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="56ef1-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="56ef1-142">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56ef1-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56ef1-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="56ef1-143">See Also</span></span>  
 <xref:System.ActivationContext>  
 <xref:System.AppDomainManager>  
 <xref:System.ApplicationIdentity>  
 [<span data-ttu-id="56ef1-144">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="56ef1-144">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [<span data-ttu-id="56ef1-145">SetAppDomainManager メソッド</span><span class="sxs-lookup"><span data-stu-id="56ef1-145">SetAppDomainManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)  
 [<span data-ttu-id="56ef1-146">チュートリアル : デザイナーを使用し、ClickOnce 配置 API で必要に応じてアセンブリをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="56ef1-146">Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API Using the Designer</span></span>](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)
