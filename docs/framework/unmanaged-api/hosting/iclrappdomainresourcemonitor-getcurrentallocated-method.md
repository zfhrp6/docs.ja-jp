---
title: "ICLRAppDomainResourceMonitor::GetCurrentAllocated メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAppDomainResourceMonitor.GetCurrentAllocated
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAppDomainResourceMonitor::GetCurrentAllocated
helpviewer_keywords:
- GetCurrentAllocated method [.NET Framework hosting]
- ICLRAppDomainResourceMonitor::GetCurrentAllocated method [.NET Framework hosting]
ms.assetid: 7bab209c-efd4-44c2-af30-61abab0ae2fc
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dee616e1fbd071662a42af856fa2cd51f7bdd5d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrappdomainresourcemonitorgetcurrentallocated-method"></a><span data-ttu-id="3ac7d-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated メソッド</span><span class="sxs-lookup"><span data-stu-id="3ac7d-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated Method</span></span>
<span data-ttu-id="3ac7d-103">(バイト単位) の作成後、ガベージ コレクションが行われたメモリ差し引かれません、アプリケーション ドメインによって行われたすべてのメモリ割り当ての合計サイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="3ac7d-103">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ac7d-104">構文</span><span class="sxs-lookup"><span data-stu-id="3ac7d-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentAllocated([in]  DWORD dwAppDomainId,  
                            [out] ULONGLONG* pBytesAllocated);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3ac7d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3ac7d-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="3ac7d-106">[in]要求されたアプリケーション ドメインの ID。</span><span class="sxs-lookup"><span data-stu-id="3ac7d-106">[in] The ID of the requested application domain.</span></span>  
  
 `pBytesAllocated`  
 <span data-ttu-id="3ac7d-107">[out]すべてのメモリ割り当ての合計サイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3ac7d-107">[out] A pointer to the total size of all memory allocations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ac7d-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="3ac7d-108">Return Value</span></span>  
 <span data-ttu-id="3ac7d-109">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="3ac7d-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="3ac7d-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3ac7d-110">HRESULT</span></span>|<span data-ttu-id="3ac7d-111">説明</span><span class="sxs-lookup"><span data-stu-id="3ac7d-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3ac7d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="3ac7d-112">S_OK</span></span>|<span data-ttu-id="3ac7d-113">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="3ac7d-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="3ac7d-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="3ac7d-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="3ac7d-115">アプリケーション ドメインがアンロードされたか、存在しません。</span><span class="sxs-lookup"><span data-stu-id="3ac7d-115">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ac7d-116">コメント</span><span class="sxs-lookup"><span data-stu-id="3ac7d-116">Remarks</span></span>  
 <span data-ttu-id="3ac7d-117">このメソッドは、アンマネージ相当するマネージ<xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="3ac7d-117">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ac7d-118">要件</span><span class="sxs-lookup"><span data-stu-id="3ac7d-118">Requirements</span></span>  
 <span data-ttu-id="3ac7d-119">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3ac7d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ac7d-120">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="3ac7d-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3ac7d-121">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="3ac7d-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3ac7d-122">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ac7d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ac7d-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="3ac7d-123">See Also</span></span>  
 [<span data-ttu-id="3ac7d-124">ICLRAppDomainResourceMonitor インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3ac7d-124">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [<span data-ttu-id="3ac7d-125">アプリケーション ドメインのリソース監視</span><span class="sxs-lookup"><span data-stu-id="3ac7d-125">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [<span data-ttu-id="3ac7d-126">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3ac7d-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="3ac7d-127">ホスティング</span><span class="sxs-lookup"><span data-stu-id="3ac7d-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
