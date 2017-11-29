---
title: ".NET Framework 4 および 4.5 で追加された CLR ホスト インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
caps.latest.revision: "26"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 65d80734bfbe16c8b5052f8de1e4c6280b663707
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a><span data-ttu-id="9454a-102">.NET Framework 4 および 4.5 で追加された CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9454a-102">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>
<span data-ttu-id="9454a-103">アンマネージ インターフェイスについて説明ホストを使用して、共通言語ランタイム (CLR) 統合、 [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]、 [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]、以降のバージョンのアプリケーションにします。</span><span class="sxs-lookup"><span data-stu-id="9454a-103">This section describes interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], and later versions into their applications.</span></span> <span data-ttu-id="9454a-104">これらのインターフェイスは、ホストを構成して、ランタイムをプロセスに読み込むのためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="9454a-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
 <span data-ttu-id="9454a-105">以降で、 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]、すべてのホスト インターフェイスで次の特性があります。</span><span class="sxs-lookup"><span data-stu-id="9454a-105">Starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], all hosting interfaces have the following characteristics:</span></span>  
  
-   <span data-ttu-id="9454a-106">有効期間の管理を使用する (`AddRef`と`Release`)、(暗黙的なコンテキストなど) をカプセル化し、 `QueryInterface` COM から</span><span class="sxs-lookup"><span data-stu-id="9454a-106">They use lifetime management (`AddRef` and `Release`), encapsulation (implicit context) and `QueryInterface` from COM.</span></span>  
  
-   <span data-ttu-id="9454a-107">ある型を使用しない COM など`BSTR`、 `SAFEARRAY`、または`VARIANT`です。</span><span class="sxs-lookup"><span data-stu-id="9454a-107">There do not use COM types such as `BSTR`, `SAFEARRAY`, or `VARIANT`.</span></span>  
  
-   <span data-ttu-id="9454a-108">アパートメント モデル、集計、またはレジストリのライセンス認証を使用するがない、 [CoCreateInstance 関数](http://go.microsoft.com/fwlink/?LinkId=142894)です。</span><span class="sxs-lookup"><span data-stu-id="9454a-108">There are no apartment models, aggregation, or registry activation that use the [CoCreateInstance function](http://go.microsoft.com/fwlink/?LinkId=142894).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9454a-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="9454a-109">In This Section</span></span>  
 [<span data-ttu-id="9454a-110">ICLRAppDomainResourceMonitor インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9454a-110">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 <span data-ttu-id="9454a-111">アプリケーション ドメインのメモリおよび CPU 使用率を検査するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="9454a-111">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
 [<span data-ttu-id="9454a-112">ICLRDomainManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9454a-112">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 <span data-ttu-id="9454a-113">ホストが初期化プロパティを指定して既定のアプリケーション ドメインを初期化するために使用されるアプリケーション ドメイン マネージャーを指定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="9454a-113">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
 [<span data-ttu-id="9454a-114">ICLRGCManager2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9454a-114">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)  
 <span data-ttu-id="9454a-115">提供、 [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)メソッドにより、ガベージ コレクション セグメントのサイズと、ガベージ コレクション システムのジェネレーション 0 の最大サイズに設定する値を超えるホストを`DWORD`です。</span><span class="sxs-lookup"><span data-stu-id="9454a-115">Provides the [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method, which enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="9454a-116">ICLRMetaHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9454a-116">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 <span data-ttu-id="9454a-117">CLR の特定のバージョンを返す、インストールされている Clr のすべてを一覧表示、すべてのプロセスのランタイムを一覧表示、アクティブ化インターフェイスを返すおよびアセンブリをコンパイルするために使用する CLR バージョンを検出するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="9454a-117">Provides methods that return a specific version of the CLR, list all installed CLRs, list all in-process runtimes, return the activation interface, and discover the CLR version used to compile an assembly.</span></span>  
  
 [<span data-ttu-id="9454a-118">ICLRMetaHostPolicy インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9454a-118">ICLRMetaHostPolicy Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 <span data-ttu-id="9454a-119">提供、 [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)ポリシーの条件、マネージ アセンブリをバージョン、および構成ファイルに基づいて、CLR インターフェイスを提供するメソッド。</span><span class="sxs-lookup"><span data-stu-id="9454a-119">Provides the [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method that provides a CLR interface based on policy criteria, managed assembly, version, and configuration file.</span></span>  
  
 [<span data-ttu-id="9454a-120">ICLRRuntimeInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9454a-120">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 <span data-ttu-id="9454a-121">バージョン、ディレクトリ、負荷の状態など、特定のランタイムに関する情報を返すメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="9454a-121">Provides methods that return information about a specific runtime, including version, directory, and load status.</span></span>  
  
 [<span data-ttu-id="9454a-122">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9454a-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 <span data-ttu-id="9454a-123">厳密な名前によるアセンブリの署名の基本的なグローバル静的関数を提供します。</span><span class="sxs-lookup"><span data-stu-id="9454a-123">Provides basic global static functions for signing assemblies with strong names.</span></span> <span data-ttu-id="9454a-124">すべての[ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)メソッドは、標準の COM Hresult を返します。</span><span class="sxs-lookup"><span data-stu-id="9454a-124">All the [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) methods return standard COM HRESULTs.</span></span>  
  
 [<span data-ttu-id="9454a-125">ICLRStrongName2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9454a-125">ICLRStrongName2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname2-interface.md)  
 <span data-ttu-id="9454a-126">Sha-2 グループ (sha-256、sha-384、および sha-512) のセキュリティで保護されたハッシュ アルゴリズムを使用する厳密な名前を作成する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="9454a-126">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
 [<span data-ttu-id="9454a-127">ICLRTask2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9454a-127">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 <span data-ttu-id="9454a-128">すべての機能を提供、 [ICLRTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)以外の場合はさらに、現在のスレッドで遅延するスレッドの中止できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="9454a-128">Provides all the functionality of the [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9454a-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="9454a-129">Related Sections</span></span>  
 [<span data-ttu-id="9454a-130">サポートされなくなった CLR ホスト インターフェイスおよびコクラス</span><span class="sxs-lookup"><span data-stu-id="9454a-130">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="9454a-131">.NET Framework バージョン 1.0 および 1.1 で提供されるホスティング インターフェイスをについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9454a-131">Describes the hosting interfaces provided with the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="9454a-132">CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9454a-132">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="9454a-133">.NET Framework バージョン 2.0、3.0、および 3.5 で提供されるホスティング インターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9454a-133">Describes the hosting interfaces provided with the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
 [<span data-ttu-id="9454a-134">ホスティング</span><span class="sxs-lookup"><span data-stu-id="9454a-134">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 <span data-ttu-id="9454a-135">.NET Framework でのホスティングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9454a-135">Introduces hosting in the .NET Framework.</span></span>
