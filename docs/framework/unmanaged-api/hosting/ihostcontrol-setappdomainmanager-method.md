---
title: "IHostControl::SetAppDomainManager メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostControl.SetAppDomainManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostControl::SetAppDomainManager
helpviewer_keywords:
- IHostControl::SetAppDomainManager method [.NET Framework hosting]
- SetAppDomainManager method [.NET Framework hosting]
ms.assetid: 6562bbe7-0d67-4c50-a958-3a18cf680375
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d689a664f5bad19a70a8d635beb1f25f33da6ff6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihostcontrolsetappdomainmanager-method"></a><span data-ttu-id="44d54-102">IHostControl::SetAppDomainManager メソッド</span><span class="sxs-lookup"><span data-stu-id="44d54-102">IHostControl::SetAppDomainManager Method</span></span>
<span data-ttu-id="44d54-103">アプリケーション ドメインが作成されているホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="44d54-103">Notifies the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44d54-104">構文</span><span class="sxs-lookup"><span data-stu-id="44d54-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="44d54-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="44d54-105">Parameters</span></span>  
 `dwAppDomainID`  
 <span data-ttu-id="44d54-106">[in]選択された数値識別子<xref:System.AppDomain>です。</span><span class="sxs-lookup"><span data-stu-id="44d54-106">[in] The numeric identifier of the selected <xref:System.AppDomain>.</span></span>  
  
 `pUnkAppDomainManager`  
 <span data-ttu-id="44d54-107">[in]ポインター、<xref:System.AppDomainManager>としてホストを実装するオブジェクト`IUnknown`です。</span><span class="sxs-lookup"><span data-stu-id="44d54-107">[in] A pointer to the <xref:System.AppDomainManager> object that the host implements as `IUnknown`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44d54-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="44d54-108">Return Value</span></span>  
  
|<span data-ttu-id="44d54-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="44d54-109">HRESULT</span></span>|<span data-ttu-id="44d54-110">説明</span><span class="sxs-lookup"><span data-stu-id="44d54-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="44d54-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="44d54-111">S_OK</span></span>|<span data-ttu-id="44d54-112">`SetAppDomainManager`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="44d54-112">`SetAppDomainManager` returned successfully.</span></span>|  
|<span data-ttu-id="44d54-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="44d54-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="44d54-114">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="44d54-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="44d54-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="44d54-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="44d54-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="44d54-116">The call timed out.</span></span>|  
|<span data-ttu-id="44d54-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="44d54-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="44d54-118">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="44d54-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="44d54-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="44d54-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="44d54-120">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="44d54-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="44d54-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="44d54-121">E_FAIL</span></span>|<span data-ttu-id="44d54-122">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="44d54-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="44d54-123">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="44d54-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="44d54-124">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="44d54-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44d54-125">コメント</span><span class="sxs-lookup"><span data-stu-id="44d54-125">Remarks</span></span>  
 <span data-ttu-id="44d54-126"><xref:System.AppDomainManager>ホストのメカニズムを提供してマネージ コードにブートス トラップを作成し、それぞれの設定を制御<xref:System.AppDomain>です。</span><span class="sxs-lookup"><span data-stu-id="44d54-126">The <xref:System.AppDomainManager> provides the host with a mechanism to bootstrap into managed code and to control the creation and settings of each <xref:System.AppDomain>.</span></span> <span data-ttu-id="44d54-127"><xref:System.AppDomainManager>はそれぞれに読み込まれます<xref:System.AppDomain>ときを<xref:System.AppDomain>を作成します。</span><span class="sxs-lookup"><span data-stu-id="44d54-127">The <xref:System.AppDomainManager> is loaded into each <xref:System.AppDomain> when that <xref:System.AppDomain> is created.</span></span> <span data-ttu-id="44d54-128">その選択した場合、CLR をホストに通知の値を設定して、アプリケーション ドメインが作成されている、`pUnkAppDomainManager`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="44d54-128">If it chooses, the CLR notifies the host that the application domain has been created by setting the value of the `pUnkAppDomainManager` parameter.</span></span>  
  
 <span data-ttu-id="44d54-129">実装で、`SetAppDomainManager`メソッド、ホストを設定できますアセンブリの名前と種類のアプリケーション ドメイン マネージャー。</span><span class="sxs-lookup"><span data-stu-id="44d54-129">In its implementation of the `SetAppDomainManager` method, the host can set the assembly name and type for the application domain manager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44d54-130">必要条件</span><span class="sxs-lookup"><span data-stu-id="44d54-130">Requirements</span></span>  
 <span data-ttu-id="44d54-131">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="44d54-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44d54-132">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="44d54-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="44d54-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="44d54-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="44d54-134">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44d54-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44d54-135">参照</span><span class="sxs-lookup"><span data-stu-id="44d54-135">See Also</span></span>  
 <xref:System.AppDomain>  
 <xref:System.AppDomainManager>  
 [<span data-ttu-id="44d54-136">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="44d54-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
