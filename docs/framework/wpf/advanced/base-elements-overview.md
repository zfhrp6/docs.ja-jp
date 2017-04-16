---
title: "基本要素の概要 | Microsoft Docs"
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
  - "基本要素"
ms.assetid: 2c997092-72c6-4767-bc84-74267f4eee72
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 基本要素の概要
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のクラスの大部分は、[!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] のドキュメントで一般に基本要素クラスと呼ばれている 4 つのクラスから派生しています。  このようなクラスとしては、<xref:System.Windows.UIElement>、<xref:System.Windows.FrameworkElement>、<xref:System.Windows.ContentElement>、および <xref:System.Windows.FrameworkContentElement> があります。  <xref:System.Windows.DependencyObject> クラスも関連がありますが、これは <xref:System.Windows.UIElement> と <xref:System.Windows.ContentElement> の両方に共通する基本クラスであるためです。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="base_apis"></a>   
## WPF クラスの基本要素 API  
 <xref:System.Windows.UIElement> および <xref:System.Windows.ContentElement> は、どちらも <xref:System.Windows.DependencyObject> から派生していますが、その方法は多少異なります。  このレベルでの相違点は、<xref:System.Windows.UIElement> や <xref:System.Windows.ContentElement> がユーザー インターフェイスで使用される方法と、それらがアプリケーション内で使用される目的に関するものです。  <xref:System.Windows.UIElement> のクラス階層構造内には <xref:System.Windows.Media.Visual> も存在します。これは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] の基礎となる低レベルのグラフィックス サポートを公開するクラスです。  <xref:System.Windows.Media.Visual> は、独立した四角形の画面領域を定義することにより、レンダリングのフレームワークを提供します。  実際には、<xref:System.Windows.UIElement> は比較的大きなオブジェクト モデルをサポートし、四角形の画面領域として記述できる領域にレンダリングおよびレイアウトされるように設計されている要素のためのものです。そのコンテンツ モデルは、さまざまな要素の組み合わせが可能なように、意図的にオープンに作られています。  <xref:System.Windows.ContentElement> は <xref:System.Windows.Media.Visual> から派生していません。そのモデルでは、<xref:System.Windows.ContentElement> は、リーダーやビューアーなど、他のものによって処理されます。これらのリーダーやビューアーなどは、要素を解釈し、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] が処理する完全な <xref:System.Windows.Media.Visual> を生成します。  一部の <xref:System.Windows.UIElement> クラスは、コンテンツ ホストとなるように設計されています。それらのクラスは、1 つ以上の <xref:System.Windows.ContentElement> クラスに対して、ホスティングとレンダリングを提供します \(そのようなクラスの例として、<xref:System.Windows.Controls.DocumentViewer> があります\)。  <xref:System.Windows.ContentElement> は、比較的小さなオブジェクト モデルを持ち、<xref:System.Windows.UIElement> 内にホストされるテキスト、情報、またはドキュメントのコンテンツ向けに使用されることの多い要素の基本クラスとして使用されます。  
  
### フレームワークレベルとコアレベル  
 <xref:System.Windows.UIElement> は、<xref:System.Windows.FrameworkElement> の基本クラスとして使用され、<xref:System.Windows.ContentElement> は、<xref:System.Windows.FrameworkContentElement> の基本クラスとして使用されます。  この第 2 レベルのクラスが存在する理由は、[WPF フレームワーク レベル](GTMT)とは異なる [WPF コア レベル](GTMT)をサポートすることです。この区分は、PresentationCore と PresentationFramework アセンブリ間での [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] の区分にも存在します。  [WPF フレームワーク レベル](GTMT)は、表示のためのレイアウト マネージャーの実装など、アプリケーションの基本的ニーズに対して、より完全なソリューションを提供します。  [WPF コア レベル](GTMT)は、アセンブリの追加によるオーバーヘッドを引き起こすことなく [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の大部分を使用する方法を提供します。  これらのレベルの区別は、ほとんどの通常のアプリケーション開発シナリオでほとんど問題になりません。一般には、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] を 1 つのものと見なして、[WPF フレームワーク レベル](GTMT)と [WPF コア レベル](GTMT)の違いについて意識する必要はありません。  アプリケーション設計で [WPF フレームワーク レベル](GTMT)の機能の大部分を置き換えることにした場合、たとえば開発中のソリューション全体に、独自の [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] の構成およびレイアウトが既に実装されている場合には、これらのレベルの区分に関する理解が必要となる可能性があります。  
  
<a name="subclassing_elements"></a>   
## 派生元の要素を選択する  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] を拡張したカスタム クラスを作成するための最も実際的な方法は、既存のクラス階層から必要な機能を可能な限り得ることのできる、いずれかの [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] クラスから派生させることです。  このセクションでは、継承元とするクラスの選択に役立つように、最も重要な要素クラスのうちの 3 つのクラスが提供する機能を示します。  
  
 コントロールを実装する場合には \([!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] クラスから派生させる理由としてはこれが実際のところ最も一般的なものですが\)、実用的なコントロールであるクラス、コントロール ファミリの基本クラス、または少なくとも <xref:System.Windows.Controls.Control> 基本クラスから派生させるのが一般的です。  いくつかのガイドラインと実際の例については、「[コントロールの作成の概要](../../../../docs/framework/wpf/controls/control-authoring-overview.md)」を参照してください。  
  
 コントロールを作成しているのではなく、階層の上位にあるクラスから派生する必要がある場合は、各基本要素クラスに定義された特性に関するガイドを意図した、以下のセクションを参照してください。  
  
 <xref:System.Windows.DependencyObject> から派生するクラスを作成すると、次の機能が継承されます。  
  
-   <xref:System.Windows.DependencyObject.GetValue%2A> と <xref:System.Windows.DependencyObject.SetValue%2A> のサポート、およびプロパティ システム全体のサポート。  
  
-   [依存関係プロパティ](GTMT)と、[依存関係プロパティ](GTMT)として実装されている[添付プロパティ](GTMT)を使用する機能。  
  
 <xref:System.Windows.UIElement> から派生するクラスを作成する場合は、<xref:System.Windows.DependencyObject> によって提供される機能以外に、次の機能を継承します。  
  
-   アニメーション化されたプロパティ値の基本的なサポート。  詳細については、「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」を参照してください。  
  
-   基本的な入力イベントのサポートと、コマンド実行のサポート。  詳細については、「[入力の概要](../../../../docs/framework/wpf/advanced/input-overview.md)」および「[コマンド実行の概要](../../../../docs/framework/wpf/advanced/commanding-overview.md)」を参照してください。  
  
-   レイアウト システムに情報を提供するためにオーバーライドできる仮想メソッド。  
  
 <xref:System.Windows.FrameworkElement> から派生するクラスを作成する場合は、<xref:System.Windows.UIElement> によって提供される機能以外に、次の機能を継承します。  
  
-   スタイル設定とストーリーボードのサポート。  詳細については、「<xref:System.Windows.Style>」および「[ストーリーボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)」を参照してください。  
  
-   データ バインディングのサポート。  詳細については、「[データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)」を参照してください。  
  
-   動的リソース参照のサポート。  詳細については、「[XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)」を参照してください。  
  
-   プロパティ値継承のサポート、および、データ バインディング、スタイル、またはレイアウトのフレームワークの実装などのフレームワーク サービスのプロパティに関する条件をレポートする場合に役立つ、メタデータ内の他のフラグ。  詳細については、「[フレームワーク プロパティ メタデータ](../../../../docs/framework/wpf/advanced/framework-property-metadata.md)」を参照してください。  
  
-   [論理ツリー](GTMT)の概念。  詳細については、「[WPF のツリー](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)」を参照してください。  
  
-   レイアウトに影響を与えるプロパティの変更を検出できる <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> オーバーライドなど、レイアウト システムの実際的な [WPF フレームワーク レベル](GTMT)の実装のサポート。  
  
 <xref:System.Windows.ContentElement> から派生するクラスを作成する場合は、<xref:System.Windows.DependencyObject> によって提供される機能以外に、次の機能を継承します。  
  
-   アニメーションのサポート。  詳細については、「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」を参照してください。  
  
-   基本的な入力イベントのサポートと、コマンド実行のサポート。  詳細については、「[入力の概要](../../../../docs/framework/wpf/advanced/input-overview.md)」および「[コマンド実行の概要](../../../../docs/framework/wpf/advanced/commanding-overview.md)」を参照してください。  
  
 <xref:System.Windows.FrameworkContentElement> から派生するクラスを作成する場合は、<xref:System.Windows.ContentElement> によって提供される機能以外に、次の機能を使用できます。  
  
-   スタイル設定とストーリーボードのサポート。  詳細については、「<xref:System.Windows.Style>」および「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」を参照してください。  
  
-   データ バインディングのサポート。  詳細については、「[データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)」を参照してください。  
  
-   動的リソース参照のサポート。  詳細については、「[XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)」を参照してください。  
  
-   プロパティ値継承のサポート、および、データ バインディング、スタイル、またはレイアウトのフレームワークの実装などのフレームワーク サービスのプロパティに関する条件をレポートする場合に役立つ、メタデータ内の他のフラグ。  詳細については、「[フレームワーク プロパティ メタデータ](../../../../docs/framework/wpf/advanced/framework-property-metadata.md)」を参照してください。  
  
-   レイアウト システムの変更 \(たとえば <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>\) へのアクセスは継承されません。  レイアウト システムの実装は、<xref:System.Windows.FrameworkElement> でのみ利用できます。  ただし、レイアウトに影響を与えるプロパティの変更を検出し、それらの変更を任意のコンテンツ ホストに報告できる <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> オーバーライドは継承されます。  
  
 さまざまなクラスに関してコンテンツ モデルが文書化されています。  派生元として適切なクラスを見つける必要がある場合、クラスのコンテンツ モデルは、考慮する必要がある項目の候補の 1 つです。  詳細については、「[WPF のコンテンツ モデル](../../../../docs/framework/wpf/controls/wpf-content-model.md)」を参照してください。  
  
<a name="other_base_classes"></a>   
## 他の基本クラス  
  
### DispatcherObject  
 <xref:System.Windows.Threading.DispatcherObject> は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] スレッド処理モデルのサポートを提供し、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションのために作成されたすべてのオブジェクトが <xref:System.Windows.Threading.Dispatcher> に関連付けられるようにします。  <xref:System.Windows.UIElement>、<xref:System.Windows.DependencyObject>、または <xref:System.Windows.Media.Visual> から派生しない場合でも、このスレッド処理モデルのサポートを可能にするために <xref:System.Windows.Threading.DispatcherObject> から派生することを検討してください。  詳細については、「[スレッド モデル](../../../../docs/framework/wpf/advanced/threading-model.md)」を参照してください。  
  
### Visual  
 <xref:System.Windows.Media.Visual> は、四角形に近い表示形式を必要とする 2D オブジェクトの概念を実装します。  <xref:System.Windows.Media.Visual> の実際の描画は他のクラスで行われます \(単一のクラスですべての操作が完結しません\) が、<xref:System.Windows.Media.Visual> クラスは、描画プロセスのさまざまなレベルで使用される既知の型を提供します。  <xref:System.Windows.Media.Visual> はヒット テストを実装しますが、ヒット テストの結果を報告するイベントは公開しません \(このイベントは <xref:System.Windows.UIElement> にあります\)。  詳細については、「[ビジュアル層のプログラミング](../../../../docs/framework/wpf/graphics-multimedia/visual-layer-programming.md)」を参照してください。  
  
### Freezable  
 <xref:System.Windows.Freezable> は、変更できないオブジェクトが必要なときやパフォーマンス上の理由で望ましいときにオブジェクトのコピーを生成する手段を提供することにより、変更できるオブジェクト上で不変性をシミュレートします。  <xref:System.Windows.Freezable> 型は、ジオメトリ、ブラシ、アニメーションなどの特定のグラフィックス要素に使用できる共通の基盤です。  <xref:System.Windows.Freezable> は <xref:System.Windows.Media.Visual> ではありません。これには、別のオブジェクトのプロパティ値を設定するために <xref:System.Windows.Freezable> が適用されるときにサブプロパティとなるプロパティを格納できます。これらのサブプロパティは、描画に影響することがあります。  詳細については、「[Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)」を参照してください。  
  
 <xref:System.Windows.Media.Animation.Animatable>  
  
 <xref:System.Windows.Media.Animation.Animatable> は、<xref:System.Windows.Freezable> 派生クラスであり、このクラスによってアニメーション コントロール層とユーティリティ メンバーが追加され、現在のアニメーション プロパティを非アニメーション プロパティから区別できるようになります。  
  
### Control  
 <xref:System.Windows.Controls.Control> は、あるテクノロジではコントロールと呼ばれ、別のテクノロジではコンポーネントと呼ばれる種類のオブジェクトの基本クラスとして意図されています。  一般に [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロール クラスは、UI コントロールを直接表すクラスか、コントロールの複合に密接に参加するクラスです。  <xref:System.Windows.Controls.Control> が主に提供する機能は、コントロールのテンプレート作成です。  
  
## 参照  
 <xref:System.Windows.Controls.Control>   
 [依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [コントロールの作成の概要](../../../../docs/framework/wpf/controls/control-authoring-overview.md)   
 [WPF アーキテクチャ](../../../../docs/framework/wpf/advanced/wpf-architecture.md)