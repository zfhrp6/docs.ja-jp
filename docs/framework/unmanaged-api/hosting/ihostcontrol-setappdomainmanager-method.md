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
ms.openlocfilehash: 97e853bc74babca5b5400953b63714a13419fcaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ihostcontrolsetappdomainmanager-method"></a><span data-ttu-id="c8f00-102">IHostControl::SetAppDomainManager メソッド</span><span class="sxs-lookup"><span data-stu-id="c8f00-102">IHostControl::SetAppDomainManager Method</span></span>
<span data-ttu-id="c8f00-103">アプリケーション ドメインが作成されているホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="c8f00-103">Notifies the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8f00-104">構文</span><span class="sxs-lookup"><span data-stu-id="c8f00-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c8f00-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c8f00-105">Parameters</span></span>  
 `dwAppDomainID`  
 <span data-ttu-id="c8f00-106">[in]選択された数値識別子<xref:System.AppDomain>です。</span><span class="sxs-lookup"><span data-stu-id="c8f00-106">[in] The numeric identifier of the selected <xref:System.AppDomain>.</span></span>  
  
 `pUnkAppDomainManager`  
 <span data-ttu-id="c8f00-107">[in]ポインター、<xref:System.AppDomainManager>としてホストを実装するオブジェクト`IUnknown`です。</span><span class="sxs-lookup"><span data-stu-id="c8f00-107">[in] A pointer to the <xref:System.AppDomainManager> object that the host implements as `IUnknown`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c8f00-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="c8f00-108">Return Value</span></span>  
  
|<span data-ttu-id="c8f00-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c8f00-109">HRESULT</span></span>|<span data-ttu-id="c8f00-110">説明</span><span class="sxs-lookup"><span data-stu-id="c8f00-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c8f00-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c8f00-111">S_OK</span></span>|<span data-ttu-id="c8f00-112">`SetAppDomainManager`正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="c8f00-112">`SetAppDomainManager` returned successfully.</span></span>|  
|<span data-ttu-id="c8f00-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c8f00-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c8f00-114">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="c8f00-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c8f00-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c8f00-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c8f00-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="c8f00-116">The call timed out.</span></span>|  
|<span data-ttu-id="c8f00-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c8f00-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c8f00-118">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="c8f00-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c8f00-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c8f00-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c8f00-120">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="c8f00-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c8f00-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c8f00-121">E_FAIL</span></span>|<span data-ttu-id="c8f00-122">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="c8f00-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c8f00-123">メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="c8f00-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c8f00-124">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="c8f00-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8f00-125">コメント</span><span class="sxs-lookup"><span data-stu-id="c8f00-125">Remarks</span></span>  
 <span data-ttu-id="c8f00-126"><xref:System.AppDomainManager>ホストのメカニズムを提供してマネージ コードにブートス トラップを作成し、それぞれの設定を制御<xref:System.AppDomain>です。</span><span class="sxs-lookup"><span data-stu-id="c8f00-126">The <xref:System.AppDomainManager> provides the host with a mechanism to bootstrap into managed code and to control the creation and settings of each <xref:System.AppDomain>.</span></span> <span data-ttu-id="c8f00-127"><xref:System.AppDomainManager>はそれぞれに読み込まれます<xref:System.AppDomain>ときを<xref:System.AppDomain>を作成します。</span><span class="sxs-lookup"><span data-stu-id="c8f00-127">The <xref:System.AppDomainManager> is loaded into each <xref:System.AppDomain> when that <xref:System.AppDomain> is created.</span></span> <span data-ttu-id="c8f00-128">その選択した場合、CLR をホストに通知の値を設定して、アプリケーション ドメインが作成されている、`pUnkAppDomainManager`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="c8f00-128">If it chooses, the CLR notifies the host that the application domain has been created by setting the value of the `pUnkAppDomainManager` parameter.</span></span>  
  
 <span data-ttu-id="c8f00-129">実装で、`SetAppDomainManager`メソッド、ホストを設定できますアセンブリの名前と種類のアプリケーション ドメイン マネージャー。</span><span class="sxs-lookup"><span data-stu-id="c8f00-129">In its implementation of the `SetAppDomainManager` method, the host can set the assembly name and type for the application domain manager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8f00-130">要件</span><span class="sxs-lookup"><span data-stu-id="c8f00-130">Requirements</span></span>  
 <span data-ttu-id="c8f00-131">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c8f00-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8f00-132">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c8f00-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c8f00-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="c8f00-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c8f00-134">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8f00-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8f00-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="c8f00-135">See Also</span></span>  
 <xref:System.AppDomain>  
 <xref:System.AppDomainManager>  
 [<span data-ttu-id="c8f00-136">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c8f00-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
