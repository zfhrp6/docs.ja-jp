---
title: "ICLRAppDomainResourceMonitor インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAppDomainResourceMonitor
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAppDomainResourceMonitor
helpviewer_keywords: ICLRAppDomainResourceMonitor interface [.NET Framework hosting]
ms.assetid: 72fa83a1-8997-41d7-b355-ab177a24a303
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1bebd39fce4f6aa6f570b3af348332bf7bcc87ad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrappdomainresourcemonitor-interface"></a><span data-ttu-id="06f1b-102">ICLRAppDomainResourceMonitor インターフェイス</span><span class="sxs-lookup"><span data-stu-id="06f1b-102">ICLRAppDomainResourceMonitor Interface</span></span>
<span data-ttu-id="06f1b-103">アプリケーション ドメインのメモリおよび CPU 使用率を検査するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="06f1b-103">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="06f1b-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="06f1b-104">Methods</span></span>  
  
|<span data-ttu-id="06f1b-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="06f1b-105">Method</span></span>|<span data-ttu-id="06f1b-106">説明</span><span class="sxs-lookup"><span data-stu-id="06f1b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="06f1b-107">GetCurrentAllocated メソッド</span><span class="sxs-lookup"><span data-stu-id="06f1b-107">GetCurrentAllocated Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md)|<span data-ttu-id="06f1b-108">(バイト単位) の作成後、ガベージ コレクションが行われたメモリ差し引かれません、アプリケーション ドメインによって行われたすべてのメモリ割り当ての合計サイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="06f1b-108">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>|  
|[<span data-ttu-id="06f1b-109">GetCurrentSurvived メソッド</span><span class="sxs-lookup"><span data-stu-id="06f1b-109">GetCurrentSurvived Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md)|<span data-ttu-id="06f1b-110">最後のフル ブロッキング ガベージ コレクションで残ったをして、現在のアプリケーション ドメインによって参照されているバイト数を取得します。</span><span class="sxs-lookup"><span data-stu-id="06f1b-110">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>|  
|[<span data-ttu-id="06f1b-111">GetCurrentCpuTime メソッド</span><span class="sxs-lookup"><span data-stu-id="06f1b-111">GetCurrentCpuTime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md)|<span data-ttu-id="06f1b-112">アプリケーション ドメインが作成されたため、現在のアプリケーション ドメインで実行中にすべてのスレッドによって使用されている合計プロセッサ時間を取得します。</span><span class="sxs-lookup"><span data-stu-id="06f1b-112">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06f1b-113">コメント</span><span class="sxs-lookup"><span data-stu-id="06f1b-113">Remarks</span></span>  
 <span data-ttu-id="06f1b-114">`ICLRAppDomainResourceMonitor`インターフェイスには、次のマネージ プロパティを次のような機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="06f1b-114">The `ICLRAppDomainResourceMonitor` interface provides functionality that is similar to the following managed properties:</span></span>  
  
-   <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>  
  
## <a name="requirements"></a><span data-ttu-id="06f1b-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="06f1b-115">Requirements</span></span>  
 <span data-ttu-id="06f1b-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="06f1b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06f1b-117">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="06f1b-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="06f1b-118">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="06f1b-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="06f1b-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06f1b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06f1b-120">参照</span><span class="sxs-lookup"><span data-stu-id="06f1b-120">See Also</span></span>  
 [<span data-ttu-id="06f1b-121">\<appDomainResourceMonitoring > 要素</span><span class="sxs-lookup"><span data-stu-id="06f1b-121">\<appDomainResourceMonitoring> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)  
 [<span data-ttu-id="06f1b-122">アプリケーション ドメインのリソース監視</span><span class="sxs-lookup"><span data-stu-id="06f1b-122">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [<span data-ttu-id="06f1b-123">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="06f1b-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="06f1b-124">ホスティング</span><span class="sxs-lookup"><span data-stu-id="06f1b-124">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
