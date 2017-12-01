---
title: "アプリケーション ドメインのリソース監視"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- monitoring managed memory use by application domain
- application domains, memory use
- memory use, monitoring
- application domains, resource monitoring
ms.assetid: 318bedf8-7f35-4f00-b34a-2b7b8e3fa315
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 62a514f94857044af5020d36a1cfd6ce06741ac7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="application-domain-resource-monitoring"></a>アプリケーション ドメインのリソース監視
アプリケーション ドメインのリソース監視 (ARM) では、ホスト アプリケーション ドメインによる CPU およびメモリの使用状況を監視できるようにします。 これは、ASP.NET などのホストの実行時間の長いプロセスで多数のアプリケーション ドメインを使用するのに役立ちます。 ホストに悪影響がのみ、プロセス全体のパフォーマンス問題のあるアプリケーションを特定できる場合、アプリケーションのアプリケーション ドメインをアンロードできます。 ARM では、このような意思決定を行う支援するために使用できる情報を提供します。  
  
 たとえば、ホスティング サービスには、ASP.NET サーバーで実行されている多くのアプリケーションがあります。 プロセスの 1 つのアプリケーションでは、大量のメモリやプロセッサ時間がかかりすぎる消費を開始、する場合は、ホスティング サービスは、問題の原因となっているアプリケーション ドメインを識別する ARM を使用できます。  
  
 ARM はライブ アプリケーションで使用する十分な軽量です。 For Windows (ETW) またはマネージまたはネイティブの Api を介して直接イベントのトレースを使用して、情報にアクセスすることができます。  
  
## <a name="enabling-resource-monitoring"></a>リソースの監視を有効にします。  
 ARM は、4 つの方法で有効にすることができます: 共通言語ランタイム (CLR) が開始されたときに、構成ファイルを指定すること、によってアンマネージを使用してホスト API、マネージ コードを使用して、または ARM ETW イベントを待機しています。  
  
 ARM が有効になっていると、すぐには、プロセス内のすべてのアプリケーション ドメインでデータの収集を開始します。ARM が有効にする前に、アプリケーション ドメインが作成されている場合、アプリケーション ドメインが作成されたときではなく、ARM が有効にすると、累積的なデータが起動します。有効にすると、ARM を無効にすることはできません。  
  
-   追加することによって CLR スタートアップ時 ARM を有効にすることができます、 [ \<appDomainResourceMonitoring >](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)構成ファイル、および設定する要素、`enabled`属性を`true`です。 値`false`(既定) のみ ARM が起動時に無効になっている。 つまり、他のライセンス認証メカニズムのいずれかを使用して後でアクティブにできます。  
  
-   ホストは、ARM を有効に要求することによって、 [ICLRAppDomainResourceMonitor](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)インターフェイスをホストします。 このインターフェイスは正常に取得した、ARM が有効になります。  
  
-   マネージ コードは、ARM を有効にするには、静的 (`Shared` Visual Basic で)<xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>プロパティを`true`です。 プロパティを設定するとすぐには、ARM は有効です。  
  
-   ETW イベントを待機して、起動後に ARM を有効にできます。 ARM が有効であり、パブリック プロバイダーを有効にすると、すべてのアプリケーション ドメイン イベントを発生させる開始`Microsoft-Windows-DotNETRuntime`を使用して、`AppDomainResourceManagementKeyword`キーワード。 アプリケーション ドメインとスレッドとデータを関連付ける、する必要がありますも有効にする、`Microsoft-Windows-DotNETRuntimeRundown`とプロバイダー、`ThreadingKeyword`キーワード。  
  
## <a name="using-arm"></a>ARM の使用  
 ARM では、アプリケーション ドメイン、およびメモリ使用量に関する情報の 3 つの種類によって使用されるプロセッサの合計時間を示します。  
  
-   **合計プロセッサ時間を秒単位で、アプリケーション ドメインの**: この時間がその有効期間中に、アプリケーション ドメインで実行に費やされたすべてのスレッドのオペレーティング システムにより報告されたスレッドの時間を加算して計算されます。 ブロックされているか、スリープ状態のスレッドがプロセッサ時間を使用しないでください。 スレッドは、ネイティブ コードを呼び出すの呼び出しが行われたアプリケーション ドメインの数に、スレッドがネイティブ コードに費やす時間が含まれます。  
  
    -   マネージ API:<xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>プロパティです。  
  
    -   API をホスティング: [iclrappdomainresourcemonitor::getcurrentcputime](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md)メソッドです。  
  
    -   ETW イベント: `ThreadCreated`、 `ThreadAppDomainEnter`、および`ThreadTerminated`イベント。 プロバイダーとキーワードについてを参照してください「AppDomain リソース監視イベント」 [CLR ETW イベント](../../../docs/framework/performance/clr-etw-events.md)です。  
  
-   **(バイト単位)、その有効期間中にアプリケーション ドメインによって行われたマネージの割り当ての合計**: 割り当ての合計は常に反映されておらず、アプリケーション ドメインによるメモリの使用割り当て済みオブジェクトの有効期間が短い可能性があるためです。 ただし、アプリケーションでは、割り当てし、大量のオブジェクトの解放する場合、割り当てのコストが大幅な可能性があります。  
  
    -   マネージ API:<xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>プロパティです。  
  
    -   API をホスティング: [iclrappdomainresourcemonitor::getcurrentallocated](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md)メソッドです。  
  
    -   ETW イベント:`AppDomainMemAllocated`イベント、`Allocated`フィールドです。  
  
-   **マネージ メモリ、(バイト単位) は、アプリケーション ドメインによって参照されると、最新の完全なブロッキング コレクションで残ったを**: この値は正確な後にのみフル ブロッキング コレクション。 (これは、バック グラウンドで発生して、アプリケーションをブロックしませんが、同時実行のガベージ コレクションとは対照的です。)たとえば、<xref:System.GC.Collect?displayProperty=nameWithType>メソッドのオーバー ロードがフル ブロッキング コレクションが発生します。  
  
    -   マネージ API:<xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>プロパティです。  
  
    -   API をホスティング: [iclrappdomainresourcemonitor::getcurrentsurvived](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md)メソッド、`pAppDomainBytesSurvived`パラメーター。  
  
    -   ETW イベント:`AppDomainMemSurvived`イベント、`Survived`フィールドです。  
  
-   **マネージ メモリ合計、(バイト単位) は、プロセスによって参照されると、最新の完全なブロッキング コレクションで残ったを**: この番号に個々 のアプリケーション ドメインの残ったメモリを比較することができます。  
  
    -   マネージ API:<xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>プロパティです。  
  
    -   API をホスティング: [iclrappdomainresourcemonitor::getcurrentsurvived](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md)メソッド、`pTotalBytesSurvived`パラメーター。  
  
    -   ETW イベント:`AppDomainMemSurvived`イベント、`ProcessSurvived`フィールドです。  
  
### <a name="determining-when-a-full-blocking-collection-occurs"></a>完全なときに決定する、ブロッキング コレクションが発生しました。  
 残ったメモリの数が正確な場合を判断するのにフル ブロッキング コレクションが発生したときを把握する必要があります。 これを行うためのメソッドは、ARM 統計情報を確認するを使用する API に依存します。  
  
#### <a name="managed-api"></a>マネージ API  
 プロパティを使用する場合、<xref:System.AppDomain>クラスを使用することができます、<xref:System.GC.RegisterForFullGCNotification%2A?displayProperty=nameWithType>すべてのコレクションの通知を登録します。 コレクションのアプローチではなく、コレクションの完了を待機しているために、使用するしきい値は、重要ではありません。 呼び出すことができますし、<xref:System.GC.WaitForFullGCComplete%2A?displayProperty=nameWithType>メソッドで、完全なコレクションが完了するまでブロックします。 ループ内でメソッドを呼び出し、メソッドが返すときに必要な分析がスレッドを作成できます。  
  
 代わりに、呼び出すことができます、<xref:System.GC.CollectionCount%2A?displayProperty=nameWithType>メソッドを定期的にジェネレーション 2 のコレクションの数が増えたかどうかを参照してください。 ポーリング頻度に応じてこの手法可能性がありますに渡さないほど正確で完全なコレクションの発生を示す値。  
  
#### <a name="hosting-api"></a>ホスト API  
 ホストは、CLR の実装を渡す必要があります、アンマネージ ホスト API を使用する場合、 [IHostGCManager](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)インターフェイスです。 CLR の呼び出し、 [ihostgcmanager::suspensionending](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md)メソッドのコレクションが発生したときに中断されているスレッドの実行を再開するときにします。 CLR は、ホストは、コレクションが完全または部分的なであるかどうかを特定できるように、メソッドのパラメーターとして完了したコレクションの生成を渡します。 実装、 [ihostgcmanager::suspensionending](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md)カウントが更新されるとすぐに取得ことを確認の残ったメモリ メソッドを照会できます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
 [ICLRAppDomainResourceMonitor インターフェイス](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [\<appDomainResourceMonitoring>](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)  
 [CLR ETW イベント](../../../docs/framework/performance/clr-etw-events.md)
