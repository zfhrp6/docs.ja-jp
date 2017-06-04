---
title: "Application Domain Resource Monitoring | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "monitoring managed memory use by application domain"
  - "application domains, memory use"
  - "memory use, monitoring"
  - "application domains, resource monitoring"
ms.assetid: 318bedf8-7f35-4f00-b34a-2b7b8e3fa315
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# Application Domain Resource Monitoring
アプリケーション ドメインのリソース監視 \(ARM\) を使用すると、ホストでアプリケーション ドメインによる CPU とメモリの使用状況を監視できます。  これは、ASP.NET など、長時間実行されるプロセスで多数のアプリケーション ドメインを使用するホストで役立ちます。  プロセス全体のパフォーマンスに悪影響を及ぼしているアプリケーションのアプリケーション ドメインをホストでアンロードできます。ただし、問題となっているアプリケーションを特定できる場合に限ります。  ARM を使用することで、そのような判断の際に役立つ情報が提供されます。  
  
 たとえば、ホスティング サービスが ASP.NET サーバーで多数のアプリケーションを実行している場合があります。  プロセスの特定のアプリケーションによるメモリ使用量が多くなりすぎたり、プロセッサ時間が長くなりすぎたりした場合、ホスティング サービスで ARM を使用すると、問題の原因になっているアプリケーション ドメインを特定できます。  
  
 ARM は軽量のため、実行中のアプリケーションで問題なく使用できます。  情報を確認するときは、Windows イベント トレーシング \(ETW\) を使用するか、マネージ API またはネイティブ API から直接アクセスします。  
  
## リソース監視の有効化  
 ARM を有効にする方法は 4 つあります。共通言語ランタイム \(CLR\) の起動時に構成ファイルを指定するか、アンマネージ ホスト API を使用するか、マネージ コードを使用するか、ARM ETW イベントをリッスンします。  
  
 ARM を有効にすると、プロセス内のアプリケーション ドメインに関するデータの収集がすぐに開始されます。  ARM を有効にする前にアプリケーション ドメインが作成されていた場合の累積データは、アプリケーション ドメインの作成時点ではなく、ARM を有効にした時点からの累積データです。ARM を有効にすると、後で無効にすることはできません。  
  
-   CLR の起動時に [\<appDomainResourceMonitoring\>](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md) 要素を構成ファイルに追加し、`true`へ `enabled` 属性を設定することで ARM を有効にすることができます。  値が `false` \(既定\) の場合、ARM が起動時には有効にならないだけで、他のアクティブ化方法を使用して後から有効にすることができます。  
  
-   ホストで ARM を有効にするには、[ICLRAppDomainResourceMonitor](../../../ocs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) ホスト インターフェイスを要求します。  このインターフェイスが正常に取得されると、ARM が有効になります。  
  
-   マネージ コードで ARM を有効にするには、static \(Visual Basic では `Shared`\) の <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=fullName> プロパティを `true` に設定します。  プロパティを設定すると、すぐに ARM が有効になります。  
  
-   起動後に ARM を有効にするには、ETW イベントをリッスンします。  `AppDomainResourceManagementKeyword` キーワードを使用してパブリック プロバイダー `Microsoft-Windows-DotNETRuntime` を有効にすると、ARM が有効になり、すべてのアプリケーション ドメインのイベントの生成が開始されます。  データをアプリケーション ドメインおよびスレッドと関連付けるには、さらに `ThreadingKeyword` キーワードを指定して `Microsoft-Windows-DotNETRuntimeRundown` プロバイダーを有効にする必要があります。  
  
## ARM の使用  
 ARM を使用すると、アプリケーション ドメインによって使用されている合計プロセッサ時間と、メモリの使用状況に関する 3 種類の情報が得られます。  
  
-   **アプリケーション ドメインの合計プロセッサ時間 \(秒\)**: アプリケーション ドメインの有効期間中に実行に時間を費やしたすべてのスレッドについて、オペレーティング システムから報告されたスレッド時間を合計した時間です。  ブロック状態またはスリープ状態のスレッドはプロセッサ時間を消費しません。  ネイティブ コードを呼び出すスレッドの場合、スレッドがネイティブ コードで費やした時間は、呼び出しを行ったアプリケーション ドメインの時間に加算されます。  
  
    -   マネージ API: <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=fullName> プロパティ。  
  
    -   ホスト API: [ICLRAppDomainResourceMonitor::GetCurrentCpuTime](../Topic/ICLRAppDomainResourceMonitor::GetCurrentCpuTime%20Method.md) メソッド。  
  
    -   ETW イベント: `ThreadCreated` イベント、`ThreadAppDomainEnter` イベント、および `ThreadTerminated` イベント。  プロバイダーおよびキーワードの詳細については、「[CLR ETW イベント](../../../docs/framework/performance/clr-etw-events.md)」の「アプリケーション ドメインのリソース監視イベント」を参照してください。  
  
-   **有効期間中にアプリケーション ドメインによって行われたマネージ割り当ての合計 \(バイト\)**: 割り当てオブジェクトの有効期間が短い場合があるため、アプリケーション ドメインによるすべてのメモリ使用が、割り当ての合計に必ずしも反映されるとは限りません。  ただし、アプリケーションで大量のオブジェクトの割り当てや解放を行う場合、割り当てのコストが問題になる可能性があります。  
  
    -   マネージ API: <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=fullName> プロパティ。  
  
    -   ホスト API: [ICLRAppDomainResourceMonitor::GetCurrentAllocated](../Topic/ICLRAppDomainResourceMonitor::GetCurrentAllocated%20Method.md) メソッド。  
  
    -   ETW イベント: `AppDomainMemAllocated` イベント、`Allocated` フィールド。  
  
-   **アプリケーション ドメインによって参照される、最後のフル ブロッキング コレクションで残ったマネージ メモリ \(バイト\)**: この数値は、フル ブロッキング コレクションの後にしか正確になりません \(対照的なのは同時実行コレクションです。同時実行コレクションはバックグラウンドで実行され、アプリケーションがブロックされません\)。フル ブロッキング コレクションは、たとえば <xref:System.GC.Collect?displayProperty=fullName> メソッド オーバーロードで実行されます。  
  
    -   マネージ API: <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=fullName> プロパティ。  
  
    -   ホスト API: [ICLRAppDomainResourceMonitor::GetCurrentSurvived](../Topic/ICLRAppDomainResourceMonitor::GetCurrentSurvived%20Method.md) メソッド、`pAppDomainBytesSurvived` パラメーター。  
  
    -   ETW イベント: `AppDomainMemSurvived` イベント、`Survived` フィールド。  
  
-   **プロセスよって参照される、最後のフル ブロッキング コレクションで残った合計マネージ メモリ \(バイト\)**: 個々のアプリケーション ドメインで残ったメモリをこの数値と比較できます。  
  
    -   マネージ API: <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=fullName> プロパティ。  
  
    -   ホスト API: [ICLRAppDomainResourceMonitor::GetCurrentSurvived](../Topic/ICLRAppDomainResourceMonitor::GetCurrentSurvived%20Method.md) メソッド、`pTotalBytesSurvived` パラメーター。  
  
    -   ETW イベント: `AppDomainMemSurvived` イベント、`ProcessSurvived` フィールド。  
  
### フル ブロッキング コレクションがいつ実行されたか確認する  
 残ったメモリのカウントのうちどの時点のものが正確かを判断するには、フル ブロッキング コレクションがいつ発生したかを確認する必要があります。  そのための方法は、ARM の統計情報を調べるのに使用する API によって異なります。  
  
#### マネージ API  
 <xref:System.AppDomain> クラスのプロパティを使用する場合は、<xref:System.GC.RegisterForFullGCNotification%2A?displayProperty=fullName> メソッドを使用してフル コレクションの通知を登録できます。  使用するしきい値は重要ではありません。コレクションが開始されるまでではなく、コレクションが完了するまで待機するからです。  その後、<xref:System.GC.WaitForFullGCComplete%2A?displayProperty=fullName> メソッドを呼び出して、フル コレクションが完了するまでブロックします。  ループでメソッドを呼び出し、メソッドから制御が戻るたびに必要な分析を実行するスレッドを作成できます。  
  
 また、<xref:System.GC.CollectionCount%2A?displayProperty=fullName> メソッドを定期的に呼び出して、ジェネレーション 2 のコレクションの数が増加していないかどうかを確認する方法もあります。  ただし、ポーリング間隔によっては、この手法ではフル コレクションの発生を正確に特定できない場合があります。  
  
#### ホスト API  
 アンマネージ ホスト API を使用する場合は、ホストで CLR の [IHostGCManager](../../../ocs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md) インターフェイスの実装を渡す必要があります。  この CLR は、コレクションの実行中に中断されたスレッドの実行を再開すると [IHostGCManager::SuspensionEnding](../Topic/IHostGCManager::SuspensionEnding%20Method.md) メソッドを呼び出します。  完了したコレクションのジェネレーションがメソッドのパラメーターとして CLR から渡されるため、そのコレクションがフル コレクションだったかどうかをホストで確認できます。  残ったメモリを [IHostGCManager::SuspensionEnding](../Topic/IHostGCManager::SuspensionEnding%20Method.md) メソッドの実装で照会すると、カウントが更新された後ですぐ取得できるようになります。  
  
## 参照  
 <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=fullName>   
 [ICLRAppDomainResourceMonitor インターフェイス](../../../ocs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)   
 [\<appDomainResourceMonitoring\>](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)   
 [CLR ETW イベント](../../../docs/framework/performance/clr-etw-events.md)