---
title: "ランタイム プロファイリング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance counters
- common language runtime, profiling
- Perfmon.exe
- System Monitor
- profiling
- runtime, profiling
- profiling applications
- Performance Console
ms.assetid: ccd68284-f3a8-47b8-bc3f-92e5fe3a1640
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 876635cfe0349c734a61dcc827a6f9594bb2a5d7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="runtime-profiling"></a><span data-ttu-id="a3e08-102">ランタイム プロファイリング</span><span class="sxs-lookup"><span data-stu-id="a3e08-102">Runtime Profiling</span></span>
<span data-ttu-id="a3e08-103">プロファイリングは、任意の開発シナリオまたは配置シナリオでパフォーマンス データを収集する方法の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="a3e08-103">Profiling is a method of gathering performance data in any development or deployment scenario.</span></span> <span data-ttu-id="a3e08-104">このセクションは、アプリケーションのパフォーマンスに関する情報の収集を必要とする開発者およびシステム管理者を対象にしています。</span><span class="sxs-lookup"><span data-stu-id="a3e08-104">This section is for developers and system administrators who want to gather information about application performance.</span></span>  
  
## <a name="tracking-performance-using-the-performance-monitor-perfmonexe"></a><span data-ttu-id="a3e08-105">パフォーマンス モニター (Perfmon.exe) を使用したパフォーマンスの追跡</span><span class="sxs-lookup"><span data-stu-id="a3e08-105">Tracking Performance Using the Performance Monitor (Perfmon.exe)</span></span>  
 <span data-ttu-id="a3e08-106">パフォーマンス モニターは、 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] アプリケーションをプロファイリングする場合に最も使いやすいツールです。</span><span class="sxs-lookup"><span data-stu-id="a3e08-106">The Performance Monitor is the easiest tool to use to profile your [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] application.</span></span> <span data-ttu-id="a3e08-107">パフォーマンス モニターは、共通言語ランタイムおよび [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]と共にインストールされる .NET Framework パフォーマンス カウンター内のデータをグラフィカルに表示します。</span><span class="sxs-lookup"><span data-stu-id="a3e08-107">The Performance Monitor graphically represents data found in the .NET Framework performance counters that are installed with the common language runtime and the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span> <span data-ttu-id="a3e08-108">これらのカウンターを使用することにより、メモリ管理から Just-In-Time (JIT) コンパイラのパフォーマンスまで、あらゆる情報を監視できます。</span><span class="sxs-lookup"><span data-stu-id="a3e08-108">These counters can be used to monitor everything from memory management to just-in-time (JIT) compiler performance.</span></span> <span data-ttu-id="a3e08-109">.NET パフォーマンス カウンターは、アプリケーションが使用するリソースに関する情報を提供します。この情報は、アプリケーションのパフォーマンスを判断するための間接的な指標となります。</span><span class="sxs-lookup"><span data-stu-id="a3e08-109">They tell you about the resources your application uses, which is an indirect measure of your application's performance.</span></span> <span data-ttu-id="a3e08-110">これらのカウンターは、アプリケーション内部の動作状況を把握するために使用します。</span><span class="sxs-lookup"><span data-stu-id="a3e08-110">Use these counters to understand how your application works internally.</span></span>  
  
#### <a name="to-run-perfmonexe-on-windows-vista-and-later-versions"></a><span data-ttu-id="a3e08-111">perfmon.exe を Windows Vista 以降のバージョンで実行するには</span><span class="sxs-lookup"><span data-stu-id="a3e08-111">To run Perfmon.exe on Windows Vista and later versions</span></span>  
  
1.  <span data-ttu-id="a3e08-112">コマンド プロンプトで、「 **perfmon**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a3e08-112">At the command prompt, type **perfmon**.</span></span> <span data-ttu-id="a3e08-113">**[パフォーマンス モニター]** コンソールが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3e08-113">The **Performance Monitor** console appears.</span></span>  
  
2.  <span data-ttu-id="a3e08-114">**[監視ツール]** フォルダーで、 **[パフォーマンス モニター]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a3e08-114">In the **Monitoring Tools** folder, click **Performance Monitor**.</span></span>  
  
3.  <span data-ttu-id="a3e08-115">パフォーマンス モニターのツールバーで、 **[追加]** アイコン (正符号) をクリックします (表示されている場合)。</span><span class="sxs-lookup"><span data-stu-id="a3e08-115">In the Performance Monitor toolbar, click the **Add** icon (the plus sign), if it is present.</span></span> <span data-ttu-id="a3e08-116">表示されていない場合は、モニター ウィンドウで右クリックし、 **[カウンターの追加]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="a3e08-116">If it is not present, right-click in the monitor window and select the **Add Counters** option.</span></span>  
  
     <span data-ttu-id="a3e08-117">**[接続の追加]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3e08-117">This opens the **Add Counters** dialog box.</span></span> <span data-ttu-id="a3e08-118">**[使用可能なカウンター]** リスト ボックスに、使用可能なパフォーマンス オブジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3e08-118">The **Available counters** list box displays the available performance objects.</span></span> <span data-ttu-id="a3e08-119">.NET Framework アプリケーション用には、さまざまな定義済みのオブジェクトがあります。これには、メモリ管理 (**.NET CLR メモリ**)、相互運用性 (**.NET CLR の相互運用性**)、例外処理 (**.NET CLR 例外**)、およびマルチスレッド (**.NET CLR LocksAndThreads**) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a3e08-119">There are a number of predefined objects for .NET Framework applications, including those for memory management (**.NET CLR Memory**), interoperability (**.NET CLR Interop**), exception handling (**.NET CLR Exceptions**), and multithreading (**.NET CLR LocksAndThreads**).</span></span> <span data-ttu-id="a3e08-120">各パフォーマンス オブジェクトには、個々 のパフォーマンス カウンターが多数含まれています。</span><span class="sxs-lookup"><span data-stu-id="a3e08-120">Each performance object includes a number of individual performance counters.</span></span> <span data-ttu-id="a3e08-121">パフォーマンス モニターで使用可能なパフォーマンス カウンターの一覧は、「 [Performance Counters](../../../docs/framework/debug-trace-profile/performance-counters.md)と共にインストールされる .NET Framework パフォーマンス カウンター内のデータをグラフィカルに表示します。</span><span class="sxs-lookup"><span data-stu-id="a3e08-121">For a list of the performance counters available in Performance Monitor, see [Performance Counters](../../../docs/framework/debug-trace-profile/performance-counters.md).</span></span>  
  
4.  <span data-ttu-id="a3e08-122">パフォーマンス オブジェクトの名前の横にあるチェック ボックスをオンにすると、サポートされている個々のパフォーマンス カウンターの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3e08-122">Select the check box next to a performance object's name to view the list of individual performance counters that it supports.</span></span>  
  
5.  <span data-ttu-id="a3e08-123">表示するパフォーマンス カウンターをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a3e08-123">Click the performance counter you want to view.</span></span>  
  
6.  <span data-ttu-id="a3e08-124">**[選択したオブジェクトのインスタンス]** リスト ボックスで、**[\<すべてのインスタンス>]** をクリックして、共通言語ランタイムのパフォーマンス カウンターをグローバルに (つまり、システム全体で) 監視するように指定します。</span><span class="sxs-lookup"><span data-stu-id="a3e08-124">In the **Instances of selected object** list box, click **\<All instances>** to specify that you want to monitor the performance counter for the common language runtime globally (that is, on a system-wide basis).</span></span>  
  
     <span data-ttu-id="a3e08-125">または</span><span class="sxs-lookup"><span data-stu-id="a3e08-125">-or-</span></span>  
  
     <span data-ttu-id="a3e08-126">**[選択したオブジェクトのインスタンス]** リスト ボックスで、アプリケーション名をクリックして、そのアプリケーションのパフォーマンス カウンターを監視します。</span><span class="sxs-lookup"><span data-stu-id="a3e08-126">In the **Instances of selected object** list box, click an application name to monitor the performance counter for that application.</span></span>  
  
     <span data-ttu-id="a3e08-127">複数のバージョンのランタイムを区別する必要がある場合、または同じ名前を持つ複数のアプリケーション間のあいまいさを解消する必要がある場合は、レジストリ キーも変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3e08-127">To differentiate multiple versions of the runtime, or to disambiguate multiple applications with the same name, you must also modify a registry key.</span></span> <span data-ttu-id="a3e08-128">詳細については、「 [Performance Counters and In-Process Side-By-Side Applications](../../../docs/framework/debug-trace-profile/performance-counters-and-in-process-side-by-side-applications.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3e08-128">For more information, see [Performance Counters and In-Process Side-By-Side Applications](../../../docs/framework/debug-trace-profile/performance-counters-and-in-process-side-by-side-applications.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3e08-129">パフォーマンス コンソールの実行中に新しいパフォーマンス カウンターがインストールされた場合は、新しいカウンターが表示されるように、パフォーマンス コンソールを停止して再起動してください。</span><span class="sxs-lookup"><span data-stu-id="a3e08-129">When new performance counters are installed while the Performance console is running, stop and restart the Performance console to make the new counters visible.</span></span>  
  
 <span data-ttu-id="a3e08-130">特定のゾーンまたはリモート共有に存在するアセンブリをプロファイリングする場合は、リモート アセンブリがパフォーマンス カウンターを実行するコンピューターに対して完全な信頼関係を持っていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a3e08-130">If you want to profile an assembly that exists in a zone or on a remote share, make sure that the remote assembly has full trust on the computer that runs the performance counters.</span></span> <span data-ttu-id="a3e08-131">アセンブリが十分な信頼関係を持っていない場合、パフォーマンス カウンターは機能しません。</span><span class="sxs-lookup"><span data-stu-id="a3e08-131">If the assembly does not have sufficient trust, the performance counters will not work.</span></span> <span data-ttu-id="a3e08-132">さまざまなゾーンへの信頼の付与については、「[Caspol.exe (コード アクセス セキュリティ ポリシー ツール)](../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3e08-132">For information about granting trust to different zones, see [Caspol.exe (Code Access Security Policy Tool)](../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3e08-133">[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] がインストールされているシステムでは、パフォーマンス モニターで、 **を使用して開発されたアプリケーションについて、** .NET CLR データ **や**.NET CLR ネットワーク [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)]などの一部のカテゴリでパフォーマンス カウンターのデータが表示されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="a3e08-133">On systems on which the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] is installed, the Performance Monitor may not display data for performance counters in some categories, such as **.NET CLR Data** and **.NET CLR Networking**, for applications that were developed using the [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)].</span></span> <span data-ttu-id="a3e08-134">このような場合、[\<forcePerformanceCounterUniqueSharedMemoryReads>](../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md) 要素をアプリケーションの構成ファイルに追加することで、このデータを表示するようにパフォーマンス モニターを構成できます。</span><span class="sxs-lookup"><span data-stu-id="a3e08-134">If this is the case, you can configure Performance Monitor to display this data by adding the [\<forcePerformanceCounterUniqueSharedMemoryReads>](../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md) element to the application's configuration file.</span></span>  
  
## <a name="reading-and-creating-performance-counters-programmatically"></a><span data-ttu-id="a3e08-135">プログラムを使用したパフォーマンス カウンターの読み取りと作成</span><span class="sxs-lookup"><span data-stu-id="a3e08-135">Reading and Creating Performance Counters Programmatically</span></span>  
 <span data-ttu-id="a3e08-136">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] には、パフォーマンス コンソールで利用できるものと同じパフォーマンス情報にコードからアクセスするのに使用するクラスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="a3e08-136">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] provides classes you can use to programmatically access the same performance information that is available in the Performance console.</span></span> <span data-ttu-id="a3e08-137">また、これらのクラスを使用すると、カスタム パフォーマンス カウンターを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a3e08-137">You can also use these classes to create custom performance counters.</span></span> <span data-ttu-id="a3e08-138">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]に用意されているパフォーマンス監視クラスの一部について、次の表に説明を示します。</span><span class="sxs-lookup"><span data-stu-id="a3e08-138">The following table describes some of the performance monitoring classes that are provided in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
|<span data-ttu-id="a3e08-139">クラス</span><span class="sxs-lookup"><span data-stu-id="a3e08-139">Class</span></span>|<span data-ttu-id="a3e08-140">説明</span><span class="sxs-lookup"><span data-stu-id="a3e08-140">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Diagnostics.PerformanceCounter?displayProperty=nameWithType>|<span data-ttu-id="a3e08-141">Windows NT パフォーマンス カウンター コンポーネントを表します。</span><span class="sxs-lookup"><span data-stu-id="a3e08-141">Represents a Windows NT performance counter component.</span></span> <span data-ttu-id="a3e08-142">既存の定義済みカウンターやカスタム カウンターを読み取ったり、カスタム カウンターにパフォーマンス データを書き込むには、このクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="a3e08-142">Use this class to read existing predefined or custom counters and publish (write) performance data to custom counters.</span></span>|  
|<xref:System.Diagnostics.PerformanceCounterCategory?displayProperty=nameWithType>|<span data-ttu-id="a3e08-143">コンピューター上のカウンターおよびカウンター カテゴリと対話するためのいくつかのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a3e08-143">Provides several methods for interacting with counters and categories of counters on the computer.</span></span>|  
|<xref:System.Diagnostics.PerformanceCounterInstaller?displayProperty=nameWithType>|<span data-ttu-id="a3e08-144">`PerformanceCounter` コンポーネントのインストーラーを指定します。</span><span class="sxs-lookup"><span data-stu-id="a3e08-144">Specifies an installer for the `PerformanceCounter` component.</span></span>|  
|<xref:System.Diagnostics.PerformanceCounterType?displayProperty=nameWithType>|<span data-ttu-id="a3e08-145">`NextValue` の `PerformanceCounter`メソッドを計算する数式を指定します。</span><span class="sxs-lookup"><span data-stu-id="a3e08-145">Specifies the formula to calculate the `NextValue` method for a `PerformanceCounter`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a3e08-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="a3e08-146">See Also</span></span>  
 [<span data-ttu-id="a3e08-147">Performance Counters</span><span class="sxs-lookup"><span data-stu-id="a3e08-147">Performance Counters</span></span>](../../../docs/framework/debug-trace-profile/performance-counters.md)
