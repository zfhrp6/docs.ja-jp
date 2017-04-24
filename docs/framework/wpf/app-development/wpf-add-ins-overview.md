---
title: "WPF アドインの概要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET Framework アドイン モデル [WPF]"
  - "アドイン [WPF], アーキテクチャ"
  - "アドイン [WPF], 利点"
  - "アドイン [WPF], 制限事項"
  - "アドイン [WPF], パフォーマンス"
  - "アドイン [WPF], ユーザー インターフェイス"
  - "アドインとユーザー インターフェイス [WPF]"
  - "アドインと XAML ブラウザー アプリケーション [WPF]"
  - "アドインの概要 [WPF]"
ms.assetid: 00b4c776-29a8-4dba-b603-280a0cdc2ade
caps.latest.revision: 36
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 35
---
# WPF アドインの概要
<a name="Introduction"></a> [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] には、アドイン機能拡張をサポートするアプリケーションの作成に使用できるアドイン モデルが用意されています。  このアドイン モデルを使用することで、アプリケーション機能に統合され、アプリケーション機能を拡張するアドインを作成できます。  一部のシナリオでは、アドインが提供する [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] をアプリケーションで表示する必要があります。  このトピックでは、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] が [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アドイン モデルを強化してこうしたシナリオを実現するしくみ、背後にあるアーキテクチャ、その利点、および制限事項について説明します。  
  
   
  
<a name="Requirements"></a>   
## 必要条件  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アドイン モデルを十分に理解していることが必要です。  詳細については、「[アドインおよび拡張機能](../../../../ml/index.xml)」を参照してください。  
  
<a name="AddInsOverview"></a>   
## アドインの概要  
 新しい機能を追加するためにアプリケーションを再コンパイルして再配置する手間を省くことを目的として、アプリケーションは機能拡張メカニズムを実装し、開発者 \(開発元、サード パーティのいずれも\) が元のアプリケーションに統合される別のアプリケーションを作成できるようにしています。  こうした拡張機能をサポートする方法としては、アドイン \("アドオン"、"プラグイン" などとも呼ばれる\) の使用が最も一般的です。  アドインによる機能拡張を実行する実際のアプリケーションとして、次のようなものが挙げられます。  
  
-   Internet Explorer のアドオン。  
  
-   Windows Media Player のプラグイン。  
  
-   Visual Studio のアドイン。  
  
 たとえば、Windows Media Player のアドイン モデルにおいて、サード パーティの開発者は、Windows Media Player の機能をさまざまな形で拡張する "プラグイン" を実装できます。たとえば、Windows Media Player でネイティブ サポートされていないメディア形式 \(DVD、MP3 など\) のデコーダーおよびエンコーダー、オーディオ エフェクト、スキンなどを作成できます。  各アドイン モデルは、アプリケーション固有の機能を組み込むために構築されますが、どのアドイン モデルにも共通するエンティティや動作がいくつかあります。  
  
 典型的な機能拡張ソリューションの主な 3 つのエンティティは、*コントラクト*、*アドイン*、および*ホスト アプリケーション*です。  コントラクトは、次の 2 つの方法で、アドインとホスト アプリケーションとの統合方法を定義します。  
  
-   アドインはホスト アプリケーションによって実装される機能と一体化します。  
  
-   ホスト アプリケーションはアドインが一体化するための機能を公開します。  
  
 アドインを使用できるようにするためには、ホスト アプリケーションが実行時にアドインを検索して読み込む必要があります。  したがって、アドインをサポートするアプリケーションには次の機能が必要です。  
  
-   **探索** : ホスト アプリケーションによってサポートされるコントラクトに準拠しているアドインを検索します。  
  
-   **アクティブ化** : アドインを読み込んで実行し、アドインとの通信を確立します。  
  
-   **分離** : アプリケーション ドメインまたはアプリケーション プロセスを使用することで他から切り離すための境界を確立し、アドインの使用に伴うセキュリティおよび実行に関する潜在的な問題からアプリケーションを保護します。  
  
-   **通信** : アドインとホスト アプリケーションが分離の境界を越えて通信し、メソッドを呼び出したりデータを渡したりできるようにします。  
  
-   **有効期間管理** : アプリケーション ドメインとアプリケーション プロセスの読み込みおよびアンロードを、クリーンで予測可能な方法で行います \(「[アプリケーション ドメイン](../../../../docs/framework/app-domains/application-domains.md)」を参照\)。  
  
-   **バージョン管理** : ホスト アプリケーションとアドインのどちらかに、新バージョンが作成された後も引き続き通信できるようにします。  
  
 このことからわかるように、堅牢なアドイン モデルの開発は簡単なことではありません。  そのため、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] にはアドイン モデルの構築に必要なインフラストラクチャが用意されています。  
  
> [!NOTE]
>  アドインの詳細については、「[アドインおよび拡張機能](../../../../ml/index.xml)」を参照してください。  
  
<a name="NETFrameworkAddInModelOverview"></a>   
## .NET Framework アドイン モデルの概要  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アドイン モデルは、<xref:System.AddIn> 名前空間にあり、アドイン機能拡張の開発を単純化するために設計された型のセットが用意されています。  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アドイン モデルの基本単位は*コントラクト*です。コントラクトは、ホスト アプリケーションとアドイン間の通信を定義します。  コントラクトのホスト アプリケーション固有の*ビュー*を使用して、コントラクトはホスト アプリケーションに公開されます。  同様に、コントラクトのアドイン固有の*ビュー*がアドインに公開されます。  *アダプター*は、ホスト アプリケーションとアドインが、コントラクトの対応するビュー間で通信するために使用されます。  コントラクト、ビュー、およびアダプターはセグメントと見なされ、関連セグメントのセットが*パイプライン*を構成します。  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アドイン モデルはパイプラインを基盤とし、それを基に探索、アクティブ化、セキュリティ分離、実行分離 \(アプリケーションのドメインとプロセスを両方使用\)、通信、有効期間管理、およびバージョン管理をサポートします。  
  
 このサポート全体を使用して、開発者はホスト アプリケーションの機能を統合するアドインを開発できます。  ただし、一部のシナリオでは、アドインが提供する [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] をホスト アプリケーションで表示する必要が生じます。  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の各プレゼンテーション テクノロジには [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] 実装の独自のモデルがあるため、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アドイン モデルは特定のプレゼンテーション テクノロジをサポートしません。  その代わり、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] では [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アドイン モデルをアドインの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] サポートという形で機能拡張します。  
  
<a name="WPFAddInModel"></a>   
## WPF アドイン  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] を [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アドイン モデルと併用することで、ホスト アプリケーションでアドインの [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] を表示する必要があるさまざまなシナリオに対応できます。  特に、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] によるこれらのシナリオの対応には、次の 2 つのプログラミング モデルが使用されます。  
  
1.  **アドインが UI を返す**。  アドインが、コントラクトの定義に従って、メソッド呼び出しを介してホスト アプリケーションに [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を返します。  このシナリオは、次の場合に使用されます。  
  
    -   アドインが返す [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] の外観が、動的に生成されるレポートなど、実行時にしか存在しないデータまたは条件に依存している。  
  
    -   アドインが提供するサービスの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] が、そのアドインを使用できるホスト アプリケーションの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] と違っている。  
  
    -   アドインは主にホスト アプリケーション向けのサービスを実行し、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を使用してホスト アプリケーションにステータスをレポートする。  
  
2.  **アドインが UI である**。  アドインが、コントラクトの定義に従う [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] です。  このシナリオは、次の場合に使用されます。  
  
    -   アドインは表示以外のサービス \(アドバタイズメントなど\) を提供しない。  
  
    -   アドインが提供するサービスの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] は、そのアドインを使用できるすべてのホスト アプリケーションで共通である \(電卓、カラー ピッカーなど\)。  
  
 これらのシナリオでは、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] オブジェクトをホスト アプリケーション ドメインとアドイン アプリケーション ドメインとの間で受け渡しできる必要があります。  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アドイン モデルは、アプリケーション ドメイン間の通信においてリモート処理に依存しているため、それらの間で受け渡しされるオブジェクトはリモート処理可能である必要があります。  
  
 リモート処理可能なオブジェクトとは、次の 1 つ以上に該当するクラスのインスタンスです。  
  
-   <xref:System.MarshalByRefObject> クラスから派生している。  
  
-   <xref:System.Runtime.Serialization.ISerializable> インターフェイスを実装している。  
  
-   <xref:System.SerializableAttribute> 属性が適用されている。  
  
> [!NOTE]
>  リモート処理可能な [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] オブジェクトの作成の詳細については、「[Making Objects Remotable](http://msdn.microsoft.com/ja-jp/01197253-3f13-43b7-894d-9683e431192a)」を参照してください。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] の型はリモート処理可能ではありません。  この問題を解決するため、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アドイン モデルを拡張して、アドインによって作成される [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] をホスト アプリケーションで表示できるようにします。  これは [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] によって、<xref:System.AddIn.Contract.INativeHandleContract> インターフェイスと、<xref:System.AddIn.Pipeline.FrameworkElementAdapters> クラスの 2 つの静的メソッド <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> および <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> という 2 つの方法でサポートされています。  大まかに、これらの型およびメソッドは次のように使用されます。  
  
1.  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] では、アドインが提供する [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] が、図形、コントロール、ユーザー コントロール、レイアウト パネル、ページなど、<xref:System.Windows.FrameworkElement> から直接または間接的に派生したクラスである必要があります。  
  
2.  UI がアドインとホスト アプリケーションとの間で受け渡しされることをコントラクトで宣言する場合、必ず <xref:System.AddIn.Contract.INativeHandleContract> として宣言する必要があります \(<xref:System.Windows.FrameworkElement> ではない\)。<xref:System.AddIn.Contract.INativeHandleContract> はアドイン [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] のリモート処理可能な表現で、分離の境界を越えて受け渡しできます。  
  
3.  アドインのアプリケーション ドメインから渡される前に、<xref:System.Windows.FrameworkElement> は、<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> 呼び出しによって、<xref:System.AddIn.Contract.INativeHandleContract> としてパッケージ化されます。  
  
4.  ホスト アプリケーションのアプリケーション ドメインに渡された後、<xref:System.AddIn.Contract.INativeHandleContract> は、<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> 呼び出しによって、<xref:System.Windows.FrameworkElement> として再パッケージ化する必要があります。  
  
 <xref:System.AddIn.Contract.INativeHandleContract>、<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>、および <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> の使用形態は、個々のシナリオによって異なります。  以降では、各プログラミング モデルについて詳しく説明していきます。  
  
<a name="ReturnUIFromAddInContract"></a>   
## ユーザー インターフェイスを返すアドイン  
 アドインが [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] をホスト アプリケーションに返すようにするには、次のことが必要です。  
  
1.  ホスト アプリケーション、アドイン、およびパイプラインが、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の「[アドインおよび拡張機能](../../../../ml/index.xml)」の説明に従って作成されている必要があります。  
  
2.  コントラクトに <xref:System.AddIn.Contract.IContract> を実装することが必要です。また、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を返すようにするため、戻り値が <xref:System.AddIn.Contract.INativeHandleContract> 型であるメソッドをコントラクトで宣言する必要があります。  
  
3.  アドインとホスト アプリケーションとの間で受け渡される [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] は、直接または間接的に、<xref:System.Windows.FrameworkElement> から派生している必要があります。  
  
4.  アドインが返す [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] は、分離境界を越える前に、<xref:System.Windows.FrameworkElement> から <xref:System.AddIn.Contract.INativeHandleContract> に変換される必要があります。  
  
5.  返される [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] は、分離境界を越えた後に、<xref:System.AddIn.Contract.INativeHandleContract> から <xref:System.Windows.FrameworkElement> に変換される必要があります。  
  
6.  ホスト アプリケーションは、返された <xref:System.Windows.FrameworkElement> を表示します。  
  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を返すアドインを実装する方法の例については、「[UI を返すアドインを作成する](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-returns-a-ui.md)」を参照してください。  
  
<a name="AddInIsAUI"></a>   
## ユーザー インターフェイスであるアドイン  
 アドインが [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] である場合、次のことが必要です。  
  
1.  ホスト アプリケーション、アドイン、およびパイプラインが、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の「[アドインおよび拡張機能](../../../../ml/index.xml)」の説明に従って作成されている必要があります。  
  
2.  アドインのコントラクト インターフェイスに <xref:System.AddIn.Contract.INativeHandleContract> を実装する必要があります。  
  
3.  ホスト アプリケーションに渡されるアドインが、直接または間接的に、<xref:System.Windows.FrameworkElement> から派生している必要があります。  
  
4.  アドインは、分離境界を越える前に <xref:System.Windows.FrameworkElement> から <xref:System.AddIn.Contract.INativeHandleContract> に変換される必要があります。  
  
5.  アドインは、分離境界を越えた後に <xref:System.AddIn.Contract.INativeHandleContract> から <xref:System.Windows.FrameworkElement> に変換される必要があります。  
  
6.  ホスト アプリケーションは、返された <xref:System.Windows.FrameworkElement> を表示します。  
  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] であるアドインを実装する方法の例については、「[UI であるアドインを作成する](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-is-a-ui.md)」を参照してください。  
  
<a name="ReturningMultipleUIsFromAnAddIn"></a>   
## 複数の UI を返すアドイン  
 アドインが提供する複数の [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] をホスト アプリケーションが表示するケースはよくあります。  たとえば、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] であるアドインが、ホスト アプリケーションにステータス情報も [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] として提供するとします。  このようなアドインは、[ユーザー インターフェイスを返すアドイン](#ReturnUIFromAddInContract)のモデルと[ユーザー インターフェイスであるアドイン](#AddInIsAUI)のモデルの両方の手法を組み合わせることで実装できます。  
  
<a name="AddInsAndXBAPs"></a>   
## アドインと XAML ブラウザー アプリケーション  
 ここまでの例では、ホスト アプリケーションはスタンドアロン アプリケーションとしてインストールされています。  [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] はアドインをホストすることもできますが、そのためには次に示すビルドと実装の要件を満たす必要があります。  
  
-   パイプライン \(フォルダーとアセンブリ\) とアドイン アセンブリを、クライアント コンピューターの [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] アプリケーション キャッシュの、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] と同じフォルダーにダウンロードするよう、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] アプリケーション マニフェストを構成する必要があります。  
  
-   アドインを探索して読み込む [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] コードで、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] の [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] アプリケーション キャッシュを、パイプラインとアドインの場所として使用する必要があります。  
  
-   [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] は、アドインが起点サイトにある圧縮しないファイルを参照する場合、アドインを特別なセキュリティ コンテキストの下で読み込む必要があります。[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] によってホストされる場合、アドインが参照できるのは、ホスト アプリケーションの起点サイトにある圧縮しないファイルのみです。  
  
 これらのタスクについて、次のサブセクションで詳しく説明します。  
  
### ClickOnce 配置のためのパイプラインとアドインの構成  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] は、[!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] 配置キャッシュの安全なフォルダーにダウンロードされ、そこから実行されます。  [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] でアドインをホストするには、パイプラインとアドインのアセンブリも同じ安全なフォルダーにダウンロードする必要があります。  これを行うには、パイプラインとアドインのどちらのアセンブリもダウンロード対象に含まれるよう、アプリケーション マニフェストを構成する必要があります。  これは、[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] で行うのが最も簡単ですが、[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] でパイプラインをアセンブリとして検出するには、パイプラインとアドインのアセンブリが、ホスト [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] プロジェクトのルート フォルダーに存在する必要があります。  
  
 したがって、まず、パイプライン アセンブリとアドイン アセンブリの各プロジェクトのビルド出力を設定し、パイプラインとアドインのアセンブリを [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] プロジェクトのルートにビルドします。  次の表は、ホストの [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] プロジェクトと同じソリューションとルートのフォルダーに格納される、パイプライン アセンブリ プロジェクトとアドイン アセンブリ プロジェクトのビルド出力パスを示します。  
  
 表 1: XBAP でホストされるパイプライン アセンブリのビルド出力パス  
  
|パイプライン アセンブリ プロジェクト|ビルド出力パス|  
|-------------------------|-------------|  
|コントラクト|`..  \HostXBAP\Contracts\`|  
|アドイン ビュー|`..  \HostXBAP\AddInViews\`|  
|アドイン側のアダプター|`..  \HostXBAP\AddInSideAdapters\`|  
|ホスト側のアダプター|`..  \HostXBAP\HostSideAdapters\`|  
|アドイン|`..  \HostXBAP\AddIns\WPFAddIn1`|  
  
 次に、パイプライン アセンブリとアドイン アセンブリを [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] コンテンツ ファイルとして [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] に指定します。手順は次のとおりです。  
  
1.  ソリューション エクスプローラーで各パイプライン フォルダーを右クリックし、**\[プロジェクトに含める\]** をクリックして、パイプラインとアドインのアセンブリをプロジェクトに含めます。  
  
2.  **\[プロパティ\]** ウィンドウで、パイプライン アセンブリとアドイン アセンブリそれぞれについて、**\[ビルド アクション\]** を **\[コンテンツ\]** に設定します。  
  
 最後に、パイプラインとアドインのどちらのアセンブリ ファイルもダウンロード対象に含まれるよう、アプリケーション マニフェストを構成します。  ファイルは、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] アプリケーションが占有する [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] キャッシュ内のフォルダーのルートにあるフォルダー内に存在している必要があります。  この構成は、次の手順に従って、[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] で行うことができます。  
  
1.  [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] プロジェクトを右クリックし、**\[プロパティ\]**、**\[発行\]** の順にクリックし、**\[アプリケーション ファイル\]** をクリックします。  
  
2.  **\[アプリケーション ファイル\]** ダイアログ ボックスで、各パイプラインとアドインの DLL の **\[発行の状況\]** を **\[含める \(自動\)\]** に設定し、各パイプラインとアドインの DLL の **\[ダウンロード グループ\]** を **\[\(必要\)\]** に設定します。  
  
### アプリケーション ベースからのパイプラインとアドインの使用  
 パイプラインとアドインが [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] 配置用に構成されると、[!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] キャッシュ フォルダーに [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] としてダウンロードされます。  このパイプラインとアドインを [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] から使用するには、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] コードがそれらをアプリケーション ベースから取得する必要があります。  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アドイン モデルのさまざまな型やメンバーは、パイプラインおよびアドインを使用できるよう、このシナリオ用に特別なサポートを提供しています。  パスは <xref:System.AddIn.Hosting.PipelineStoreLocation> 列挙値で識別されます。  この値を適切なアドイン メンバーのオーバーロードと併用することで、次のようなパイプラインを使用できます。  
  
-   <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=fullName>  
  
-   [AddInStore.FindAddIns\(Type, PipelineStoreLocation, String\<xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%2CSystem.String%5B%5D%29?displayProperty=fullName>  
  
-   <xref:System.AddIn.Hosting.AddInStore.Rebuild%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=fullName>  
  
-   <xref:System.AddIn.Hosting.AddInStore.Update%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=fullName>  
  
### ホストの起点サイトへのアクセス  
 アドインが起点サイトのファイルを参照できるように、アドインはホスト アプリケーションと等価なセキュリティ分離を使用して読み込む必要があります。  このセキュリティ レベルは <xref:System.AddIn.Hosting.AddInSecurityLevel?displayProperty=fullName> 列挙値により識別され、アドインがアクティブ化されたときに <xref:System.AddIn.Hosting.AddInToken.Activate%2A> メソッドに渡されます。  
  
<a name="WPFAddInModelArchitecture"></a>   
## WPF アドイン アーキテクチャ  
 これまで見てきたように、最上位のレベルでは、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] を使用することによって、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アドインで、\(<xref:System.Windows.FrameworkElement> から直接または間接的に派生した\) [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] を、<xref:System.AddIn.Contract.INativeHandleContract>、<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>、および <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> を使用して実装できます。  その結果、ホスト アプリケーションに <xref:System.Windows.FrameworkElement> が返され、ホスト アプリケーションの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] で表示されます。  
  
 簡単な [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] アドイン シナリオでは、開発者に必要な詳細はこれだけです。  より複雑なシナリオ、特にレイアウト、リソース、データ バインドなど、追加 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] サービスの活用を想定したシナリオでは、その利点と制約を把握するために [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] をサポートする [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アドイン モデルが、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] で拡張されるしくみについて詳しい知識が必要です。  
  
 基本的に、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] をアドインからホスト アプリケーションに渡しません。その代わり、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] の Win32 ウィンドウ ハンドルを [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 相互運用性を使用して渡します。  つまり、アドインの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] がホスト アプリケーションに渡されると、次の処理が行われます。  
  
-   アドイン側で、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、ホスト アプリケーションによって表示される [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] のウィンドウ ハンドルを取得します。  このウィンドウ ハンドルは、<xref:System.Windows.Interop.HwndSource> から派生し、<xref:System.AddIn.Contract.INativeHandleContract> を実装する内部 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] クラスによってカプセル化されます。  このクラスのインスタンスは、<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> によって返され、アドインのアプリケーション ドメインからホスト アプリケーションのアプリケーション ドメインにマーシャリングされます。  
  
-   ホスト アプリケーション側では、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は <xref:System.Windows.Interop.HwndSource> を、<xref:System.Windows.Interop.HwndHost> から派生し、<xref:System.AddIn.Contract.INativeHandleContract> を使用する内部 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] クラスとして、再パッケージ化します。  このクラスのインスタンスは、<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> によってホスト アプリケーションに返されます。  
  
 <xref:System.Windows.Interop.HwndHost> は、ウィンドウ ハンドルによって特定される [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] を [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] で表示するために存在します。  詳細については、「[WPF と Win32 の相互運用性](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)」を参照してください。  
  
 まとめると、<xref:System.AddIn.Contract.INativeHandleContract>、<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>、および <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> は、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] のウィンドウ ハンドルを、アドインからホスト アプリケーションに渡すために存在します。渡されると、<xref:System.Windows.Interop.HwndHost> によってカプセル化され、ホスト アプリケーションの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を表示します。  
  
> [!NOTE]
>  ホスト アプリケーションは <xref:System.Windows.Interop.HwndHost> を取得するので、ホスト アプリケーションは <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A> から返されるオブジェクトを、アドインによって実装された型 \(<xref:System.Windows.Controls.UserControl> など\) に変換できません。  
  
 その特質上、<xref:System.Windows.Interop.HwndHost> には、ホスト アプリケーションの使用に影響する制約があります。  ただし、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、<xref:System.Windows.Interop.HwndHost> をアドイン シナリオ用の一部の機能で拡張します。  その利点と制約について以下に説明します。  
  
<a name="WPFAddInModelBenefits"></a>   
## WPF アドインの利点  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アドイン [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] は、<xref:System.Windows.Interop.HwndHost> から派生する内部クラスを使用してホスト アプリケーションで表示されるため、そのような [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] は、レイアウト、レンダリング、データ バインド、スタイル、テンプレート、リソースなどの [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] サービスに関して、<xref:System.Windows.Interop.HwndHost> の機能の制約を受けます。  ただし、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、その内部 <xref:System.Windows.Interop.HwndHost> サブクラスを、次のような追加機能で強化します。  
  
-   ホスト アプリケーションの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] とアドインの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] との間を Tab キーで移動できます。  "アドインが [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] である" プログラミング モデルでは、アドインが完全に信頼されているか部分的に信頼されているかに関係なく、アドイン側のアダプターが <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> をオーバーライドして、Tab キーによる移動処理を有効にする必要があります。  
  
-   ホスト アプリケーション [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] で表示されるアドイン [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] のアクセシビリティ要件を順守します。  
  
-   アプリケーション ドメインが複数あるシナリオで [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションが安全に実行されます。  
  
-   アドインがセキュリティ分離を使用して実行されている場合 \(部分的に信頼されているセキュリティ サンドボックス\)、アドイン [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ウィンドウ ハンドルへの不正アクセスを回避します。  <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> を呼び出すことでこのセキュリティが保証されます。  
  
    -   "アドインが [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を返す" プログラミング モデルで、アドイン [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] のウィンドウ ハンドルを分離境界を越えて渡す唯一の方法は、<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> を呼び出すことです。  
  
    -   "アドインが [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] である" プログラミング モデルでは、アドイン側のアダプターで <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> をオーバーライドして <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> を呼び出すこと \(前の例に従って\) が、アドイン側のアダプターの `QueryContract` 実装をホスト側のアダプターから呼び出すことに相当する処理として必要です。  
  
-   アプリケーション ドメインの実行を何重にも保護します。  アプリケーション ドメインの制約に起因して、アドイン アプリケーション ドメインでスローされた未処理の例外は、分離境界が存在していても、アプリケーション全体のクラッシュにつながります。  ただし、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アドイン モデルおよび [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アドイン モデルは、この問題を回避し、アプリケーションの安定性を向上させる簡単な手段を提供します。  [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を表示する [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アドインは、ホスト アプリケーションが [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションである場合に、アプリケーション ドメインが実行されているスレッドの <xref:System.Windows.Threading.Dispatcher> を作成します。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アドインの <xref:System.Windows.Threading.Dispatcher> の <xref:System.Windows.Threading.Dispatcher.UnhandledException> イベントを処理することで、アプリケーション ドメインで発生した未処理の例外をすべて検出できます。  <xref:System.Windows.Threading.Dispatcher> は、<xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A> プロパティから取得できます。  
  
<a name="WPFAddInModelLimitations"></a>   
## WPF アドインの制約  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、<xref:System.Windows.Interop.HwndSource>、<xref:System.Windows.Interop.HwndHost>、およびウィンドウ ハンドルによる既定の動作に利点をもたらしますが、ホスト アプリケーションで表示されるアドイン [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] に対する制約もあります。  
  
-   ホスト アプリケーションで表示されるアドイン [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] では、ホスト アプリケーションのクリッピング動作が考慮されません。  
  
-   相互運用性シナリオの*空域*の概念もアドインに適用されます \(「[技術領域の概要](../../../../docs/framework/wpf/advanced/technology-regions-overview.md)」を参照\)。  
  
-   リソースの継承、データ バインディング、コマンド実行など、ホスト アプリケーションの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] サービスは、アドイン [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] で自動的に使用可能化されないためです。  このサービスをアドインに提供するには、パイプラインを更新する必要があります。  
  
-   アドイン [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] に回転、拡大縮小、傾斜などの変換は適用できません \(「[変換の概要](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)」を参照\)。  
  
-   <xref:System.Drawing> 名前空間の描画操作によって描画されるアドイン [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] 内のコンテンツに、アルファ ブレンド効果を含めることができます。  ただし、それを含むアドイン [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] とホスト アプリケーション [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] のいずれも、完全に不透明である必要があります。言い換えると、どちらについても `Opacity` プロパティが 1 に設定されている必要があります。  
  
-   アドイン [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を含むホスト アプリケーションのウィンドウの <xref:System.Windows.Window.AllowsTransparency%2A> プロパティが `true` の場合、アドインは非表示になります。  このことは、アドイン [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] が完全に不透明 \(`Opacity` プロパティの値が 1\) の場合にも該当します。  
  
-   アドイン [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] は、同じトップレベル ウィンドウ内の他の [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 要素より前面に表示する必要があります。  
  
-   アドインの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] には、<xref:System.Windows.Media.VisualBrush> を使用して描画できる部分はありません。  その代わり、アドインは生成された [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] のスナップショットを取り、コントラクトで定義されているメソッドを使用してホスト アプリケーションに渡すことができるビットマップを作成できます。  
  
-   メディア ファイルをアドイン [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 内の <xref:System.Windows.Controls.MediaElement> で再生することはできません。  
  
-   ホスト アプリケーションがアドイン [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 用に生成されたマウス イベントを発生させたり、受け取ったりすることはなく、ホスト アプリケーション [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] の `IsMouseOver` プロパティの値は `false` に設定されます。  
  
-   アドイン [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 内のコントロール間を、フォーカスが移動しても、`GotFocus` イベントおよび `LostFocus` イベントをホスト アプリケーションで受け取ったり、発生したりすることはありません。  
  
-   アドイン [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を含むホスト アプリケーション部分は、印刷時には白く出力されます。  
  
-   アドイン [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] によって作成されたすべてのディスパッチャー \(「<xref:System.Windows.Threading.Dispatcher>」を参照\) は、ホスト アプリケーションが実行を継続する場合、オーナー アドインがアンロードされる前に手動でシャットダウンする必要があります。  コントラクトは、アドインがアンロードされる前にホスト アプリケーションがアドインにシグナルを送信するためのメソッドを実装でき、それによりアドイン [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] がそのディスパッチャーをシャットダウンできます。  
  
-   アドイン [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] が <xref:System.Windows.Controls.InkCanvas> である場合、または <xref:System.Windows.Controls.InkCanvas> を含んでいる場合、そのアドインをアンロードすることはできません。  
  
<a name="PerformanceOptimization"></a>   
## パフォーマンスの最適化  
 既定では、複数のアプリケーション ドメインが使用されていると、各アプリケーションで必要とされているさまざまな [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アセンブリがすべてそのアプリケーションのドメインに読み込まれます。  その結果、新しいアプリケーション ドメインを作成してその中でアプリケーションを起動するために必要な時間がパフォーマンスに影響します。  ただし、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] には、アプリケーションに必要なアセンブリが既に読み込まれている場合に、それをアプリケーション ドメイン間で共有するよう指示することで起動時間を短縮する手段が用意されています。  これを行うには、<xref:System.LoaderOptimizationAttribute> 属性を使用します。これを、エントリ ポイント メソッド \(`Main`\) に適用する必要があります。  この場合、アプリケーション定義を実装するコードのみを使用する必要があります \(「[アプリケーション管理の概要](../../../../docs/framework/wpf/app-development/application-management-overview.md)」を参照\)。  
  
## 参照  
 <xref:System.LoaderOptimizationAttribute>   
 [アドインおよび拡張機能](../../../../ml/index.xml)   
 [アプリケーション ドメイン](../../../../docs/framework/app-domains/application-domains.md)   
 [.NET Framework Remoting Overview](http://msdn.microsoft.com/ja-jp/eccb1d31-0a22-417a-97fd-f4f1f3aa4462)   
 [Making Objects Remotable](http://msdn.microsoft.com/ja-jp/01197253-3f13-43b7-894d-9683e431192a)   
 [方法のトピック](../../../../docs/framework/wpf/app-development/how-to-topics.md)