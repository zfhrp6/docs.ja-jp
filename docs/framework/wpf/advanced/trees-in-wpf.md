---
title: "WPF のツリー | Microsoft Docs"
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
  - "要素ツリー"
  - "論理ツリー"
  - "ビジュアル ツリー"
ms.assetid: e83f25e5-d66b-4fc7-92d2-50130c9a6649
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# WPF のツリー
多くのテクノロジでは、要素およびコンポーネントはツリー構造で編成され、開発者はこのツリー内のオブジェクト ノードを直接操作してアプリケーションのレンダリングまたは動作に影響を与えます。  [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] でも各種のツリー構造というメタファを使用してプログラム要素間のリレーションシップを定義します。  ほとんどの場合、WPF 開発者は、オブジェクト ツリー メタファについて概念的に考えながらアプリケーションをコードで作成したりアプリケーションの一部を XAML で定義したりすることができますが、そのためには、XML DOM で使用するような一般的なオブジェクト ツリー操作 API ではなく特定の API を呼び出したり特定のマークアップを使用したりします。  WPF では、ツリー メタファ ビューを提供する <xref:System.Windows.LogicalTreeHelper> と <xref:System.Windows.Media.VisualTreeHelper> の 2 つのヘルパー クラスを公開しています。  ビジュアル ツリーおよび論理ツリーという用語も WPF のドキュメントで使用されます。これらの同じツリーは、特定の主要な WPF 機能の動作を理解するうえで役立つためです。  ここでは、ビジュアル ツリーおよび論理ツリーが表す項目を定義し、これらのツリーがオブジェクト ツリーの全体的な概念とどのように関連するかについて説明し、<xref:System.Windows.LogicalTreeHelper> および <xref:System.Windows.Media.VisualTreeHelper> について説明します。  
  
   
  
<a name="element_tree"></a>   
## WPF のツリー  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の最も完全なツリー構造はオブジェクト ツリーです。  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] でアプリケーション ページを定義し、その [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を読み込むと、マークアップ内の要素の入れ子のリレーションシップに基づいてツリー構造が作成されます。  コードでアプリケーションまたはアプリケーションの一部を定義した場合、ツリー構造は、指定したオブジェクトのコンテンツ モデルを実装するプロパティにプロパティ値を割り当てる方法に基づいて作成されます。  [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] には、完全なオブジェクト ツリーを概念化し、パブリック API にレポートできるようにする方法として、論理ツリーとビジュアル ツリーの 2 つが用意されています。  論理ツリーとビジュアル ツリーの違いは必ずしも重要とは限りませんが、特定の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] サブシステムでは問題が生じることがあり、マークアップやコード内での選択に影響することがあります。  
  
 論理ツリーやビジュアル ツリーを直接操作するとは限らない場合でも、ツリーの操作方法の概念を理解することは、WPF をテクノロジとして理解するうえで役立ちます。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] でのプロパティの継承やイベント ルーティングを理解するためには、WPF をある種のツリー メタファとして考えることも重要です。  
  
> [!NOTE]
>  オブジェクト ツリーは実際の API というよりは概念なので、この概念について考える別の方法としてオブジェクト グラフがあります。  実際には、ツリー メタファが分割される実行時のオブジェクト間にリレーションシップがあります。  ただし、特に XAML で定義された UI では、ツリー メタファは十分に関連性があるため、ほとんどの WPF のドキュメントではこの一般的な概念を指す場合にオブジェクト ツリーという用語が使用されます。  
  
<a name="logical_tree"></a>   
## 論理ツリー  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、要素を支援するオブジェクトのプロパティを設定することで UI 要素にコンテンツを追加します。  たとえば、<xref:System.Windows.Controls.ListBox> コントロールに項目を追加するには、<xref:System.Windows.Controls.ItemsControl.Items%2A> プロパティを操作します。  これにより、<xref:System.Windows.Controls.ItemsControl.Items%2A> プロパティの値である <xref:System.Windows.Controls.ItemCollection> に項目を配置することになります。  同様に、<xref:System.Windows.Controls.DockPanel> にオブジェクトを追加するには、<xref:System.Windows.Controls.Panel.Children%2A> プロパティ値を操作します。  この場合は、<xref:System.Windows.Controls.UIElementCollection> にオブジェクトを追加することになります。  コード例については、「[Add an Element Dynamically](http://msdn.microsoft.com/ja-jp/d00f258a-7973-4de7-bc54-a3fc1f638419)」を参照してください。  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] では、次の例に示すように、<xref:System.Windows.Controls.ListBox> にリスト項目を配置する場合、あるいは <xref:System.Windows.Controls.DockPanel> にコントロールまたは他の UI 要素を配置する場合は、<xref:System.Windows.Controls.ItemsControl.Items%2A> プロパティと <xref:System.Windows.Controls.Panel.Children%2A> プロパティも明示的または暗黙的に使用します。  
  
 [!code-xml[TreeOvwsSupport#AllCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeOvwsSupport/CS/page1.xaml#allcode)]  
  
 この XAML を XML としてドキュメント オブジェクト モデルで処理する場合、"implicit" としてコメント アウトされているタグを含めたとすると \(これも有効な形式です\)、結果として得られる XML DOM ツリーには、`<ListBox.Items>` および他の暗黙的な項目に対応する要素が含まれると予想されます。  しかし、マークアップを読み込んでオブジェクトに出力する時点では、XAML はそのようには処理されず、結果のオブジェクト グラフには指定したとおりの `ListBox.Items` は含まれません。  ただし、<xref:System.Windows.Controls.ItemCollection> を格納する `Items` という名前の <xref:System.Windows.Controls.ListBox> プロパティは含まれます。その <xref:System.Windows.Controls.ItemCollection> は、<xref:System.Windows.Controls.ListBox> の XAML の処理時に初期化されますが空です。  その後、パーサーによる `ItemCollection.Add` の呼び出しによって、<xref:System.Windows.Controls.ListBox> のコンテンツとして存在する各子オブジェクト要素が <xref:System.Windows.Controls.ItemCollection> に追加されます。  このオブジェクト ツリーへの XAML の処理例は、これまでのところ、作成されたオブジェクト ツリーが基本的に論理ツリーである例のように見えます。  
  
 ただし、論理ツリーは、XAML の暗黙的な構文項目が除外されている場合でも、実行時のアプリケーション UI に対して存在するオブジェクト グラフ全体ではありません。  この主な理由は、ビジュアルとテンプレートです。  たとえば <xref:System.Windows.Controls.Button> について考えます。  論理ツリーでは、<xref:System.Windows.Controls.Button> オブジェクトがレポートされ、文字列 `Content` もレポートされます。  ただし、ランタイム オブジェクト ツリーにはこのボタン以上のものが表示されます。  特に、特定の <xref:System.Windows.Controls.Button> コントロール テンプレートが適用されたので、ボタンは画面上にその状態でのみ表示されます。  実行時に論理ツリーを参照している場合でも \(表示される UI からの入力イベントを処理して論理ツリーを読み取るなど\)、適用されたテンプレートから取得されたビジュアル \(ビジュアル ボタンを囲むテンプレートで定義された濃い灰色の <xref:System.Windows.Controls.Border> など\) は論理ツリーではレポートされません。  テンプレートのビジュアルを確認するには、ビジュアル ツリーを調べる必要があります。  
  
 作成されるオブジェクト グラフおよび XAML の暗黙的な構文に [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 構文が対応付けられる方法の詳細については、「[XAML 構文の詳細](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)」または「[XAML の概要 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)」を参照してください。  
  
<a name="tree_property_inheritance_event_routing"></a>   
### 論理ツリーの目的  
 論理ツリーは、コンテンツ モデルが、使用可能な子オブジェクトを簡単に反復処理できること、およびコンテンツ モデルの拡張を目的としています。  論理ツリーは、論理ツリー内のすべてのオブジェクトがいつ読み込まれるかなど、特定の通知のフレームワークも提供します。  基本的に、論理ツリーは、ビジュアルを除外したフレームワーク レベルではランタイム オブジェクト グラフに近いと言えますが、独自のランタイム アプリケーションのコンポジションに対する多くのクエリ操作では論理ツリーで十分です。  
  
 また、静的リソース参照と動的リソース参照はどちらも、最初は要求元のオブジェクト、次は論理ツリーの上方で <xref:System.Windows.FrameworkElement.Resources%2A> コレクションの論理ツリーを介した上方への検索を行って、<xref:System.Windows.ResourceDictionary> を格納し、場合によってはそのキーを格納する別の `Resources` 値の各 <xref:System.Windows.FrameworkElement> \(または <xref:System.Windows.FrameworkContentElement>\) をチェックすることによって解決されます。  論理ツリーとビジュアル ツリーの両方が存在する場合は、論理ツリーがリソースの検索に使用されます。  リソース ディクショナリおよび検索の詳細については、「[XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)」を参照してください。  
  
<a name="composition"></a>   
### 論理ツリーのコンポジション  
 論理ツリーは、[WPF フレームワーク レベル](GTMT)で定義されます。つまり、論理ツリーの操作に最も関連する WPF 基本要素は <xref:System.Windows.FrameworkElement> または <xref:System.Windows.FrameworkContentElement> です。  ただし、実際に <xref:System.Windows.LogicalTreeHelper> API を使用するとわかるように、論理ツリーには <xref:System.Windows.FrameworkElement> でも <xref:System.Windows.FrameworkContentElement> でもないノードが含まれる場合があります。  たとえば、論理ツリーでは、文字列である <xref:System.Windows.Controls.TextBlock> の <xref:System.Windows.Controls.TextBlock.Text%2A> 値がレポートされます。  
  
<a name="override_logical_tree"></a>   
### 論理ツリーのオーバーライド  
 高度なコントロールを作成するときには、論理ツリーをオーバーライドできます。そのためには、一般的なオブジェクトやコンテンツ モデルで論理ツリー内のオブジェクトを追加または削除する方法を定義している、いくつかの [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] をオーバーライドします。  論理ツリーのオーバーライド例については、「[論理ツリーをオーバーライドする](../../../../docs/framework/wpf/advanced/how-to-override-the-logical-tree.md)」を参照してください。  
  
<a name="pvi"></a>   
### プロパティ値の継承  
 プロパティ値の継承は、ハイブリッド ツリーを通じて行われます。  プロパティの継承を有効化する <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> プロパティが含まれる実際のメタデータは、[WPF フレームワーク レベル](GTMT)の <xref:System.Windows.FrameworkPropertyMetadata> クラスです。  このため、元の値を保持する親とその値を継承する子オブジェクトの両方が <xref:System.Windows.FrameworkElement> または <xref:System.Windows.FrameworkContentElement> であり、両方が、ある論理ツリーに含まれている必要があります。  ただし、プロパティの継承をサポートする既存の WPF プロパティでは、プロパティ値の継承は、論理ツリーにない、介在するオブジェクトを通じて存続できます。  これは主に、template 宣言されたインスタンスまたはさらに上位レベルのページ レベル コンポジション \(論理ツリー内の上位\) で設定されている継承されたプロパティ値をテンプレート要素で使用することに関連します。  プロパティ値の継承が、このような境界を越えて変わらず動作するためには、継承するプロパティを添付プロパティとして登録する必要があります。また、プロパティの継承動作を使用してカスタム依存関係プロパティを定義する場合は、このパターンに従う必要があります。  プロパティの継承で使用する正確なツリーを、実行時であっても、ヘルパー クラス ユーティリティ メソッドで完全に予測することができません。  詳細については、「[プロパティ値の継承](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)」を参照してください。  
  
<a name="two_trees"></a>   
## ビジュアル ツリー  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、論理ツリーの概念に加えて、[ビジュアル ツリー](GTMT)の概念も存在します。  ビジュアル ツリーは、<xref:System.Windows.Media.Visual> 基本クラスによって表されるビジュアル オブジェクトの構造を示します。  コントロールのテンプレートを作成する場合は、そのコントロールに適用するビジュアル ツリーを定義または再定義します。  ビジュアル ツリーは、パフォーマンスの向上および最適化のために、描画に対して低レベルの制御が必要な開発者にとっても非常に有用です。  従来の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションのプログラミングの一環としてビジュアル ツリーについて公開されていることの 1 つは、[ルーティング イベント](GTMT)のイベント ルートは、通常、論理ツリーではなくビジュアル ツリーをたどるということです。  ルーティング イベントの動作の細部は、コントロールの作成者でない限り、すぐにはわからない場合があります。  ビジュアル ツリーを介したルーティング イベントにより、ビジュアルのレベルで構成を実装するコントロールによってイベントを処理したり、イベント setter を作成したりできるようになります。  
  
<a name="trees_content"></a>   
## ツリー、コンテンツ要素、およびコンテンツ ホスト  
 コンテンツ要素 \(<xref:System.Windows.ContentElement> から派生するクラス\) はビジュアル ツリーには含まれません。これらは <xref:System.Windows.Media.Visual> を継承しておらず、視覚的表現を持ちません。  UI に表示するには、<xref:System.Windows.Media.Visual> であり、論理ツリーの参加要素でもあるコンテンツ ホスト内で、<xref:System.Windows.ContentElement> をホストする必要があります。  通常、このようなオブジェクトは <xref:System.Windows.FrameworkElement> です。  コンテンツ ホストは、コンテンツにとって "ブラウザー" のようなものであり、ホストが制御する画面領域内でそのコンテンツの表示方法を選択するものと考えることができます。  コンテンツがホストされると、このコンテンツは、ビジュアル ツリーに通常関連付けられている特定のツリー プロセスで 1 つの要因になることができます。  一般に、<xref:System.Windows.FrameworkElement> ホスト クラスには、ホストされるコンテンツが実際にはビジュアル ツリーに含まれない場合でも、コンテンツの論理ツリーのサブノードを介して、ホストされる <xref:System.Windows.ContentElement> をイベント ルートに追加する実装コードが含まれます。  これは、<xref:System.Windows.ContentElement> が、自身以外の要素にルーティングするルーティング イベントを調達できるようにするために必要です。  
  
<a name="tree_traversal"></a>   
## ツリーの走査  
 <xref:System.Windows.LogicalTreeHelper> クラスには、論理ツリーの走査用に <xref:System.Windows.LogicalTreeHelper.GetChildren%2A>、<xref:System.Windows.LogicalTreeHelper.GetParent%2A>、および <xref:System.Windows.LogicalTreeHelper.FindLogicalNode%2A> の各メソッドが用意されています。  これらのコントロールはほとんど常に論理上の子要素を専用のコレクション プロパティとして公開し、`Add`、インデクサーなどのコレクション アクセスをサポートしているため、多くの場合、既存のコントロールの論理ツリーを移動する必要はありません。  ツリーの移動が使用される主なシナリオは、コントロール作成者が、コレクション プロパティが定義済みの <xref:System.Windows.Controls.ItemsControl> や <xref:System.Windows.Controls.Panel> など、対象とするコントロール パターンから派生することを選択しない場合や、コレクション プロパティを独自にサポートする場合です。  
  
 ビジュアル ツリーも、ビジュアル ツリーの走査に使用できるヘルパー クラス <xref:System.Windows.Media.VisualTreeHelper> をサポートしています。  ビジュアル ツリーでは、コントロール固有のプロパティを使用した便利な移動方法は公開されていないため、プログラミング シナリオで必要な場合には、ビジュアル ツリーを移動する方法として <xref:System.Windows.Media.VisualTreeHelper> クラスが推奨されます。  詳細については、「[WPF グラフィックス レンダリングの概要](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)」を参照してください。  
  
> [!NOTE]
>  場合によっては、適用されたテンプレートのビジュアル ツリーを調べる必要が生じることがあります。  この方法を使用するときには注意が必要です。  テンプレートを定義するコントロールのビジュアル ツリーを走査する場合でも、コントロールのコンシューマーは、インスタンスで <xref:System.Windows.Controls.Control.Template%2A> プロパティを設定することで常にテンプレートを変更でき、エンド ユーザーでさえシステム テーマを変更することで適用されたテンプレートに影響を与えることができます。  
  
<a name="routes"></a>   
## "ツリー" としてのルーティング イベントのルート  
 前述のように、特定のルーティング イベントのルートは、ビジュアル ツリーと論理ツリーの表現を組み合わせたツリーの単一の定義済みパスをたどります。  イベント ルートは、トンネル ルーティング イベントかバブル ルーティング イベントかに応じて、ツリーを上方向または下方向へ移動できます。  イベント ルートの概念では、実際にルーティングするイベントの発生とは無関係にイベント ルートを "移動する" のに使用される、ヘルパー クラスを直接にはサポートしていません。  ルートを表す <xref:System.Windows.EventRoute> クラスはありますが、そのクラスのメソッドは、通常、内部でのみ使用されています。  
  
<a name="resourcesandtrees"></a>   
## リソース ディクショナリとツリー  
 ページで定義されているすべての `Resources` に対するリソース ディクショナリ検索では、基本的に、論理ツリーが走査されます。  論理ツリーにないオブジェクトもキーを持つリソースを参照できますが、リソース検索シーケンスは、そのオブジェクトが論理ツリーに接続している場所から開始されます。  WPF では、論理ツリー ノードのみが <xref:System.Windows.ResourceDictionary> を含む `Resources` プロパティを使用できるため、<xref:System.Windows.ResourceDictionary> からのキーを持つリソースの検索時にビジュアル ツリーを走査しても利点はありません。  
  
 ただし、リソース検索も、直接の論理ツリーを超えて拡張できます。  アプリケーション マークアップの場合、アプリケーション レベルのリソース ディクショナリ、テーマ サポート、および静的プロパティまたはキーとして参照されるシステム値へとリソース検索が続きます。  リソース参照が動的な場合は、テーマ自体も、テーマ論理ツリーの外部にあるシステム値を参照できます。  リソース ディクショナリおよび検索ロジックの詳細については、「[XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)」を参照してください。  
  
## 参照  
 [入力の概要](../../../../docs/framework/wpf/advanced/input-overview.md)   
 [WPF グラフィックス レンダリングの概要](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)   
 [ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)   
 [オブジェクト ツリーに存在しないオブジェクト要素の初期化](../../../../docs/framework/wpf/advanced/initialization-for-object-elements-not-in-an-object-tree.md)   
 [WPF アーキテクチャ](../../../../docs/framework/wpf/advanced/wpf-architecture.md)