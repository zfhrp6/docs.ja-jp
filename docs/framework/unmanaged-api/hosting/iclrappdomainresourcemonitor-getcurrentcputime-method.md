---
title: ICLRAppDomainResourceMonitor::GetCurrentCpuTime メソッド
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentCpuTime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime method [.NET Framework hosting]
- GetCurrentCpuTime method [.NET Framework hosting]
ms.assetid: ebc9cc33-fcd6-4cae-9ecb-ea21c51874e6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53deeab574716a426c1c4617abe279e72f27c04e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433522"
---
# <a name="iclrappdomainresourcemonitorgetcurrentcputime-method"></a><span data-ttu-id="d15bd-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime メソッド</span><span class="sxs-lookup"><span data-stu-id="d15bd-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime Method</span></span>
<span data-ttu-id="d15bd-103">アプリケーション ドメインが作成されたため、現在のアプリケーション ドメインで実行中にすべてのスレッドによって使用されている合計プロセッサ時間を取得します。</span><span class="sxs-lookup"><span data-stu-id="d15bd-103">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d15bd-104">構文</span><span class="sxs-lookup"><span data-stu-id="d15bd-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentCpuTime([in]  DWORD dwAppDomainId,  
                          [out] ULONGLONG* pMilliseconds);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d15bd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d15bd-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="d15bd-106">[in]要求されたアプリケーション ドメインの ID。</span><span class="sxs-lookup"><span data-stu-id="d15bd-106">[in] The ID of the requested application domain.</span></span>  
  
 `pMilliseconds`  
 <span data-ttu-id="d15bd-107">[out]アプリケーション ドメインが作成されたため、現在のアプリケーション ドメインで実行中にすべてのスレッドによって使用されているプロセッサの合計時間へのポインター。</span><span class="sxs-lookup"><span data-stu-id="d15bd-107">[out] A pointer to the total processor time that has been used by all threads while executing in the current application domain since the application domain was created.</span></span> <span data-ttu-id="d15bd-108">このパラメーターは、`null` に設定できます。</span><span class="sxs-lookup"><span data-stu-id="d15bd-108">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d15bd-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="d15bd-109">Return Value</span></span>  
  
|<span data-ttu-id="d15bd-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d15bd-110">HRESULT</span></span>|<span data-ttu-id="d15bd-111">説明</span><span class="sxs-lookup"><span data-stu-id="d15bd-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d15bd-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="d15bd-112">S_OK</span></span>|<span data-ttu-id="d15bd-113">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="d15bd-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="d15bd-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="d15bd-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="d15bd-115">アプリケーション ドメインがアンロードされたか、存在しません。</span><span class="sxs-lookup"><span data-stu-id="d15bd-115">The application domain has been unloaded or does not exist.</span></span>|  
|<span data-ttu-id="d15bd-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d15bd-116">E_FAIL</span></span>|<span data-ttu-id="d15bd-117">アプリケーション ドメインのリソースの監視が有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="d15bd-117">Application domain resource monitoring is not enabled.</span></span><br /><br /> <span data-ttu-id="d15bd-118">- または -</span><span class="sxs-lookup"><span data-stu-id="d15bd-118">-or-</span></span><br /><br /> <span data-ttu-id="d15bd-119">その他のすべてのエラーです。</span><span class="sxs-lookup"><span data-stu-id="d15bd-119">All other failures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d15bd-120">コメント</span><span class="sxs-lookup"><span data-stu-id="d15bd-120">Remarks</span></span>  
 <span data-ttu-id="d15bd-121">このメソッドは、アンマネージ相当するマネージ<xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="d15bd-121">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d15bd-122">要件</span><span class="sxs-lookup"><span data-stu-id="d15bd-122">Requirements</span></span>  
 <span data-ttu-id="d15bd-123">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d15bd-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d15bd-124">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="d15bd-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d15bd-125">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="d15bd-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d15bd-126">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d15bd-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d15bd-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="d15bd-127">See Also</span></span>  
 [<span data-ttu-id="d15bd-128">ICLRAppDomainResourceMonitor インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d15bd-128">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [<span data-ttu-id="d15bd-129">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d15bd-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="d15bd-130">アプリケーション ドメインのリソース監視</span><span class="sxs-lookup"><span data-stu-id="d15bd-130">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [<span data-ttu-id="d15bd-131">ホスティング</span><span class="sxs-lookup"><span data-stu-id="d15bd-131">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
