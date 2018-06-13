---
title: WPF のツリー
ms.date: 03/30/2017
helpviewer_keywords:
- logical tree [WPF]
- element tree [WPF]
- visual tree [WPF]
ms.assetid: e83f25e5-d66b-4fc7-92d2-50130c9a6649
ms.openlocfilehash: e7695fa94a7742d474cb998ff26a5cf009cdb6eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549073"
---
# <a name="trees-in-wpf"></a>WPF のツリー
多くのテクノロジ要素とコンポーネントは、開発者が直接レンダリングやアプリケーションの動作に影響を与えるツリー内のオブジェクト ノードを操作をツリー構造に編成されています。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] プログラム要素間のリレーションシップを定義するのにいくつかのツリー構造体要素を使用します。 WPF の開発者の大部分できますコードでアプリケーションを作成またはオブジェクト ツリーの比喩、概念的には検討中に XAML で、アプリケーションの部分を定義するが、特定の API を呼び出すか、いくつかの一般的なのではなく、そのために特定のマークアップを使用します。XML DOM で使用するなどのオブジェクト ツリー操作 API WPF は、ツリーの比喩ビューを提供する 2 つのヘルパー クラスを公開<xref:System.Windows.LogicalTreeHelper>と<xref:System.Windows.Media.VisualTreeHelper>です。 用語のビジュアル ツリーおよび論理ツリーも使われます、WPF ドキュメントのため、これらの同じツリーが特定のキーの WPF 機能の動作を理解するのに便利です。 このトピックは、ビジュアル ツリーおよび論理ツリーを表す新機能を定義し、このようなツリーが、全体的なオブジェクトのツリーの概念に関連する方法について説明しますが導入されています<xref:System.Windows.LogicalTreeHelper>と<xref:System.Windows.Media.VisualTreeHelper>s。  
  

  
<a name="element_tree"></a>   
## <a name="trees-in-wpf"></a>WPF のツリー  
 最も包括的なツリー構造[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]オブジェクト ツリーです。 アプリケーション ページを定義する場合[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]し、ロード、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップ内の要素の入れ子のリレーションシップに基づいてツリー構造が作成されます。 アプリケーションを定義するか、コードでは、アプリケーション、ツリー構造の一部が作成された場合は、特定のオブジェクトのコンテンツ モデルを実装するプロパティのプロパティ値を割り当てる方法に基づいています。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]、完全なオブジェクト ツリーを概念化し、パブリック API に報告できる 2 つの方法がある: ビジュアル ツリーおよび論理ツリーとして。 論理ツリーとビジュアル ツリーの違いは、必ずしも必ずしも重要が特定の問題が発生することができる場合によっては、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]サブシステムとマークアップやコードで選択したに影響します。  
  
 いない常に、論理ツリーまたはビジュアル ツリーを直接操作する場合でも、ツリーの操作方法の概念を理解するはテクノロジとして WPF を理解するために役立ちます。 WPF ツリーの比喩、ある種が非常に重要のプロパティの継承とイベントのルーティングのしくみを理解することにもとして見なすこと[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]です。  
  
> [!NOTE]
>  オブジェクト ツリーは、実際の API の概念の詳細であるため、オブジェクト グラフは概念について考えるを別の方法です。 実際には、リレーションシップの間はツリーの比喩が分割が実行時のオブジェクトです。 ただし、特に XAML で定義された UI を備えた、ツリーの比喩は関連この一般的な概念を参照するときに、ほとんどの WPF のドキュメントがオブジェクト ツリーのという用語を使用します。  
  
<a name="logical_tree"></a>   
## <a name="the-logical-tree"></a>論理ツリー  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]をそれらの要素を格納するオブジェクトのプロパティを設定して、UI 要素にコンテンツを追加します。 項目を追加するなど、<xref:System.Windows.Controls.ListBox>コントロールを操作することでその<xref:System.Windows.Controls.ItemsControl.Items%2A>プロパティです。 これによりにアイテムを配置する、<xref:System.Windows.Controls.ItemCollection>されている、<xref:System.Windows.Controls.ItemsControl.Items%2A>プロパティの値。 同様に、追加するオブジェクトを<xref:System.Windows.Controls.DockPanel>を操作することでその<xref:System.Windows.Controls.Panel.Children%2A>プロパティの値。 ここでは、オブジェクトを追加する、<xref:System.Windows.Controls.UIElementCollection>です。 コード例は、次を参照してください。 [、要素を動的に追加](http://msdn.microsoft.com/library/d00f258a-7973-4de7-bc54-a3fc1f638419)です。  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]でリスト項目を配置するとき、<xref:System.Windows.Controls.ListBox>コントロールまたはその他の UI 要素で、 <xref:System.Windows.Controls.DockPanel>、使用することも、<xref:System.Windows.Controls.ItemsControl.Items%2A>と<xref:System.Windows.Controls.Panel.Children%2A>プロパティ、明示的または暗黙的に、次の例のようにです。  
  
 [!code-xaml[TreeOvwsSupport#AllCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeOvwsSupport/CS/page1.xaml#allcode)]  
  
 かどうかとして XML ドキュメント オブジェクト モデルでは、次の XAML を処理するコメント タグが含まれていたかどうか、アウト暗黙的な (これが有効な)、結果の XML DOM ツリーに要素が含まれますが、`<ListBox.Items>`およびその他の暗黙的な項目です。 XAML を処理しないようにして、マークアップを読み取るし、オブジェクトを書き込むときに、生成されたオブジェクト グラフには文字どおりは含まれませんが、`ListBox.Items`です。 ただしが、<xref:System.Windows.Controls.ListBox>という名前のプロパティ`Items`を格納している、 <xref:System.Windows.Controls.ItemCollection>、および<xref:System.Windows.Controls.ItemCollection>は初期化されますが、空のときに、 <xref:System.Windows.Controls.ListBox> XAML を処理します。 次に、各子オブジェクト要素のコンテンツとして存在する、<xref:System.Windows.Controls.ListBox>に追加、<xref:System.Windows.Controls.ItemCollection>パーサーの呼び出しで`ItemCollection.Add`です。 オブジェクト ツリーに XAML の処理には、この例はこれまで一見例で作成されたオブジェクト ツリーは、基本的に論理ツリーです。  
  
 ただし、論理ツリーは、オブジェクト グラフ全体の XAML の暗黙的な構文項目を使用しても、実行時に UI が除外されているアプリケーションが存在するではありません。主な理由は、ビジュアルとテンプレート。 たとえば、<xref:System.Windows.Controls.Button>です。 論理ツリーのレポート、<xref:System.Windows.Controls.Button>オブジェクトともその文字列`Content`です。 実行時のオブジェクト ツリーで、このボタンに詳細があります。 具体的には、ボタンのみ画面に表示されますがあるため、特定<xref:System.Windows.Controls.Button>コントロール テンプレートを適用します。 テンプレートを適用したに由来するビジュアル (テンプレートで定義されたなど<xref:System.Windows.Controls.Border>ビジュアル ボタンを囲む濃い灰色の) 場合でも、実行時に、論理ツリーを見ることが、論理ツリーには報告されません (からの入力イベントの処理など、表示される UI および論理ツリーを読み取り)。 テンプレートのビジュアルを検索するには、代わりに、ビジュアル ツリーを検査する必要なります。  
  
 方法の詳細についての[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、作成されたオブジェクト グラフと XAML では、暗黙的な構文に構文のマップを参照してください[XAML 構文の詳細](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)または[XAML の概要 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)です。  
  
<a name="tree_property_inheritance_event_routing"></a>   
### <a name="the-purpose-of-the-logical-tree"></a>論理ツリーの目的は、  
 論理ツリーには、コンテンツ モデルは、それらの使用可能な子オブジェクトを簡単に反復処理できますのでこと、およびコンテンツ モデルの拡張が存在しています。 また、論理ツリー フレームワークを提供、特定の論理ツリー内のすべてのオブジェクトが読み込まれるときになど、通知します。 基本的には、論理ツリーには、フレームワーク レベルで、ビジュアルは含まれませんが、独自の実行時のアプリケーションの合成に対する多くのクエリ処理の適切な実行時のオブジェクト グラフの近似値です。  
  
 論理ツリーを上へ検索で両方の静的および動的リソース参照を解決するさらに、<xref:System.Windows.FrameworkElement.Resources%2A>のコレクションに、初期要求側のオブジェクト、および論理ツリーを続行し、各<xref:System.Windows.FrameworkElement>(または<xref:System.Windows.FrameworkContentElement>)別の`Resources`値を含む、 <xref:System.Windows.ResourceDictionary>、そのキーを含む可能性があります。 論理ツリーとビジュアル ツリーの両方が存在する場合は、論理ツリーをリソースの検索に使用されます。 リソース ディクショナリと照合の詳細については、次を参照してください。 [XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)です。  
  
<a name="composition"></a>   
### <a name="composition-of-the-logical-tree"></a>論理ツリーの合成  
 論理ツリーが、WPF フレームワーク レベル、つまり論理ツリーの操作に最も関連性は、WPF の基本要素はいずれかで定義されている<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>です。 ただし、することができますを参照してくださいかどうかは実際に使用する、 <xref:System.Windows.LogicalTreeHelper> API、論理ツリー場合もありますノードが含まれていないか<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>です。 論理ツリーのインスタンスのレポート、<xref:System.Windows.Controls.TextBlock.Text%2A>の値、 <xref:System.Windows.Controls.TextBlock>、された文字列します。  
  
<a name="override_logical_tree"></a>   
### <a name="overriding-the-logical-tree"></a>論理ツリーのオーバーライド  
 高度なコントロールの作成者がいくつかの操作をオーバーライドすることで、論理ツリーをオーバーライドできます[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]一般的なオブジェクトまたはコンテンツ モデルが追加または論理ツリー内のオブジェクトを削除する方法を定義します。 論理ツリーをオーバーライドする方法の例は、次を参照してください。[論理ツリーをオーバーライドする](../../../../docs/framework/wpf/advanced/how-to-override-the-logical-tree.md)です。  
  
<a name="pvi"></a>   
### <a name="property-value-inheritance"></a>プロパティ値の継承  
 プロパティ値の継承は、ハイブリッド ツリーを通じて動作します。 実際のメタデータを含む、<xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>プロパティをプロパティの継承を有効にするには、WPF フレームワーク レベル<xref:System.Windows.FrameworkPropertyMetadata>クラスです。 したがって、元の値を保持する親とその値を継承する子オブジェクトの両方両方あります<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>、それら両方を指定する必要な論理ツリーの一部とします。 ただし、プロパティの継承をサポートする既存の WPF プロパティ、プロパティ値の継承が論理ツリーに含まれていない間にあるオブジェクトを永続化することです。 主にですが、テンプレート化されているインスタンスのいずれかに設定されている継承されたプロパティ値を使用して要素がテンプレートまたはページ レベルの構成のさらに高いレベルで論理ツリー内の上位。 このような境界を越えて一貫して動作するプロパティ値の継承の順番は、継承したプロパティは、添付プロパティとして登録する必要があり。、プロパティを使用してカスタムの依存関係プロパティを定義する場合、このパターンに従う必要があります。継承の動作です。 正確なツリー プロパティの継承を使用することはできませんで完全に予測ヘルパー クラスのユーティリティ メソッドの実行時にもします。 詳細については、「[プロパティ値の継承](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)」を参照してください。  
  
<a name="two_trees"></a>   
## <a name="the-visual-tree"></a>ビジュアル ツリー  
 論理ツリーの概念、に加えてものビジュアル ツリーの概念[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]です。 によって表されるように、ビジュアル ツリーが、ビジュアル オブジェクトの構造を記述、<xref:System.Windows.Media.Visual>基本クラスです。 コントロール用のテンプレートを記述するときにを定義するか、そのコントロールに適用するビジュアル ツリーを再定義ができます。 ビジュアル ツリーは、下位のパフォーマンスおよび最適化のための描画を制御したい開発者を対象もです。 ビジュアル ツリーを従来の一部としての 1 つの露出[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ルーティング イベントのイベントのルートが、論理ツリーではなく、ビジュアル ツリーに沿って出張ほとんどの場合は、アプリケーション プログラミングします。 コントロールの作成者でない限り、ルーティングされたイベントの動作の細部がすぐにわかりますできない可能性があります。 ビジュアル ツリーを使用してイベントのルーティング イベントを処理したり、イベント セッターを作成するビジュアルのレベルで構成を実装するコントロールを使用します。  
  
<a name="trees_content"></a>   
## <a name="trees-content-elements-and-content-hosts"></a>ツリーのコンテンツ要素、およびコンテンツ ホスト  
 コンテンツ要素 (から派生したクラス<xref:System.Windows.ContentElement>) のビジュアル ツリーの一部ではない; から継承しない<xref:System.Windows.Media.Visual>視覚的に表現はありません。 すべての UI に表示するために、<xref:System.Windows.ContentElement>をコンテンツ ホストでホストされる必要があります、<xref:System.Windows.Media.Visual>および論理ツリーの参加要素。 このようなオブジェクトは、通常、<xref:System.Windows.FrameworkElement>です。 コンテンツ ホストは、コンテンツが、"browser"のようなものと、ホストを制御する画面領域内でそのコンテンツを表示する方法を選択を考えることができます。 コンテンツがホストされている場合、コンテンツは通常、ビジュアル ツリーに関連付けられている特定のツリー プロセス内の参加者作成できます。 一般に、<xref:System.Windows.FrameworkElement>ホスト クラスには、いずれかのホストを追加する実装コードが含まれています。<xref:System.Windows.ContentElement>コンテンツの論理ツリーのサブノードを介してイベント ルートにいなくてもホストするコンテンツが true のビジュアル ツリーの一部です。 これは、必要なできるように、<xref:System.Windows.ContentElement>自体以外の任意の要素にルーティングするルーティング イベントを送信できます。  
  
<a name="tree_traversal"></a>   
## <a name="tree-traversal"></a>ツリーの移動  
 <xref:System.Windows.LogicalTreeHelper>クラスを提供、 <xref:System.Windows.LogicalTreeHelper.GetChildren%2A>、 <xref:System.Windows.LogicalTreeHelper.GetParent%2A>、および<xref:System.Windows.LogicalTreeHelper.FindLogicalNode%2A>の論理ツリーの移動メソッドです。 ほとんどの場合、する必要はありません、既存のコントロールの論理ツリーを走査するため、ほとんどの場合、これらのコントロールはなど、コレクションへのアクセスをサポートする専用のコレクション プロパティとして、論理上の子要素を公開`Add`インデクサー、などなど。 ツリーの移動は主のシナリオなどの目的のコントロール パターンから派生しないように選択コントロールの作成者によって使用される<xref:System.Windows.Controls.ItemsControl>または<xref:System.Windows.Controls.Panel>コレクションのプロパティが既に定義されている、および、独自のコレクションを使用するユーザープロパティのサポート。  
  
 ビジュアル ツリーを走査のビジュアル ツリーがヘルパー クラスにもサポートしています<xref:System.Windows.Media.VisualTreeHelper>です。 ビジュアル ツリーに便利コントロール固有のプロパティを通じて公開されていないため、<xref:System.Windows.Media.VisualTreeHelper>クラスは、プログラミング シナリオで必要とされる場合に、ビジュアル ツリーを走査することをお勧めします。 詳しくは、「[WPF グラフィックス レンダリングの概要](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)」をご覧ください。  
  
> [!NOTE]
>  適用されているテンプレートのビジュアル ツリーを検査するために必要な場合があります。 この手法を使用する場合に注意する必要があります。 コントロールのコンシューマーが設定してでテンプレートを変更できる常にコントロールのビジュアル ツリーを走査し、テンプレートを定義した場合は、場合でも、<xref:System.Windows.Controls.Control.Template%2A>インスタンス、およびエンド ユーザーでもプロパティに影響を与えるテンプレートを適用した変更することで、システムのテーマ。  
  
<a name="routes"></a>   
## <a name="routes-for-routed-events-as-a-tree"></a>ルーティングされたイベントに「ツリー」としてのルート  
 前述のように、visual および論理ツリー表現のハイブリッドであるツリーの単一引用符と事前に指定されたパスに沿った特定のルーティング イベントの経路を通過します。 イベントのルーティングが出張上矢印のいずれかまたはがかどうかに応じて、ツリー内での手順をトンネルまたはバブル ルーティング イベント。 イベント ルートの概念には、実際にルーティング イベントを発生させるとは別にイベントのルートを「参照」するために使用できるヘルパー クラスを直接サポートはありません。 ルートを表すクラスが<xref:System.Windows.EventRoute>、そのクラスのメソッドしますが、一般に内部でのみ使用します。  
  
<a name="resourcesandtrees"></a>   
## <a name="resource-dictionaries-and-trees"></a>リソース ディクショナリとツリー  
 すべてのリソース ディクショナリ検索`Resources`定義されているページ内を通過する時間基本的には、論理ツリー。 論理ツリーに含まれていないオブジェクトがキーを持つリソースを参照できますが、論理ツリーにそのオブジェクトが接続されている時点リソース ルックアップ シーケンスを開始します。 WPF では、論理ツリーのノードのみを持つことができます、`Resources`プロパティを含む、 <xref:System.Windows.ResourceDictionary>、したがって利点はありません。 キー付きのリソースを探してビジュアル ツリーを走査することで、<xref:System.Windows.ResourceDictionary>です。  
  
 ただし、リソースの検索も、直接の論理ツリーを超えて拡張できます。 アプリケーション マークアップでは、アプリケーション レベルのリソース ディクショナリしてから、静的プロパティまたはキーとして参照されるテーマのサポート、およびシステムの値にへとリソース ルックアップが続きます。 テーマ自体リソース参照が動的な場合は、テーマの論理ツリーの外部システムの値を参照できます。 リソース ディクショナリ、および検索ロジックの詳細については、次を参照してください。 [XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)です。  
  
## <a name="see-also"></a>関連項目  
 [入力の概要](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [WPF グラフィックス レンダリングの概要](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [オブジェクト ツリーに存在しないオブジェクト要素の初期化](../../../../docs/framework/wpf/advanced/initialization-for-object-elements-not-in-an-object-tree.md)  
 [WPF アーキテクチャ](../../../../docs/framework/wpf/advanced/wpf-architecture.md)
