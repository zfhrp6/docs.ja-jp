---
title: WCF パフォーマンス カウンター
ms.date: 03/30/2017
helpviewer_keywords:
- performance counters [WCF]
ms.assetid: f559b2bd-ed83-4988-97a1-e88f06646609
ms.openlocfilehash: 1d9e6b83a78967193c4cb0343f6c77560354a837
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33805169"
---
# <a name="wcf-performance-counters"></a><span data-ttu-id="f99f2-102">WCF パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="f99f2-102">WCF Performance Counters</span></span>
<span data-ttu-id="f99f2-103">Windows Communication Foundation (WCF) には、アプリケーションのパフォーマンスの測定に役立つパフォーマンス カウンターの大規模なセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f99f2-103">Windows Communication Foundation (WCF) includes a large set of performance counters to help you gauge your application's performance.</span></span>  
  
## <a name="enabling-performance-counters"></a><span data-ttu-id="f99f2-104">パフォーマンス カウンターの有効化</span><span class="sxs-lookup"><span data-stu-id="f99f2-104">Enabling Performance Counters</span></span>  
 <span data-ttu-id="f99f2-105">できますよう有効にする WCF サービスのパフォーマンス カウンター、WCF サービスの app.config 構成ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="f99f2-105">You can enable performance counters for a WCF service through the app.config configuration file of the WCF service as follows:</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <diagnostics performanceCounters="All" />  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="f99f2-106">特定の種類のパフォーマンス カウンターを有効にするよう `performanceCounters` 属性を設定できます。</span><span class="sxs-lookup"><span data-stu-id="f99f2-106">The `performanceCounters` attribute can be set to enable a specific type of performance counters.</span></span> <span data-ttu-id="f99f2-107">有効な値は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f99f2-107">Valid values are</span></span>  
  
-   <span data-ttu-id="f99f2-108">All : すべてのカテゴリ カウンター (ServiceModelService、ServiceModelEndpoint、ServiceModelOperation) を有効にします。</span><span class="sxs-lookup"><span data-stu-id="f99f2-108">All: All category counters (ServiceModelService, ServiceModelEndpoint and ServiceModelOperation) are enabled.</span></span>  
  
-   <span data-ttu-id="f99f2-109">ServiceOnly : ServiceModelService カテゴリ カウンターのみを有効にします。</span><span class="sxs-lookup"><span data-stu-id="f99f2-109">ServiceOnly: Only ServiceModelService category counters are enabled.</span></span> <span data-ttu-id="f99f2-110">これが既定値です。</span><span class="sxs-lookup"><span data-stu-id="f99f2-110">This is the default value.</span></span>  
  
-   <span data-ttu-id="f99f2-111">Off : ServiceModel\* パフォーマンス カウンターを無効にします。</span><span class="sxs-lookup"><span data-stu-id="f99f2-111">Off: ServiceModel\* performance counters are disabled.</span></span>  
  
 <span data-ttu-id="f99f2-112">すべての WCF アプリケーションのパフォーマンス カウンターを有効にする場合は、Machine.config ファイルで構成設定を配置できます。</span><span class="sxs-lookup"><span data-stu-id="f99f2-112">If you want to enable performance counters for all WCF applications, you can place the configuration settings in the Machine.config file.</span></span>  <span data-ttu-id="f99f2-113">参照してください、**パフォーマンス カウンターのメモリ サイズの増加**コンピューター上のパフォーマンス カウンターのための十分なメモリを構成する方法についてのセクションを示しています。</span><span class="sxs-lookup"><span data-stu-id="f99f2-113">Please see the **Increasing Memory Size for Performance Counters** section below for more information on configuring sufficient memory for performance counters on your machine.</span></span>  
  
 <span data-ttu-id="f99f2-114">カスタム操作の呼び出し元などの WCF 機能拡張ポイントを使用する場合は、独自のパフォーマンス カウンターを出力する必要もします。</span><span class="sxs-lookup"><span data-stu-id="f99f2-114">If you use WCF extensibility points such as custom operation invokers, you should also emit your own performance counters.</span></span> <span data-ttu-id="f99f2-115">これは、WCF が既定のパスに標準的なパフォーマンス カウンター データを出力できなく機能拡張ポイントを実装する場合があるためです。</span><span class="sxs-lookup"><span data-stu-id="f99f2-115">This is because if you implement an extensibility point, WCF may no longer emit the standard performance counter data in the default path.</span></span> <span data-ttu-id="f99f2-116">手動パフォーマンス カウンターのサポートを実装しない場合、予測したパフォーマンス カウンター データが得られない場合があります。</span><span class="sxs-lookup"><span data-stu-id="f99f2-116">If you do not implement manual performance counter support, you may not see the performance counter data you expect.</span></span>  
  
 <span data-ttu-id="f99f2-117">また次のように、コード内でパフォーマンス カウンターを有効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="f99f2-117">You can also enable performance counters in your code as follows,</span></span>  
  
```  
using System.Configuration;  
using System.ServiceModel.Configuration;  
using System.ServiceModel.Diagnostics;  
Configuration config = ConfigurationManager.OpenExeConfiguration(  
    ConfigurationUserLevel.None);  
ServiceModelSectionGroup sg = ServiceModelSectionGroup.GetSectionGroup(config);  
sg.Diagnostic.PerformanceCounters = PerformanceCounterScope.All;  
config.Save();  
```  
  
## <a name="viewing-performance-data"></a><span data-ttu-id="f99f2-118">パフォーマンス データの表示</span><span class="sxs-lookup"><span data-stu-id="f99f2-118">Viewing Performance Data</span></span>  
 <span data-ttu-id="f99f2-119">Windows に付属のパフォーマンス モニター (Perfmon.exe) を使用して、パフォーマンス カウンターによりキャプチャされたデータを表示できます。</span><span class="sxs-lookup"><span data-stu-id="f99f2-119">To view data captured by the performance counters, you can use the Performance Monitor (Perfmon.exe) that comes with Windows.</span></span> <span data-ttu-id="f99f2-120">移動してこのツールを起動することができます**開始**、 をクリック**実行**および種類`perfmon.exe` ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="f99f2-120">You can launch this tool by going to **Start**, and click **Run** and type `perfmon.exe` in the dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f99f2-121">エンドポイント ディスパッチャーによって最後のメッセージが処理される前に、パフォーマンス カウンター インスタンスが解放される場合があります。</span><span class="sxs-lookup"><span data-stu-id="f99f2-121">Performance counter instances may be released before the last messages have been processed by the endpoint dispatcher.</span></span> <span data-ttu-id="f99f2-122">その結果、パフォーマンス データに一部のメッセージがキャプチャされない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f99f2-122">This can result in performance data not being captured for a few messages.</span></span>  
  
## <a name="increasing-memory-size-for-performance-counters"></a><span data-ttu-id="f99f2-123">パフォーマンス カウンターのメモリ サイズの増加</span><span class="sxs-lookup"><span data-stu-id="f99f2-123">Increasing Memory Size for Performance Counters</span></span>  
 <span data-ttu-id="f99f2-124">WCF では、そのパフォーマンス カウンターのカテゴリを個別の共有メモリを使用します。</span><span class="sxs-lookup"><span data-stu-id="f99f2-124">WCF uses separate shared memory for its performance counter categories.</span></span>  
  
 <span data-ttu-id="f99f2-125">既定では、個々の共有メモリは、グローバル パフォーマンス カウンターのメモリ サイズの 4 分の 1 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="f99f2-125">By default, separate shared memory is set to a quarter the size of global performance counter memory.</span></span> <span data-ttu-id="f99f2-126">グローバル パフォーマンス カウンターのメモリの既定値は 524,288 バイトです。</span><span class="sxs-lookup"><span data-stu-id="f99f2-126">The default global performance counter memory is 524,288 bytes.</span></span> <span data-ttu-id="f99f2-127">そのため、次の 3 つの WCF パフォーマンス カウンターのカテゴリには、既定のサイズは約 128 KB があります。</span><span class="sxs-lookup"><span data-stu-id="f99f2-127">Therefore, the three WCF performance counter categories have a default size of approximately 128KB each.</span></span> <span data-ttu-id="f99f2-128">コンピューターでの WCF アプリケーションの実行時特性によっては、パフォーマンス カウンターのメモリを使い果たして可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f99f2-128">Depending upon the runtime characteristics of the WCF applications on a machine, performance counter memory may be exhausted.</span></span> <span data-ttu-id="f99f2-129">この場合、WCF は、アプリケーション イベント ログにエラーを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="f99f2-129">When this happens, WCF writes an error to the application event log.</span></span> <span data-ttu-id="f99f2-130">エラーの内容にはパフォーマンス カウンターが読み込まれなかったことが示され、エントリには、"System.InvalidOperationException: カスタム カウンター ファイル ビューのメモリが足りません" という例外が含まれます。</span><span class="sxs-lookup"><span data-stu-id="f99f2-130">The content of the error states that a performance counter was not loaded, and the entry contains the exception "System.InvalidOperationException: Custom counters file view is out of memory."</span></span> <span data-ttu-id="f99f2-131">このエラー レベルでトレースが有効になっている場合は、さらにこの障害がトレースされます。</span><span class="sxs-lookup"><span data-stu-id="f99f2-131">If tracing is enabled at the error level, this failure is also traced.</span></span> <span data-ttu-id="f99f2-132">パフォーマンスの低下がパフォーマンス カウンターのメモリがなくなった場合、パフォーマンス カウンターが有効になっていると、WCF アプリケーションの実行を続行する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f99f2-132">If performance counter memory is exhausted, continuing to run your WCF applications with performance counters enabled could result in performance degradation.</span></span> <span data-ttu-id="f99f2-133">コンピューターの管理者は、使用可能なすべてのパフォーマンス カウンターをいつでも読み込めるだけの十分なメモリを割り当てておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="f99f2-133">If you are an administrator of the machine, you should configure it to allocate enough memory to support the maximum number of performance counters that can exist at any time.</span></span>  
  
 <span data-ttu-id="f99f2-134">レジストリの WCF カテゴリのパフォーマンス カウンターのメモリの量を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="f99f2-134">You can change the amount of performance counter memory for WCF categories in the registry.</span></span> <span data-ttu-id="f99f2-135">これを行うには、次の 3 つの場所に `FileMappingSize` という名前の新しい DWORD 値を追加し、目的の値をバイト単位で設定します。</span><span class="sxs-lookup"><span data-stu-id="f99f2-135">To do so, you need to add a new DWORD value named `FileMappingSize` to the three following locations, and set it to the desired value in bytes.</span></span> <span data-ttu-id="f99f2-136">コンピューターを再起動すると、設定した値が有効になります。</span><span class="sxs-lookup"><span data-stu-id="f99f2-136">Reboot your machine so that these changes are taken into effect.</span></span>  
  
-   <span data-ttu-id="f99f2-137">HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance</span><span class="sxs-lookup"><span data-stu-id="f99f2-137">HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance</span></span>  
  
-   <span data-ttu-id="f99f2-138">HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance</span><span class="sxs-lookup"><span data-stu-id="f99f2-138">HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance</span></span>  
  
-   <span data-ttu-id="f99f2-139">HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance</span><span class="sxs-lookup"><span data-stu-id="f99f2-139">HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance</span></span>  
  
 <span data-ttu-id="f99f2-140">膨大な数のオブジェクト (ServiceHost など) が破棄され、ガベージ コレクトされるまで待機している場合、`PrivateBytes` パフォーマンス カウンターには非常に高い数値が登録されます。</span><span class="sxs-lookup"><span data-stu-id="f99f2-140">When a large number of objects (for example, ServiceHost) are disposed of but waiting to be garbage-collected, the `PrivateBytes` performance counter will register an unusually high number.</span></span> <span data-ttu-id="f99f2-141">この問題を解決するには、アプリケーション固有の独自のカウンターを追加するか、`performanceCounters` 属性を使用してサービス レベルのカウンターだけを有効にします。</span><span class="sxs-lookup"><span data-stu-id="f99f2-141">To resolve this problem, you can either add your own application-specific counters, or use the `performanceCounters` attribute to enable only service-level counters.</span></span>  
  
## <a name="types-of-performance-counters"></a><span data-ttu-id="f99f2-142">パフォーマンス カウンターの種類</span><span class="sxs-lookup"><span data-stu-id="f99f2-142">Types of Performance Counters</span></span>  
 <span data-ttu-id="f99f2-143">パフォーマンス カウンターには、サービス、エンドポイント、操作の 3 つのレベルがあります。</span><span class="sxs-lookup"><span data-stu-id="f99f2-143">Performance counters are scoped to three different levels: Service, Endpoint and Operation.</span></span>  
  
 <span data-ttu-id="f99f2-144">WMI を使用してパフォーマンス カウンターのインスタンス名を取得できます。</span><span class="sxs-lookup"><span data-stu-id="f99f2-144">You can use WMI to retrieve the name of a performance counter instance.</span></span> <span data-ttu-id="f99f2-145">たとえば、オブジェクトに適用された</span><span class="sxs-lookup"><span data-stu-id="f99f2-145">For example,</span></span>  
  
-   <span data-ttu-id="f99f2-146">WMI を通じてサービス カウンターのインスタンス名を取得できます[サービス](../../../../../docs/framework/wcf/diagnostics/wmi/service.md)インスタンスの"CounterInstanceName"プロパティです。</span><span class="sxs-lookup"><span data-stu-id="f99f2-146">Service counter instance name can be obtained through WMI [Service](../../../../../docs/framework/wcf/diagnostics/wmi/service.md) instance's "CounterInstanceName" property.</span></span>  
  
-   <span data-ttu-id="f99f2-147">WMI を通じてエンドポイント カウンターのインスタンス名を取得できます[エンドポイント](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md)インスタンスの"CounterInstanceName"プロパティです。</span><span class="sxs-lookup"><span data-stu-id="f99f2-147">Endpoint counter instance name can be obtained through WMI [Endpoint](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) instance's "CounterInstanceName" property.</span></span>  
  
-   <span data-ttu-id="f99f2-148">WMI を通じて操作カウンター インスタンスの名前を取得できます[エンドポイント](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md)インスタンスの"GetOperationCounterInstanceName"メソッドです。</span><span class="sxs-lookup"><span data-stu-id="f99f2-148">Operation counter instance name can be obtained through WMI [Endpoint](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) instance's "GetOperationCounterInstanceName" method.</span></span>  
  
 <span data-ttu-id="f99f2-149">WMI の詳細については、次を参照してください。[診断の Windows Management Instrumentation を使用して](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="f99f2-149">For more information on WMI, see [Using Windows Management Instrumentation for Diagnostics](../../../../../docs/framework/wcf/diagnostics/wmi/index.md).</span></span>  
  
### <a name="service-performance-counters"></a><span data-ttu-id="f99f2-150">サービスのパフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="f99f2-150">Service performance counters</span></span>  
 <span data-ttu-id="f99f2-151">サービスのパフォーマンス カウンターはサービス動作全体を測定し、サービス全体のパフォーマンスを診断するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="f99f2-151">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="f99f2-152">パフォーマンス モニターを使用して表示する場合、これらのカウンターは、`ServiceModelService 4.0.0.0` パフォーマンス オブジェクトの下にあります。</span><span class="sxs-lookup"><span data-stu-id="f99f2-152">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor.</span></span> <span data-ttu-id="f99f2-153">インスタンスには次のパターンの名前が付けられています。</span><span class="sxs-lookup"><span data-stu-id="f99f2-153">The instances are named using the following pattern:</span></span>  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
 <span data-ttu-id="f99f2-154">サービス スコープ内のカウンターは、エンドポイントのコレクションのカウンターが集計されています。</span><span class="sxs-lookup"><span data-stu-id="f99f2-154">A counter in a service scope is aggregated from counter in a collection of endpoints.</span></span>  
  
 <span data-ttu-id="f99f2-155">サービス インスタンス作成のパフォーマンス カウンターは、新しい InstanceContext が作成されるとインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="f99f2-155">Performance counters for service instance creation are incremented when a new InstanceContext is created.</span></span> <span data-ttu-id="f99f2-156">新しい InstanceContext は、非アクティブ化メッセージを (既存のサービスで) 受信した場合でも、あるセッションからインスタンスに接続し、セッションを終了後に別のセッションから再接続した場合でも作成されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f99f2-156">Note that a new InstanceContext is created even when you receive a non-activating message (with an existing service), or when you connect to an instance from one session, end the session, and then reconnect from another session.</span></span>  
  
### <a name="endpoint-performance-counters"></a><span data-ttu-id="f99f2-157">エンドポイントのパフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="f99f2-157">Endpoint performance counters</span></span>  
 <span data-ttu-id="f99f2-158">エンドポイントのパフォーマンス カウンターにより、エンドポイントでのメッセージの受信状況を表すデータを参照できます。</span><span class="sxs-lookup"><span data-stu-id="f99f2-158">Endpoint performance counters enable you to look at data reflecting how an endpoint is accepting messages.</span></span> <span data-ttu-id="f99f2-159">パフォーマンス モニターを使用して表示する場合、これらのカウンターは、`ServiceModelEndpoint 4.0.0.0` パフォーマンス オブジェクトの下にあります。</span><span class="sxs-lookup"><span data-stu-id="f99f2-159">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing using the Performance Monitor.</span></span> <span data-ttu-id="f99f2-160">インスタンスには次のパターンの名前が付けられています。</span><span class="sxs-lookup"><span data-stu-id="f99f2-160">The instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 <span data-ttu-id="f99f2-161">このデータは、個々の操作で収集されるデータに似ていますが、エンドポイントから集計されただけのデータです。</span><span class="sxs-lookup"><span data-stu-id="f99f2-161">The data is similar to what is collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
 <span data-ttu-id="f99f2-162">エンドポイント スコープ内のカウンターは、操作のコレクションのカウンターから集計されます。</span><span class="sxs-lookup"><span data-stu-id="f99f2-162">A counter in an endpoint scope is aggregated from counters in a collection of operations.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f99f2-163">コントラクト名とアドレスが同一の 2 つのエンドポイントは、同じカウンター インスタンスにマップされます。</span><span class="sxs-lookup"><span data-stu-id="f99f2-163">If two endpoints have identical contract names and addresses, they are mapped to the same counter instance.</span></span>  
  
### <a name="operation-performance-counters"></a><span data-ttu-id="f99f2-164">操作のパフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="f99f2-164">Operation performance counters</span></span>  
 <span data-ttu-id="f99f2-165">パフォーマンス モニターを使用して表示する場合、操作パフォーマンス カウンターは、`ServiceModelOperation 4.0.0.0` パフォーマンス オブジェクトの下にあります。</span><span class="sxs-lookup"><span data-stu-id="f99f2-165">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="f99f2-166">それぞれの操作に個別のインスタンスがあります。</span><span class="sxs-lookup"><span data-stu-id="f99f2-166">Each operation has an individual instance.</span></span> <span data-ttu-id="f99f2-167">つまり、指定したコントラクトに 10 の操作がある場合、10 の操作カウンター インスタンスがそのコントラクトに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="f99f2-167">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="f99f2-168">オブジェクトのインスタンスには次のパターンの名前が付いています。</span><span class="sxs-lookup"><span data-stu-id="f99f2-168">The object instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 <span data-ttu-id="f99f2-169">このカウンターにより呼び出しがどのように使用されている、操作がどれほど効率的に実行されているかを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="f99f2-169">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
 <span data-ttu-id="f99f2-170">カウンターが複数のスコープで表示される場合、上位のスコープで収集されたデータは、下位のスコープからのデータが集計されています。</span><span class="sxs-lookup"><span data-stu-id="f99f2-170">When counters are visible at multiple scopes, data gathered from a higher scope are aggregated with data from lower scopes.</span></span> <span data-ttu-id="f99f2-171">たとえば、エンドポイントの `Calls` は、エンドポイント内のすべての操作呼び出しの合計を表します。サービスの `Calls` は、サービス内のすべての操作呼び出しの合計を表します。</span><span class="sxs-lookup"><span data-stu-id="f99f2-171">For example, `Calls` at an endpoint represents the sum of all operation calls within the endpoint; `Calls` at a service represents the sum of all calls to all endpoints within the service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f99f2-172">1 つのコントラクトに重複した操作名がある場合は、その両方の操作に対してカウンター インスタンスは 1 つだけ取得されます。</span><span class="sxs-lookup"><span data-stu-id="f99f2-172">If you have duplicate operation names on a contract, you only get one counter instances for both operations.</span></span>  
  
## <a name="programming-the-wcf-performance-counters"></a><span data-ttu-id="f99f2-173">WCF パフォーマンス カウンターのプログラミング</span><span class="sxs-lookup"><span data-stu-id="f99f2-173">Programming the WCF Performance Counters</span></span>  
 <span data-ttu-id="f99f2-174">WCF パフォーマンス カウンタをプログラムでアクセスできるように、いくつかのファイルは、SDK のインストール フォルダーにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="f99f2-174">Several files are installed in the SDK install folder so that you can access the WCF performance counters programmatically.</span></span> <span data-ttu-id="f99f2-175">そのファイルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="f99f2-175">These files are listed as follows.</span></span>  
  
-   <span data-ttu-id="f99f2-176">_ServiceModelEndpointPerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="f99f2-176">_ServiceModelEndpointPerfCounters.vrg</span></span>  
  
-   <span data-ttu-id="f99f2-177">_ServiceModelOperationPerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="f99f2-177">_ServiceModelOperationPerfCounters.vrg</span></span>  
  
-   <span data-ttu-id="f99f2-178">_ServiceModelServicePerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="f99f2-178">_ServiceModelServicePerfCounters.vrg</span></span>  
  
-   <span data-ttu-id="f99f2-179">_SMSvcHostPerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="f99f2-179">_SMSvcHostPerfCounters.vrg</span></span>  
  
-   <span data-ttu-id="f99f2-180">_TransactionBridgePerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="f99f2-180">_TransactionBridgePerfCounters.vrg</span></span>  
  
 <span data-ttu-id="f99f2-181">カウンターをプログラムでアクセスする方法の詳細については、次を参照してください。[パフォーマンス カウンターのプログラミング アーキテクチャ](http://go.microsoft.com/fwlink/?LinkId=95179)です。</span><span class="sxs-lookup"><span data-stu-id="f99f2-181">For more information on how to access the counters programmatically, see [Performance Counter Programming Architecture](http://go.microsoft.com/fwlink/?LinkId=95179).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f99f2-182">関連項目</span><span class="sxs-lookup"><span data-stu-id="f99f2-182">See Also</span></span>  
 [<span data-ttu-id="f99f2-183">管理と診断</span><span class="sxs-lookup"><span data-stu-id="f99f2-183">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
