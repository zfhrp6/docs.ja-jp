---
title: "WPF アドインの概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- add-ins and XAML browser applications [WPF]
- add-ins overview [WPF]
- add-ins [WPF], performance
- add-ins [WPF], benefits
- .NET Framework add-in model [WPF]
- add-ins [WPF], user interface
- add-ins and the user interface [WPF]
- add-ins [WPF], architecture
- add-ins [WPF], limitations
ms.assetid: 00b4c776-29a8-4dba-b603-280a0cdc2ade
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ffd45957b41cdfd8488aedd865aa70ef5b2634b2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="wpf-add-ins-overview"></a>WPF アドインの概要
<a name="Introduction"></a> [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] には、開発者がアドイン機能拡張をサポートするアプリケーションの作成に使用できるアドイン モデルが用意されています。 このアドイン モデルを使用することで、アプリケーション機能に統合され、アプリケーション機能を拡張するアドインを作成できます。 一部のシナリオでは、アドインが提供する [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] をアプリケーションで表示する必要があります。このトピックでは、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] が [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アドイン モデルを強化してこうしたシナリオを実現するしくみ、背後にあるアーキテクチャ、その利点、および制限事項について説明します。  
  

  
<a name="Requirements"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アドイン モデルを十分に理解していることが必要です。 詳細については、「[アドインおよび拡張機能](../../../../docs/framework/add-ins/index.md)」を参照してください。  
  
<a name="AddInsOverview"></a>   
## <a name="add-ins-overview"></a>アドインの概要  
 新しい機能を追加するためにアプリケーションを再コンパイルして再配置する手間を省くことを目的として、アプリケーションは機能拡張メカニズムを実装し、開発者 (ファーストパーティ、サードパーティのいずれも) が元のアプリケーションに統合される別のアプリケーションを作成できるようにしています。 こうした拡張機能をサポートする方法としては、アドイン ("アドオン"、"プラグイン" などとも呼ばれる) の使用が最も一般的です。 アドインによる機能拡張を公開する実際のアプリケーションとして、次のようなものが挙げられます。  
  
-   Internet Explorer のアドオン。  
  
-   Windows Media Player のプラグイン。  
  
-   Visual Studio のアドイン。  
  
 たとえば、Windows Media Player のアドイン モデルにおいて、サードパーティの開発者は、Windows Media Player の機能をさまざまな形で拡張する "プラグイン" を実装できます。たとえば、Windows Media Player でネイティブにサポートされていないメディア形式 (DVD、MP3 など) のデコーダーおよびエンコーダー、オーディオ効果、スキンなどを作成できます。 各アドイン モデルは、アプリケーション固有の機能を公開するためにビルドされますが、どのアドイン モデルにも共通するエンティティや動作がいくつかあります。  
  
 典型的な機能拡張ソリューションの主な 3 つのエンティティは、*コントラクト*、*アドイン*、および*ホスト アプリケーション*です。 コントラクトは、次の 2 つの方法で、アドインとホスト アプリケーションとの統合方法を定義します。  
  
-   アドインは、ホスト アプリケーションによって実装される機能と統合されます。  
  
-   ホスト アプリケーションで、アドインを統合するための機能を公開します。  
  
 アドインを使用するには、ホスト アプリケーションが実行時にアドインを検索して読み込む必要があります。 したがって、アドインをサポートするアプリケーションには次の機能が必要です。  
  
-   **探索**: ホスト アプリケーションによってサポートされるコントラクトに準拠しているアドインを検索します。  
  
-   **アクティブ化**: アドインを読み込んで実行し、アドインとの通信を確立します。  
  
-   **分離**: アプリケーション ドメインまたはアプリケーション プロセスを使用することで他から切り離すための境界を確立し、アドインの使用に伴うセキュリティおよび実行に関する潜在的な問題からアプリケーションを保護します。  
  
-   **通信**: アドインとホスト アプリケーションが分離境界を越えて通信し、メソッドを呼び出したりデータを渡したりできるようにします。  
  
-   **有効期間管理**: アプリケーション ドメインとアプリケーション プロセスの読み込みおよびアンロードを、クリーンで予測可能な方法で行います (「[アプリケーション ドメイン](../../../../docs/framework/app-domains/application-domains.md)」を参照)。  
  
-   **バージョン管理**: ホスト アプリケーションとアドインのどちらかに、新バージョンが作成された後も引き続き通信できるようにします。  
  
 このことからわかるように、堅牢なアドイン モデルの開発は簡単なことではありません。 そのため、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] にはアドイン モデルのビルド用のインフラストラクチャが用意されています。  
  
> [!NOTE]
>  アドインの詳細については、「[アドインおよび拡張機能](../../../../docs/framework/add-ins/index.md)」を参照してください。  
  
<a name="NETFrameworkAddInModelOverview"></a>   
## <a name="net-framework-add-in-model-overview"></a>.NET Framework アドイン モデルの概要  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]アドイン モデルで見つかった、<xref:System.AddIn>名前空間には、アドインでは、拡張機能の開発を簡略化できるように設計された型のセットが含まれています。 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アドイン モデルの基本単位は*コントラクト*です。コントラクトは、ホスト アプリケーションとアドイン間の通信方法を定義します。 コントラクトのホスト アプリケーション固有の*ビュー*を使用して、コントラクトはホスト アプリケーションに公開されます。 同様に、コントラクトのアドイン固有の*ビュー*がアドインに公開されます。 *アダプター*は、ホスト アプリケーションとアドインが、コントラクトの対応するビュー間で通信するために使用されます。 コントラクト、ビュー、およびアダプターはセグメントと見なされ、関連セグメントのセットが*パイプライン*を構成します。 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アドイン モデルはパイプラインを基盤とし、それを基に探索、アクティブ化、セキュリティ分離、実行分離 (アプリケーションのドメインとプロセスを両方使用)、通信、有効期間管理、およびバージョン管理をサポートします。  
  
 このサポート全体を使用して、開発者はホスト アプリケーションの機能を統合するアドインをビルドできます。 ただし、一部のシナリオでは、アドインが提供する [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] をホスト アプリケーションで表示する必要があります。[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の各プレゼンテーション テクノロジには [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] 実装の独自のモデルがあるため、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アドイン モデルは特定のプレゼンテーション テクノロジをサポートしません。 その代わり、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] では [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アドイン モデルをアドインの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] サポートという形で機能拡張します。  
  
<a name="WPFAddInModel"></a>   
## <a name="wpf-add-ins"></a>WPF アドイン  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] を [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アドイン モデルと併用することで、ホスト アプリケーションでアドインの [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] を表示する必要があるさまざまなシナリオに対応できます。特に、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] によるこれらのシナリオの対応には、次の 2 つのプログラミング モデルが使用されます。  
  
1.  **アドインが UI を返す**。 アドインが、コントラクトの定義に従って、メソッド呼び出しを介してホスト アプリケーションに [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を返します。 このシナリオは、次の場合に使用されます。  
  
    -   アドインが返す [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] の外観が、動的に生成されるレポートなど、実行時にしか存在しないデータまたは条件に依存している。  
  
    -   アドインが提供するサービスの[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] が、そのアドインを使用できるホスト アプリケーションの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] と異なっている。  
  
    -   アドインは主にホスト アプリケーション向けのサービスを実行し、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を使用してホスト アプリケーションにステータスをレポートする。  
  
2.  **アドインが UI である**。 アドインが、コントラクトの定義に従う [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] です。 このシナリオは、次の場合に使用されます。  
  
    -   アドインは表示以外のサービス (広告など) を提供しない。  
  
    -   アドインが提供するサービスの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] は、そのアドインを使用できるすべてのホスト アプリケーションで共通である (電卓、カラー ピッカーなど)。  
  
 これらのシナリオでは、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] オブジェクトをホスト アプリケーション ドメインとアドイン アプリケーション ドメインとの間で受け渡しできる必要があります。 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アドイン モデルは、アプリケーション ドメイン間の通信においてリモート処理に依存しているため、それらの間で受け渡しされるオブジェクトはリモート処理可能である必要があります。  
  
 リモート処理可能なオブジェクトとは、次の 1 つ以上に該当するクラスのインスタンスです。  
  
-   派生した、<xref:System.MarshalByRefObject>クラスです。  
  
-   <xref:System.Runtime.Serialization.ISerializable> インターフェイスを実装します。  
  
-   <xref:System.SerializableAttribute>属性を適用します。  
  
> [!NOTE]
>  リモート処理可能な [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] オブジェクトの作成の詳細については、「[オブジェクトをリモート処理可能にする](http://msdn.microsoft.com/library/01197253-3f13-43b7-894d-9683e431192a)」を参照してください。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 型は、リモート処理可能ではありません。 この問題を解決するため、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アドイン モデルを拡張して、アドインによって作成される [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] をホスト アプリケーションで表示できるようにします。 このサポートによって提供されます[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]によって 2 つの種類:<xref:System.AddIn.Contract.INativeHandleContract>インターフェイスとによって実装される 2 つの静的メソッド、<xref:System.AddIn.Pipeline.FrameworkElementAdapters>クラス:<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>と<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>です。 大まかに、これらの型とメソッドは次のように使用されます。  
  
1.  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]いる必要があります[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]によって提供される、アドインから直接または間接的に派生するクラスは、<xref:System.Windows.FrameworkElement>図形、コントロール、ユーザー コントロール、レイアウト パネル、およびページなどです。  
  
2.  として宣言する必要がありますコントラクトは、UI をアドインとホスト アプリケーションの間で渡されることを宣言する限り、 <xref:System.AddIn.Contract.INativeHandleContract> (されません、 <xref:System.Windows.FrameworkElement>) です。<xref:System.AddIn.Contract.INativeHandleContract>アドインでのリモート処理可能な表現である[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]分離の境界を越えて渡すことです。  
  
3.  アドインのアプリケーションのドメインから渡される前に、<xref:System.Windows.FrameworkElement>としてパッケージ化、<xref:System.AddIn.Contract.INativeHandleContract>を呼び出して<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>です。  
  
4.  ホスト アプリケーションのアプリケーション ドメインに渡された後、<xref:System.AddIn.Contract.INativeHandleContract>として再パッケージ化する必要があります、<xref:System.Windows.FrameworkElement>を呼び出して<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>です。  
  
 方法<xref:System.AddIn.Contract.INativeHandleContract>、 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>、および<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>使用は、特定のシナリオによって異なります。 以降のセクションでは、各プログラミング モデルについて詳しく説明していきます。  
  
<a name="ReturnUIFromAddInContract"></a>   
## <a name="add-in-returns-a-user-interface"></a>ユーザー インターフェイスを返すアドイン  
 アドインが [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] をホスト アプリケーションに返すには、次のことが必要です。  
  
1.  ホスト アプリケーション、アドイン、およびパイプラインが、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の「[アドインおよび拡張機能](../../../../docs/framework/add-ins/index.md)」の説明に従って作成されている必要があります。  
  
2.  コントラクトを実装する必要があります<xref:System.AddIn.Contract.IContract>およびを返す、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、コントラクト型の戻り値を持つメソッドを宣言する必要があります<xref:System.AddIn.Contract.INativeHandleContract>です。  
  
3.  [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]渡されるアドインとホスト間でアプリケーション直接的または間接的にから派生しなければなりません<xref:System.Windows.FrameworkElement>です。  
  
4.  [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]によって返されるアドインから変換する必要があります、<xref:System.Windows.FrameworkElement>を<xref:System.AddIn.Contract.INativeHandleContract>分離境界を横断する前にします。  
  
5.  [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]から変換する必要があるれる、<xref:System.AddIn.Contract.INativeHandleContract>を<xref:System.Windows.FrameworkElement>後、分離境界を越えます。  
  
6.  ホスト アプリケーションは、表示、返された<xref:System.Windows.FrameworkElement>です。  
  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を返すアドインを実装する方法の例については、「[方法 : UI を返すアドインを作成する](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-returns-a-ui.md)」を参照してください。  
  
<a name="AddInIsAUI"></a>   
## <a name="add-in-is-a-user-interface"></a>ユーザー インターフェイスであるアドイン  
 アドインが [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] である場合、次のことが必要です。  
  
1.  ホスト アプリケーション、アドイン、およびパイプラインが、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の「[アドインおよび拡張機能](../../../../docs/framework/add-ins/index.md)」の説明に従って作成されている必要があります。  
  
2.  アドインのコントラクト インターフェイスを実装する必要があります<xref:System.AddIn.Contract.INativeHandleContract>です。  
  
3.  ホスト アプリケーションに渡されるアドインを直接または間接的にから派生しなければなりません<xref:System.Windows.FrameworkElement>です。  
  
4.  アドインから変換する必要があります、<xref:System.Windows.FrameworkElement>を<xref:System.AddIn.Contract.INativeHandleContract>分離境界を横断する前にします。  
  
5.  アドインから変換する必要があります、<xref:System.AddIn.Contract.INativeHandleContract>を<xref:System.Windows.FrameworkElement>後、分離境界を越えます。  
  
6.  ホスト アプリケーションは、表示、返された<xref:System.Windows.FrameworkElement>です。  
  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] であるアドインを実装する方法の例については、「[方法 : UI であるアドインを作成する](../../../../docs/framework/wpf/app-development/how-to-create-an-add-in-that-is-a-ui.md)」を参照してください。  
  
<a name="ReturningMultipleUIsFromAnAddIn"></a>   
## <a name="returning-multiple-uis-from-an-add-in"></a>複数の UI を返すアドイン  
 アドインが提供する複数の [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] をホスト アプリケーションが表示するケースはよくあります。 たとえば、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] であるアドインが、ホスト アプリケーションにステータス情報も [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] として提供するとします。 このようなアドインは、[ユーザー インターフェイスを返すアドイン](#ReturnUIFromAddInContract)のモデルと[ユーザー インターフェイスであるアドイン](#AddInIsAUI)のモデルの両方の手法を組み合わせることで実装できます。  
  
<a name="AddInsAndXBAPs"></a>   
## <a name="add-ins-and-xaml-browser-applications"></a>アドインと XAML ブラウザー アプリケーション  
 ここまでの例では、ホスト アプリケーションはスタンドアロン アプリケーションとしてインストールされています。 [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] はアドインをホストすることもできますが、そのためには次に示すビルドと実装の要件を満たす必要があります。  
  
-   パイプライン (フォルダーとアセンブリ) とアドイン アセンブリを、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] と同じフォルダーにある、クライアント コンピューターの [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] アプリケーション キャッシュにダウンロードするよう、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] アプリケーション マニフェストを特別に構成する必要があります。  
  
-   アドインを探索して読み込む [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] コードで、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] の [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] アプリケーション キャッシュを、パイプラインとアドインの場所として使用する必要があります。  
  
-   [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] は、アドインが起点サイトにある圧縮しないファイルを参照する場合、アドインを特別なセキュリティ コンテキストの下で読み込む必要があります。[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] によってホストされる場合、アドインが参照できるのは、ホスト アプリケーションの起点サイトにある圧縮しないファイルのみです。  
  
 これらのタスクについて、次のサブセクションで詳しく説明します。  
  
### <a name="configuring-the-pipeline-and-add-in-for-clickonce-deployment"></a>ClickOnce 配置のためのパイプラインとアドインの構成  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] は、[!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] 配置キャッシュの安全なフォルダーにダウンロードされ、そこから実行されます。 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] でアドインをホストするには、パイプラインとアドインのアセンブリも同じ安全なフォルダーにダウンロードする必要があります。 このためには、パイプラインとアドインのどちらのアセンブリもダウンロード対象に含まれるよう、アプリケーション マニフェストを構成する必要があります。 これは、[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] で実行することが最も簡単ですが、[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] でパイプラインをアセンブリとして検出するには、パイプラインとアドインのアセンブリが、ホスト [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] プロジェクトのルート フォルダーに存在する必要があります。  
  
 したがって、まず、パイプライン アセンブリとアドイン アセンブリの各プロジェクトのビルド出力を設定し、パイプラインとアドインのアセンブリを [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] プロジェクトのルートにビルドします。 次の表は、ホストの [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] プロジェクトと同じソリューションとルートのフォルダーに格納される、パイプライン アセンブリ プロジェクトとアドイン アセンブリ プロジェクトのビルド出力パスを示します。  
  
 表 1: XBAP でホストされるパイプライン アセンブリのビルド出力パス  
  
|パイプライン アセンブリ プロジェクト|ビルド出力パス|  
|-------------------------------|-----------------------|  
|コントラクト|`..\HostXBAP\Contracts\`|  
|アドイン ビュー|`..\HostXBAP\AddInViews\`|  
|アドイン側のアダプター|`..\HostXBAP\AddInSideAdapters\`|  
|ホスト側のアダプター|`..\HostXBAP\HostSideAdapters\`|  
|アドイン|`..\HostXBAP\AddIns\WPFAddIn1`|  
  
 次に、パイプライン アセンブリとアドイン アセンブリを [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] コンテンツ ファイルとして [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] に指定します。手順は次のとおりです。  
  
1.  ソリューション エクスプローラーで各パイプライン フォルダーを右クリックし、**[プロジェクトに含める]** を選択して、パイプラインとアドインのアセンブリをプロジェクトに含めます。  
  
2.  **[プロパティ]** ウィンドウで、パイプライン アセンブリとアドイン アセンブリそれぞれについて、**[ビルド アクション]** を **[コンテンツ]** に設定します。  
  
 最後に、パイプラインとアドインのどちらのアセンブリ ファイルもダウンロード対象に含まれるよう、アプリケーション マニフェストを構成します。 ファイルは、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] アプリケーションが占有する [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] キャッシュ内のフォルダーのルートにあるフォルダー内に存在している必要があります。 この構成は、次の手順に従って、[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] で行うことができます。  
  
1.  [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] プロジェクトを右クリックして、**[プロパティ]**、**[発行]** の順にクリックし、**[アプリケーション ファイル]** をクリックします。  
  
2.  **[アプリケーション ファイル]** ダイアログ ボックスで、各パイプラインとアドインの DLL の **[発行の状況]** を **[含める (自動)]** に設定し、各パイプラインとアドインの DLL の **[ダウンロード グループ]** を **[(必須)]** に設定します。  
  
### <a name="using-the-pipeline-and-add-in-from-the-application-base"></a>アプリケーション ベースからのパイプラインとアドインの使用  
 パイプラインとアドインは [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] 配置用に構成されると、同じ [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] キャッシュ フォルダーに [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] としてダウンロードされます。 このパイプラインとアドインを [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] から使用するには、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] コードがそれらをアプリケーション ベースから取得する必要があります。 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アドイン モデルのさまざまな型やメンバーは、パイプラインおよびアドインを使用できるよう、このシナリオ用に特別なサポートを提供しています。 まず、パスは、によって識別される、<xref:System.AddIn.Hosting.PipelineStoreLocation.ApplicationBase>列挙値。 この値を適切なアドイン メンバーのオーバーロードと併用することで、次のようなパイプラインを使用できます。  
  
-   <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.FindAddIns%28System.Type%2CSystem.AddIn.Hosting.PipelineStoreLocation%2CSystem.String%5B%5D%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.Rebuild%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
-   <xref:System.AddIn.Hosting.AddInStore.Update%28System.AddIn.Hosting.PipelineStoreLocation%29?displayProperty=nameWithType>  
  
### <a name="accessing-the-hosts-site-of-origin"></a>ホストの起点サイトへのアクセス  
 アドインが起点サイトのファイルを参照できるように、アドインはホスト アプリケーションと等価なセキュリティ分離を使用して読み込む必要があります。 このセキュリティ レベルがによって識別される、<xref:System.AddIn.Hosting.AddInSecurityLevel.Host?displayProperty=nameWithType>列挙値に渡されると、<xref:System.AddIn.Hosting.AddInToken.Activate%2A>アドインをアクティブ化されるメソッド。  
  
<a name="WPFAddInModelArchitecture"></a>   
## <a name="wpf-add-in-architecture"></a>WPF アドイン アーキテクチャ  
 最上位のレベルでは、これまで見てきたよう[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]により[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]を実装するアドイン[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)](から直接的または間接的に派生した<xref:System.Windows.FrameworkElement>) を使用して<xref:System.AddIn.Contract.INativeHandleContract>、<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>と<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>です。 結果は、ホスト アプリケーションが返される、<xref:System.Windows.FrameworkElement>から表示される、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]ホスト アプリケーションにします。  
  
 簡単な [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] アドイン シナリオでは、開発者に必要な詳細はこれだけです。 より複雑なシナリオ、特にレイアウト、リソース、データ バインドなど、追加の [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] サービスの活用を想定したシナリオでは、その利点と制約を把握するために [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] をサポートする [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アドイン モデルが、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] で拡張されるしくみについて詳しい知識が必要です。  
  
 基本的に、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] をアドインからホスト アプリケーションに渡しません。その代わり、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] の Win32 ウィンドウ ハンドルを [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 相互運用性を使用して渡します。 つまり、アドインの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] がホスト アプリケーションに渡されると、次の処理が行われます。  
  
-   アドイン側で、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、ホスト アプリケーションによって表示される [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] のウィンドウ ハンドルを取得します。 ウィンドウ ハンドルが内部でカプセル化された[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]から派生したクラス<xref:System.Windows.Interop.HwndSource>を実装して<xref:System.AddIn.Contract.INativeHandleContract>です。 このクラスのインスタンスがによって返される<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>はアドインのアプリケーション ドメインから、ホスト アプリケーションのアプリケーション ドメインにマーシャ リングとします。  
  
-   ホスト アプリケーション側で[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]は再パッケージ化、<xref:System.Windows.Interop.HwndSource>内部として[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]から派生したクラス<xref:System.Windows.Interop.HwndHost>消費<xref:System.AddIn.Contract.INativeHandleContract>です。 このクラスのインスタンスがによって返される<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>ホスト アプリケーションにします。  
  
 <xref:System.Windows.Interop.HwndHost>表示に存在する[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]から、ウィンドウ ハンドルによって識別される[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)][!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]です。 詳細については、「[WPF と Win32 の相互運用性](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)」を参照してください。  
  
 要約すると、 <xref:System.AddIn.Contract.INativeHandleContract>、 <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>、および<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>のウィンドウ ハンドルを許可するのには存在、 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]から、アドインによってカプセル化は、ホスト アプリケーションに渡される、<xref:System.Windows.Interop.HwndHost>とホストの表示アプリケーションの[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]します。  
  
> [!NOTE]
>  ホスト アプリケーションを取得するため、 <xref:System.Windows.Interop.HwndHost>、ホスト アプリケーションは、によって返されるオブジェクトを変換できません<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>アドインによって、型に実装されます (たとえば、 <xref:System.Windows.Controls.UserControl>)。  
  
 、その性質上<xref:System.Windows.Interop.HwndHost>ホスト アプリケーションが使用できる方法に影響する特定の制限があります。 ただし、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]拡張<xref:System.Windows.Interop.HwndHost>アドインでは、シナリオのいくつかの機能を持つ。 その利点と制約について、以下に説明します。  
  
<a name="WPFAddInModelBenefits"></a>   
## <a name="wpf-add-in-benefits"></a>WPF アドインの利点  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アドイン[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]から派生する内部クラスを使用してホスト アプリケーションから表示される<xref:System.Windows.Interop.HwndHost>、those[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]の機能によって制限されて<xref:System.Windows.Interop.HwndHost>に関連する[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]レイアウト、レンダリング、データ バインディング、スタイル、テンプレート、およびリソースなどのサービスです。 ただし、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]は強化し、その内部<xref:System.Windows.Interop.HwndHost>サブクラスを次を含む追加の機能を備えた。  
  
-   ホスト アプリケーションの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] とアドインの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] との間を Tab キーで移動できます。 注意してください、"アドインでは、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]"プログラミング モデルには、オーバーライドするアドイン側アダプターが必要です。<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>アドインが完全に信頼できるまたは部分的に信頼されているかどうか、tab キーを有効にします。  
  
-   ホスト アプリケーション [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] で表示されるアドイン [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] のアクセシビリティ要件を順守します。  
  
-   アプリケーション ドメインが複数あるシナリオで [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションが安全に実行されます。  
  
-   アドインがセキュリティ分離を使用して実行されている場合 (部分的に信頼されているセキュリティ サンドボックス)、アドイン [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ウィンドウ ハンドルへの不正アクセスを回避します。 呼び出す<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>このセキュリティを確保します。  
  
    -   に対して、"アドインから返されます、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]"プログラミング モデル、アドインでのウィンドウ ハンドルを渡す唯一の方法[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]分離間で境界が呼び出されて<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>です。  
  
    -   "アドインでは、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]"プログラミング モデル、オーバーライドする<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A>アドイン側アダプターと呼び出し元に<xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>(前の例に示す) が必要がありますアドイン側アダプターの呼び出しとして`QueryContract`実装。ホスト側のアダプターです。  
  
-   アプリケーション ドメインの実行を何重にも保護します。 アプリケーション ドメインの制約に起因して、アドイン アプリケーション ドメインでスローされた未処理の例外は、分離境界が存在していても、アプリケーション全体のクラッシュにつながります。 ただし、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アドイン モデルおよび [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アドイン モデルは、この問題を回避して、アプリケーションの安定性を向上させる簡単な手段を提供します。 A[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アドインを表示する、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]を作成、<xref:System.Windows.Threading.Dispatcher>の場合は、ホスト アプリケーションは、アプリケーション ドメインで実行されているスレッドの[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アプリケーションです。 処理することにより、アプリケーション ドメインで発生したすべての未処理の例外を検出することができます、<xref:System.Windows.Threading.Dispatcher.UnhandledException>のイベント、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アドインの<xref:System.Windows.Threading.Dispatcher>します。 取得することができます、<xref:System.Windows.Threading.Dispatcher>から、<xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A>プロパティです。  
  
<a name="WPFAddInModelLimitations"></a>   
## <a name="wpf-add-in-limitations"></a>WPF アドインの制約  
 利点以外を[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]によって提供される既定の動作に追加<xref:System.Windows.Interop.HwndSource>、 <xref:System.Windows.Interop.HwndHost>、およびウィンドウ ハンドルのアドインの制限があります[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]ホスト アプリケーションから表示します。  
  
-   ホスト アプリケーションで表示されるアドイン [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] では、ホスト アプリケーションのクリッピング動作が考慮されません。  
  
-   相互運用性シナリオの*空域*の概念もアドインに適用されます (「[技術領域の概要](../../../../docs/framework/wpf/advanced/technology-regions-overview.md)」を参照)。  
  
-   リソースの継承、データ バインディング、コマンド実行など、ホスト アプリケーションの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] サービスは、アドイン [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] で自動的には使用可能になりません。 これらのサービスをアドインに提供するには、パイプラインを更新する必要があります。  
  
-   アドイン [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] に回転、拡大縮小、傾斜などの変換は適用できません (「[変換の概要](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)」を参照)。  
  
-   アドインでは、内部コンテンツ[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]からの操作を描画することによってレンダリングされる、<xref:System.Drawing>アルファ ブレンド名前空間を含めることができます。 ただし、それを含むアドイン [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] とホスト アプリケーション [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] のいずれも、100% 不透明である必要があります。言い換えると、どちらについても `Opacity` プロパティが 1 に設定されている必要があります。  
  
-   場合、<xref:System.Windows.Window.AllowsTransparency%2A>追加で格納しているホスト アプリケーションのウィンドウのプロパティ[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]に設定されている`true`アドインでは表示されません。 このことは、アドイン [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] が 100% 不透明 (`Opacity` プロパティの値が 1) の場合にも該当します。  
  
-   アドイン [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] は、同じトップレベル ウィンドウ内の他の [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 要素より前面に表示する必要があります。  
  
-   アドインの部分はありません[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]を使用して表示することができます、<xref:System.Windows.Media.VisualBrush>です。 その代わり、アドインは生成された [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] のスナップショットを取り、コントラクトで定義されているメソッドを使用してホスト アプリケーションに渡すことができるビットマップを作成できます。  
  
-   メディア ファイルを再生することはできません、<xref:System.Windows.Controls.MediaElement>アドインで[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]です。  
  
-   ホスト アプリケーションがアドイン [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 用に生成されたマウス イベントを受け取ったり、発生させたりすることはなく、ホスト アプリケーション [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] の `IsMouseOver` プロパティの値は `false` に設定されます。  
  
-   アドイン [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 内のコントロール間を、フォーカスが移動しても、`GotFocus` イベントおよび `LostFocus` イベントをホスト アプリケーションで受け取ったり、発生したりすることはありません。  
  
-   アドイン [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を含むホスト アプリケーション部分は、印刷時には白く出力されます。  
  
-   すべてのディスパッチャー (を参照してください<xref:System.Windows.Threading.Dispatcher>)、アドインによって作成された[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]必要がある手動でシャット ダウンに所有者のアドインが読み込み解除される場合は、ホスト アプリケーションが実行を継続します。 コントラクトは、アドインがアンロードされる前にホスト アプリケーションがアドインにシグナルを送信するためのメソッドを実装でき、それによりアドイン [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] がそのディスパッチャーをシャットダウンできます。  
  
-   場合、アドイン[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]は、<xref:System.Windows.Controls.InkCanvas>または含まれている、 <xref:System.Windows.Controls.InkCanvas>、アドインをアンロードすることはできません。  
  
<a name="PerformanceOptimization"></a>   
## <a name="performance-optimization"></a>パフォーマンスの最適化  
 既定では、複数のアプリケーション ドメインが使用されていると、各アプリケーションで必要とされているさまざまな [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アセンブリがすべてそのアプリケーションのドメインに読み込まれます。 その結果、新しいアプリケーション ドメインを作成してその中でアプリケーションを開始するために必要な時間がパフォーマンスに影響します。 ただし、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] には、アセンブリが既に読み込まれている場合に、それをアプリケーション ドメイン間で共有するようアプリケーションに指示することで開始時間を短縮する手段が用意されています。 使用して、これを行う、<xref:System.LoaderOptimizationAttribute>属性は、エントリ ポイント メソッドに適用する必要があります (`Main`)。 この場合、アプリケーション定義を実装するコードのみを使用する必要があります (「[アプリケーション管理の概要](../../../../docs/framework/wpf/app-development/application-management-overview.md)」を参照)。  
  
## <a name="see-also"></a>参照  
 <xref:System.LoaderOptimizationAttribute>  
 [アドインおよび拡張機能](../../../../docs/framework/add-ins/index.md)  
 [アプリケーション ドメイン](../../../../docs/framework/app-domains/application-domains.md)  
 [.NET framework リモート処理の概要](http://msdn.microsoft.com/library/eccb1d31-0a22-417a-97fd-f4f1f3aa4462)  
 [オブジェクトをリモート処理可能](http://msdn.microsoft.com/library/01197253-3f13-43b7-894d-9683e431192a)  
 [方法トピック](../../../../docs/framework/wpf/app-development/how-to-topics.md)
