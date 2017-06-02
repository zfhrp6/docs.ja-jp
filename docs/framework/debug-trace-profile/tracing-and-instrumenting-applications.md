---
title: "アプリケーションのトレースとインストルメント | Microsoft Docs"
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
  - "トレース [.NET Framework]"
  - "デバッグ [.NET Framework]、インストルメンテーション"
  - "パフォーマンスの監視、インストルメンテーション"
  - "インストルメンテーションは、インストルメンテーションの概要"
  - "トレースのトレース [.NET Framework]"
  - "パフォーマンスの監視、トレース コード"
  - "Trace クラス、.NET アプリケーションのインストルメンテーション"
ms.assetid: 773b6fc4-9013-4322-b728-5dec7a72e743
caps.latest.revision: 21
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 21
---
# アプリケーションのトレースとインストルメント
トレースとは、実行中のアプリケーションの実行状態を監視する方法です。 .NET Framework アプリケーションの開発時に、トレースとデバッグのインストルメンテーションをアプリケーションに追加できます。このインストルメンテーションは、アプリケーションの開発中でも開発したアプリケーションの配置後でも使用できます。 使用することができます、 <xref:System.Diagnostics.Trace?displayProperty=fullName>、 <xref:System.Diagnostics.Debug?displayProperty=fullName>、および<xref:System.Diagnostics.TraceSource?displayProperty=fullName>エラーおよびアプリケーション ログ、テキスト ファイル、またはその他のデバイスを後で分析の実行に関する情報を記録するクラス。  
  
 用語*インストルメンテーション*製品のパフォーマンスのレベルを監視または測定し、エラーを診断する機能を意味します。 プログラミングでは、組み込むアプリケーションの機能を指します。  
  
-   **コードのトレース**-実行時にアプリケーションの実行状態について示すメッセージを受信します。  
  
-   **デバッグ**- 追跡して、開発中のアプリケーションのプログラミング エラーを修正します。 詳細については、次を参照してください。[デバッグ](../Topic/Debugging%20in%20Visual%20Studio.md)します。  
  
-   **パフォーマンス カウンター** -アプリケーションのパフォーマンスを追跡するためのコンポーネントです。 詳細については、次を参照してください。[パフォーマンス カウンター](../../../docs/framework/debug-trace-profile/performance-counters.md)します。  
  
-   **イベント ログ**-できるようにするコンポーネントは、アプリケーションの実行における主要なイベントを追跡します。 詳細については、次を参照してください。、 <xref:System.Diagnostics.EventLog>クラスです。  
  
 トレース ステートメントをコード内に計画的に配置することによってアプリケーションをインストルメントすることは、分散アプリケーションでは特に便利です。 トレース ステートメントを使用してアプリケーションをインストルメントすると、不適切な動作についての情報を表示できるだけでなく、アプリケーションの実行状態を監視するための情報も表示できます。  
  
 <xref:System.Diagnostics.TraceSource>クラスは拡張されたトレース機能および旧バージョンの静的メソッドの代わりに使用できる提供<xref:System.Diagnostics.Trace>と<xref:System.Diagnostics.Debug>トレース クラスです。 使い慣れた<xref:System.Diagnostics.Trace>と<xref:System.Diagnostics.Debug>クラスも引き続き広く使用されますが、 <xref:System.Diagnostics.TraceSource>クラスがなどの新しいトレース コマンドに推奨<xref:System.Diagnostics.TraceSource.TraceEvent%2A>と<xref:System.Diagnostics.TraceSource.TraceData%2A>します。  
  
 <xref:System.Diagnostics.Trace>と<xref:System.Diagnostics.Debug>クラスは同じですが、そのプロシージャおよび関数を除く、<xref:System.Diagnostics.Trace>クラスは既定でにコンパイル リリース ビルドの<xref:System.Diagnostics.Debug>クラスはありません。  
  
 <xref:System.Diagnostics.Trace>と<xref:System.Diagnostics.Debug>クラスは、監視し、開発中または配置後のアプリケーションのパフォーマンスを確認するための手段を提供します。 たとえば、使用、<xref:System.Diagnostics.Trace>とようになります (たとえば、新しいデータベース接続の作成)、アプリケーションの効率を監視できる、特定の種類の配置されたアプリケーションでアクションを追跡するクラス。  
  
## <a name="code-tracing-and-debugging"></a>コードのトレースとデバッグ  
 出力メソッドを使用する開発時に、<xref:System.Diagnostics.Debug>クラスを Visual Studio 統合開発環境 (IDE) の出力ウィンドウにメッセージを表示します。 例:  
  
```vb  
Trace.WriteLine("Hello World!")  
Debug.WriteLine("Hello World!")  
  
```  
  
```csharp  
System.Diagnostics.Trace.WriteLine("Hello World!");  
System.Diagnostics.Debug.WriteLine("Hello World!");  
  
```  
  
 これらの例の"Hello World!"が表示されます。 出力 ウィンドウで、デバッガーでアプリケーションを実行します。  
  
 これにより、アプリケーションをデバッグし、テスト環境での動作に基づいてアプリケーションのパフォーマンスを最適化できます。 アプリケーションをデバッグするには、デバッグ ビルドで、<xref:System.Diagnostics.Debug>条件付きの属性をすべてのデバッグ出力を受け取るようにをオンにします。 オンにしないでリリース ビルドをコンパイルするには、アプリケーションのリリースの準備ができたら、<xref:System.Diagnostics.Debug>条件属性をコンパイラでは、最終的な実行可能ファイルには、デバッグ コードに含めないようにします。 詳細については、次を参照してください。[方法: トレースとデバッグによる条件付きコンパイル](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)します。 アプリケーションの別のビルド構成の詳細については、次を参照してください。[コンパイルとビルド](../Topic/Compiling%20and%20Building%20in%20Visual%20Studio.md)します。  
  
 トレースすることも、インストールされたアプリケーションのコードが実行される方法を使って、<xref:System.Diagnostics.Trace>クラスです。 配置することで[トレース スイッチ](../../../docs/framework/debug-trace-profile/trace-switches.md)コードでは、トレースが発生したかどうかと、どのくらい広範を制御することができます。 これにより、運用環境におけるアプリケーションのステータスを監視できます。 複数のコンポーネントが複数のコンピューターで実行されるビジネス アプリケーションでは、この監視が特に重要です。 配置後のスイッチの機能は、構成ファイルで制御できます。 詳細については、次を参照してください。[方法: トレース スイッチの構成と初期化を、作成](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)します。  
  
 トレースを使用するアプリケーションの開発時には、通常、アプリケーション コードにトレース メッセージとデバッグ メッセージの両方を組み込みます。 オンにせず、リリース ビルドをコンパイルするには、アプリケーションをデプロイする準備ができたら、**デバッグ**条件属性です。 ただし、有効化しても、**トレース**条件属性をコンパイラは、実行可能ファイルにトレース コードを含むようです。 詳細については、次を参照してください。[方法: トレースとデバッグによる条件付きコンパイル](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)します。  
  
### <a name="phases-of-code-tracing"></a>コードのトレースの段階  
 コードのトレースには、次の&3; つの段階があります。  
  
1.  **インストルメンテーション**-トレース コードをアプリケーションに追加します。  
  
2.  **トレース**-トレース コードは、指定された対象に情報を書き込みます。  
  
3.  **分析**-トレース情報を特定し、アプリケーションの問題の理解を評価します。  
  
 既定の設定では、開発中は、すべてのデバッグ出力メソッドおよびトレース出力メソッドが、Visual Studio の出力ウィンドウに情報を書き込みます。 配置後のアプリケーションでは、メソッドは指定された場所にトレース情報を書き込みます。 トレースまたはデバッグの出力ターゲットを指定する方法の詳細については、次を参照してください。[トレース リスナー](../../../docs/framework/debug-trace-profile/trace-listeners.md)します。  
  
 配置されたアプリケーションで起こりうる問題を、トレースを使用して分析したり修正したりするためにしばしば使用される主要な手順を次に示します。 これらの手順を実行する方法の詳細については、適切なリンクを参照してください。  
  
##### <a name="to-use-tracing-in-an-application"></a>アプリケーションでトレースを使用するには  
  
1.  アプリケーションを配置した後で受け取るトレース出力の種類を検討します。  
  
2.  スイッチのセットを作成します。 詳細については、次を参照してください。[方法: トレース スイッチを設定する](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)です。  
  
3.  アプリケーションのコードにトレース ステートメントを追加します。  
  
4.  トレース出力を表示する場所を決定し、適切なリスナーを追加します。 詳細については、次を参照してください。[トレース リスナーの初期化と作成](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-listeners.md)します。  
  
5.  アプリケーションおよびそのアプリケーションに含まれるトレース コードをテストおよびデバッグします。  
  
6.  次のいずれかのプロシージャを使用して、アプリケーションを実行可能なコードにコンパイルします。  
  
    -   使用して、**ビルド**メニューを**デバッグ**のページ、**プロパティ ページ** ダイアログ ボックスで**ソリューション エクスプ ローラー**します。 Visual Studio でコンパイルをする場合は、この方法を使用してください。  
  
         \- または  
  
    -   使用して、**トレース**と**デバッグ**コンパイラ ディレクティブは、コンパイルのコマンド ライン メソッドです。 詳細については、次を参照してください。[トレースとデバッグによる条件付きコンパイル](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)します。 コマンド ラインからコンパイルする場合はこの方法を使用してください。  
  
7.  問題が実行時に発生する場合は、適切なトレース スイッチをオンにしてください。 詳細については、次を参照してください。[トレース スイッチ](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)します。  
  
     トレース コードは、指定された場所 (画面、テキスト ファイル、イベント ログなど) にトレース メッセージを書き込みます。 含まれるリスナーの種類、 **Trace.Listeners**コレクションが決定します。  
  
8.  トレース メッセージを分析して、アプリケーションの問題を識別および理解します。  
  
## <a name="trace-instrumentation-and-distributed-applications"></a>トレースの実装および分散アプリケーション  
 分散アプリケーションを作成するときに、アプリケーションが使用される環境でテストをすることが難しい場合があります。 オペレーティング システムや Web ブラウザーのすべての組み合わせ (ローカライズ言語オプションのすべてのケースも含む) をテストしたり、アプリケーションに同時にアクセスする最大ユーザー数をシミュレートしたりできる開発チームはほとんどありません。 このため、大量の情報、異なる設定、エンド ユーザー固有の動作などの要因に対して分散アプリケーションがどのように応答するかをテストすることはできません。 また、分散アプリケーションを構成する要素の大半には、直接対話したりこれらの構成要素の利用状況を表示したりするためのユーザー インターフェイスは備わっていません。  
  
 ただしをシステム管理者、特に不当なによって特定のイベントを記述する分散アプリケーションの有効化することでこれを補うことができます*のインストルメント化*アプリケーション-は、コードの重要な位置にトレース ステートメントを配置することによってです。 これにより、予測不可能な動作 (極度に遅い応答時間など) が実行時に発生した場合でも、原因を判断できます。  
  
 トレース ステートメントを使用すると、オリジナル ソース コードを検査、変更、および再コンパイルしたり、デバッグ環境で実行時エラーを生成したりするなど、困難なタスクを避けることができます。  アプリケーションの実装は、エラーの表示だけでなく、パフォーマンスを監視するためにもすることができます。  
  
## <a name="strategic-placement-of-trace-statements"></a>トレース ステートメントの計画的な配置  
 実行時に使用するトレース ステートメントを配置するときには、十分に注意する必要があります。 考えられるすべてのトレース シナリオが適切に処理されるように、配置されるアプリケーションで必要とされるトレース情報を考慮する必要があります。 しかし、トレースを使用するアプリケーションは多岐にわたっており、トレースの計画的な配置にあたっての一般的なガイドラインはありません。 トレース ステートメント配置の詳細については、次を参照してください。[方法: アプリケーション コードにトレース ステートメントを追加](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)します。  
  
## <a name="output-from-tracing"></a>トレースの出力  
 トレース出力と呼ばれるオブジェクトによって収集された*リスナー*します。 リスナーは、トレースの出力を受け取り、出力デバイス (通常は、ウィンドウ、ログ、またはテキスト ファイル) に書き込むためのオブジェクトです。 追加は、通常、トレース リスナーの作成時に、 <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=fullName>をすべてのトレース出力を受信するリスナーを収集します。  
  
 トレース情報は、常に書き込まれるには、少なくとも既定値に<xref:System.Diagnostics.Trace>出力対象、 <xref:System.Diagnostics.DefaultTraceListener>します。 何らかの理由を削除した場合、 <xref:System.Diagnostics.DefaultTraceListener>に他のリスナーを追加することがなく、<xref:System.Diagnostics.Trace.Listeners%2A>コレクションのトレース メッセージは表示されません。 詳細については、次を参照してください。[トレース リスナー](../../../docs/framework/debug-trace-profile/trace-listeners.md)します。  
  
 6 つ<xref:System.Diagnostics.Debug>メンバーと<xref:System.Diagnostics.Trace>トレース情報を書き込むメソッドを次の表に示します。  
  
|メソッド|出力|  
|------------|------------|  
|**アサート**|指定されたテキスト。何も指定されない場合は、呼び出し履歴。 出力が書き込まれるだけで引数として指定された条件、 **Assert**ステートメントは**false**します。|  
|**失敗します。**|指定されたテキスト。何も指定されない場合は、呼び出し履歴。|  
|**書き込み**|指定されたテキスト。|  
|**WriteIf**|引数として指定された条件の場合は、指定したテキスト、 **WriteIf**ステートメントが満たしています。|  
|**WriteLine**|指定されたテキストおよびキャリッジ リターン。|  
|**WriteLineIf**|引数として指定された条件の場合、指定したテキストおよびキャリッジ リターン、 **WriteLineIf**ステートメントが満たしています。|  
  
 内のすべてのリスナー、<xref:System.Diagnostics.Trace.Listeners%2A>上記の表で説明したメッセージを受信するコレクションが実行された操作がメッセージを受信するリスナーの種類に応じて異なる場合があります。 たとえば、 <xref:System.Diagnostics.DefaultTraceListener>を受け取ったときにアサーションのダイアログ ボックスが表示されます、**失敗**か失敗した**Assert**通知が、 <xref:System.Diagnostics.TextWriterTraceListener>単に、ストリームに出力を書き込みます。  
  
 独自のリスナーを実装することにより、結果をカスタマイズできます。 たとえば、メッセージ ボックスにメッセージを表示するカスタム トレース リスナーや、データベースに接続してメッセージをテーブルに追加するトレース リスナーなどを実装できます。 すべてのカスタム リスナーは、前に示した&6; つのメソッドをサポートする必要があります。 開発者が定義するリスナーの作成の詳細については、次を参照してください。 <xref:System.Diagnostics.TraceListener> 、.NET Framework の参照。  
  
> [!NOTE]
>  [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)]、 **Debug.Write**、 **Debug.WriteIf**、 **Debug.WriteLine**、および**Debug.WriteLineIf**メソッドに置き換えた、 **Debug.Print**以前のバージョンの Visual Basic で使用可能なメソッドです。  
  
 **書き込み**と**WriteLine**メソッド常にテキストを記述を指定することです。 **Assert**、 **WriteIf**、および**WriteLineIf**のみ、指定したテキストを記述するかどうかは、式が指定したテキストを記述するかどうかを制御するブール型の引数が必要; **true** (の**WriteIf**と**WriteLineIf**)、または**false** (の**Assert**)。 **失敗**メソッドは、常に、指定したテキストを書き込みます。 詳細については、次を参照してください。[方法: アプリケーション コードにトレース ステートメントを追加](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)および .NET Framework リファレンスです。  
  
## <a name="security-concerns"></a>セキュリティに関する注意事項  
 ASP.NET アプリケーションを配置する前にトレースとデバッグを無効にしないと、アプリケーションに関する情報が公開され、悪意を持ったプログラムによって利用される可能性があります。 詳細については、次を参照してください。[する方法: トレースとデバッグによる条件付きコンパイル](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)、[コンパイルとビルド](../Topic/Compiling%20and%20Building%20in%20Visual%20Studio.md)、と[する方法: トレース スイッチの構成と初期化を、作成](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)します。 デバッグは、IIS (Internet Information Services) で設定することもできます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Diagnostics.Trace>   
 <xref:System.Diagnostics.TraceSource>   
 [コード コントラクト](../../../docs/framework/debug-trace-profile/code-contracts.md)   
 [C#、f#、および Visual Basic プロジェクトの種類](../Topic/Debugging%20Preparation:%20C%23,%20F%23,%20and%20Visual%20Basic%20Project%20Types.md)   
 [方法: アプリケーション コードにトレース ステートメントを追加](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)   
 [方法: トレースとデバッグによる条件付きコンパイル](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)   
 [方法: 作成、初期化、およびトレース スイッチを構成します。](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)   
 [方法: 作成し、トレース ソースの初期化](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md)   
 [方法: TraceSource とフィルターを使用して、トレース リスナー](../../../docs/framework/debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md)   
 [トレース リスナー](../../../docs/framework/debug-trace-profile/trace-listeners.md)   
 [トレース スイッチ](../../../docs/framework/debug-trace-profile/trace-switches.md)