---
title: "ランタイム プロファイリング | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "パフォーマンス カウンター"
  - "共通言語ランタイム、プロファイル"
  - "Perfmon.exe"
  - "システム モニター"
  - "プロファイル"
  - "ランタイム、プロファイル"
  - "プロファイリング (アプリケーションの)"
  - "パフォーマンス コンソール"
ms.assetid: ccd68284-f3a8-47b8-bc3f-92e5fe3a1640
caps.latest.revision: 22
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 22
---
# ランタイム プロファイリング
プロファイリングは、任意の開発シナリオまたは配置シナリオでパフォーマンス データを収集する方法の 1 つです。 このセクションは、アプリケーションのパフォーマンスに関する情報の収集を必要とする開発者およびシステム管理者を対象にしています。  
  
## パフォーマンス モニター \(Perfmon.exe\) を使用したパフォーマンスの追跡  
 パフォーマンス モニターは、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] アプリケーションをプロファイリングする場合に最も使いやすいツールです。 パフォーマンス モニターは、共通言語ランタイムおよび [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] と共にインストールされる .NET Framework パフォーマンス カウンター内のデータをグラフィカルに表示します。 これらのカウンターを使用することにより、メモリ管理から Just\-In\-Time \(JIT\) コンパイラのパフォーマンスまで、あらゆる情報を監視できます。 .NET パフォーマンス カウンターは、アプリケーションが使用するリソースに関する情報を提供します。この情報は、アプリケーションのパフォーマンスを判断するための間接的な指標となります。 これらのカウンターは、アプリケーション内部の動作状況を把握するために使用します。  
  
#### perfmon.exe を Windows Vista 以降のバージョンで実行するには  
  
1.  コマンド プロンプトで、「**perfmon**」と入力します。**\[パフォーマンス モニター\]** コンソールが表示されます。  
  
2.  **\[監視ツール\]** フォルダーで、**\[パフォーマンス モニター\]** をクリックします。  
  
3.  パフォーマンス モニターのツールバーで、**\[追加\]** アイコン \(正符号\) をクリックします \(表示されている場合\)。 表示されていない場合は、モニター ウィンドウで右クリックし、**\[カウンターの追加\]** オプションを選択します。  
  
     **\[接続の追加\]** ダイアログ ボックスが表示されます。**\[使用可能なカウンター\]** リスト ボックスに、使用可能なパフォーマンス オブジェクトが表示されます。 .NET Framework アプリケーション用には、さまざまな定義済みのオブジェクトがあります。これには、メモリ管理 \(**.NET CLR メモリ**\)、相互運用性 \(**.NET CLR の相互運用性**\)、例外処理 \(**.NET CLR 例外**\)、およびマルチスレッド \(**.NET CLR LocksAndThreads**\) が含まれます。 各パフォーマンス オブジェクトには、個々 のパフォーマンス カウンターが多数含まれています。 パフォーマンス モニターで使用可能なパフォーマンス カウンターの一覧は、「[Performance Counters](../../../docs/framework/debug-trace-profile/performance-counters.md)」を参照してください。  
  
4.  パフォーマンス オブジェクトの名前の横にあるチェック ボックスをオンにすると、サポートされている個々のパフォーマンス カウンターの一覧が表示されます。  
  
5.  表示するパフォーマンス カウンターをクリックします。  
  
6.  **\[選択したオブジェクトのインスタンス\]** リスト ボックスで、**\< すべてのインスタンス\>** をクリックして、共通言語ランタイムのパフォーマンス カウンターをグローバルに \(システム全体で\) 監視するように指定します。  
  
     または  
  
     **\[選択したオブジェクトのインスタンス\]** リスト ボックスで、アプリケーション名をクリックして、そのアプリケーションのパフォーマンス カウンターを監視します。  
  
     複数のバージョンのランタイムを区別する必要がある場合、または同じ名前を持つ複数のアプリケーション間のあいまいさを解消する必要がある場合は、レジストリ キーも変更する必要があります。 詳細については、「[Performance Counters and In\-Process Side\-By\-Side Applications](../../../docs/framework/debug-trace-profile/performance-counters-and-in-process-side-by-side-applications.md)」を参照してください。  
  
> [!NOTE]
>  パフォーマンス コンソールの実行中に新しいパフォーマンス カウンターがインストールされた場合は、新しいカウンターが表示されるように、パフォーマンス コンソールを停止して再起動してください。  
  
 特定のゾーンまたはリモート共有に存在するアセンブリをプロファイリングする場合は、リモート アセンブリがパフォーマンス カウンターを実行するコンピューターに対して完全な信頼関係を持っていることを確認してください。 アセンブリが十分な信頼関係を持っていない場合、パフォーマンス カウンターは機能しません。 さまざまなゾーンに対する信頼関係の設定方法については、「[Caspol.exe \(コード アクセス セキュリティ ポリシー ツール\)](../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md)」を参照してください。  
  
> [!NOTE]
>  [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] がインストールされているシステムでは、パフォーマンス モニターで、[!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] を使用して開発されたアプリケーションについて、**.NET CLR データ** や **.NET CLR ネットワーク** などの一部のカテゴリでパフォーマンス カウンターのデータが表示されない場合があります。 このような場合、[\<forcePerformanceCounterUniqueSharedMemoryReads\>](../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md) 要素をアプリケーションの構成ファイルに追加することで、このデータを表示するようにパフォーマンス モニターを構成できます。  
  
## プログラムを使用したパフォーマンス カウンターの読み取りと作成  
 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] には、パフォーマンス コンソールで利用できるものと同じパフォーマンス情報にコードからアクセスするのに使用するクラスが用意されています。 また、これらのクラスを使用すると、カスタム パフォーマンス カウンターを作成できます。[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] に用意されているパフォーマンス監視クラスの一部について、次の表に説明を示します。  
  
|クラス|説明|  
|---------|--------|  
|<xref:System.Diagnostics.PerformanceCounter?displayProperty=fullName>|Windows NT パフォーマンス カウンター コンポーネントを表します。 既存の定義済みカウンターやカスタム カウンターを読み取ったり、カスタム カウンターにパフォーマンス データを書き込むには、このクラスを使用します。|  
|<xref:System.Diagnostics.PerformanceCounterCategory?displayProperty=fullName>|コンピューター上のカウンターおよびカウンター カテゴリと対話するためのいくつかのメソッドを提供します。|  
|<xref:System.Diagnostics.PerformanceCounterInstaller?displayProperty=fullName>|`PerformanceCounter` コンポーネントのインストーラーを指定します。|  
|<xref:System.Diagnostics.PerformanceCounterType?displayProperty=fullName>|`PerformanceCounter` の `NextValue` メソッドを計算する数式を指定します。|  
  
## 参照  
 [Performance Counters](../../../docs/framework/debug-trace-profile/performance-counters.md)