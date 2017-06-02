---
title: "コントロール |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 7652a2e64cdc107546ac3ea51178a3542606bd43
ms.contentlocale: ja-jp
ms.lasthandoff: 05/22/2017

---
# <a name="controls"></a>コントロール
<a name="introduction"></a> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] には、<xref:System.Windows.Controls.Button>、<xref:System.Windows.Controls.Label>、<xref:System.Windows.Controls.TextBox>、<xref:System.Windows.Controls.Menu>、<xref:System.Windows.Controls.ListBox> など、ほとんどの Windows アプリケーションで使用される共通の UI コンポーネントが多数用意されています。 これまで、これらのオブジェクトはコントロールと呼ばれてきました。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] SDK では、アプリケーションで表示可能なオブジェクトを表すクラスを広義に意味する用語として「コントロール」を引き続き使用しますが、クラスは、表示可能な部分を持つために <xref:System.Windows.Controls.Control> クラスを継承する必要がないことに注意してください。 <xref:System.Windows.Controls.Control> クラスを継承するクラスには、<xref:System.Windows.Controls.ControlTemplate> があります。これを使用すると、コントロールのコンシューマーは、新しいサブクラスを作成しなくても、コントロールの外観を大幅に変更できます。  このトピックでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] でのコントロール (<xref:System.Windows.Controls.Control> クラスを継承するものとそうでないものの両方) の一般的な使用方法について説明します。  
  
 
  
<a name="creating_an_instance_of_a_control"></a>   
## <a name="creating-an-instance-of-a-control"></a>コントロールのインスタンスの作成  
 アプリケーションにコントロールを追加するには、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] またはコードのいずれかを使用します。  次の例では、ユーザーに姓と名の入力を求める単純なアプリケーションの作成方法を示します。  この例では、ラベル 2 個、テキスト ボックス 2 個、ボタン 2 個の合計 6 個のコントロールを [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で作成します。 どのコントロールも同じ方法で作成できます。  
  
 [!code-xml[ControlsOverview#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 次の例では、同じアプリケーションをコードで作成します。 簡略化するために、<xref:System.Windows.Controls.Grid> である `grid1` の作成はサンプルから除外しています。                   `grid1` には、上記の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] の例で示したのと同じ列と行の定義があります。  
  
 [!code-csharp[ControlsOverview#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)] [!code-vb[ControlsOverview#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>   
## <a name="changing-the-appearance-of-a-control"></a>コントロールの外観の変更  
 通常は、アプリケーションの外観に合わせてコントロールの外観を変更します。 コントロールの外観を変更するには、目的に応じて、次のいずれかの手順を実行します。  
  
-   コントロールのプロパティ値を変更します。  
  
-   コントロールに <xref:System.Windows.Style> を作成します。  
  
-   コントロールに新しい <xref:System.Windows.Controls.ControlTemplate> を作成します。  
  
### <a name="changing-a-controls-property-value"></a>コントロールのプロパティ値の変更  
 多くのコントロールには、<xref:System.Windows.Controls.Button> の <xref:System.Windows.Controls.Control.Background%2A> のような、コントロールの外観を変更するためのプロパティが用意されています。 値プロパティは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] でもコードでも設定できます。 次の例では、<xref:System.Windows.Controls.Button> の <xref:System.Windows.Controls.Control.Background%2A>、<xref:System.Windows.Controls.Control.FontSize%2A>、<xref:System.Windows.Controls.Control.FontWeight%2A> の各プロパティを [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で設定しています。  
  
 [!code-xml[ControlsOverview#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 次の例では、同じプロパティをコードで設定しています。  
  
 [!code-csharp[ControlsOverview#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)] [!code-vb[ControlsOverview#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>コントロールのスタイル作成  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、アプリケーションの各インスタンスのプロパティを設定するのではなく、<xref:System.Windows.Style> を作成することによって、すべてのコントロールの外観を指定する機能が用意されています。                           次の例では、アプリケーションの各 <xref:System.Windows.Controls.Button> に適用される <xref:System.Windows.Style> を作成しています。                          <xref:System.Windows.Style> 定義は、通常、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] では <xref:System.Windows.ResourceDictionary> に定義されます。たとえば、<xref:System.Windows.FrameworkElement> の <xref:System.Windows.FrameworkElement.Resources%2A> プロパティがそれに該当します。  
  
 [!code-xml[ControlsOverview#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 スタイルにキーを割り当て、そのキーをコントロールの `Style` プロパティで指定することによって、特定の種類のコントロールのみにスタイルを適用することもできます。  スタイルの詳細については、「[スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)」を参照してください。  
  
### <a name="creating-a-controltemplate"></a>ControlTemplate の作成  
 <xref:System.Windows.Style> を使用すると、複数のコントロールのプロパティを一度に設定できますが、<xref:System.Windows.Style> の作成だけでは <xref:System.Windows.Controls.Control> の外観を十分カスタマイズできない場合もあります。 <xref:System.Windows.Controls.Control> クラスを継承するクラスには <xref:System.Windows.Controls.ControlTemplate> があり、これで <xref:System.Windows.Controls.Control> の構造と外観が定義されます。 <xref:System.Windows.Controls.Control> の <xref:System.Windows.Controls.Control.Template%2A> プロパティはパブリックであるため、<xref:System.Windows.Controls.Control> に既定とは異なる <xref:System.Windows.Controls.ControlTemplate> を付与できます。 一般的に、<xref:System.Windows.Controls.Control> の外観をカスタマイズするには、コントロールを継承するのではなく、<xref:System.Windows.Controls.Control> に新しい <xref:System.Windows.Controls.ControlTemplate> を指定します。  
  
 よく使用される <xref:System.Windows.Controls.Button> というコントロールについて考えてみます。  <xref:System.Windows.Controls.Button> の主な動作は、ユーザーがクリックしたときに、アプリケーションが一定のアクションを実行できるようにすることです。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、<xref:System.Windows.Controls.Button> は既定で浮き出し表示の四角形で表されます。  アプリケーションの開発中に <xref:System.Windows.Controls.Button> の動作 (ボタンのクリック イベントを処理する) を利用しながら、ボタンのプロパティを変更するだけでは実現できない外観の変更を試みることにしたとします。  このような場合は、新しい <xref:System.Windows.Controls.ControlTemplate> を作成できます。  
  
 次の例では、<xref:System.Windows.Controls.Button> の <xref:System.Windows.Controls.ControlTemplate> を作成します。  この <xref:System.Windows.Controls.ControlTemplate> は、角が丸くて背景がグラデーションになっている <xref:System.Windows.Controls.Button> を作成します。  この <xref:System.Windows.Controls.ControlTemplate> には、<xref:System.Windows.Controls.Border.Background%2A> が 2 つの <xref:System.Windows.Media.GradientStop> オブジェクトを持つ <xref:System.Windows.Media.LinearGradientBrush> である <xref:System.Windows.Controls.Border> が含まれています。  最初の <xref:System.Windows.Media.GradientStop> ではデータ バインディングを使用して、<xref:System.Windows.Media.GradientStop> の <xref:System.Windows.Media.GradientStop.Color%2A> プロパティをボタンの背景の色にバインドしています。  <xref:System.Windows.Controls.Button> の <xref:System.Windows.Controls.Control.Background%2A> プロパティを設定すると、その値の色が最初の <xref:System.Windows.Media.GradientStop> として使用されます。 データ バインディングの詳細については、「[データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)」を参照してください。 この例ではまた、<xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> が `true` のときに <xref:System.Windows.Controls.Button> の外観を変更する <xref:System.Windows.Trigger> も作成しています。  
  
 [!code-xml[ControlsOverview#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xml[ControlsOverview#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
>  この例が正常に動作するには、<xref:System.Windows.Controls.Button> の <xref:System.Windows.Controls.Control.Background%2A> プロパティが <xref:System.Windows.Media.SolidColorBrush> に設定されている必要があります。  
  
<a name="subscribing_to_events"></a>   
## <a name="subscribing-to-events"></a>イベントのサブスクライブ  
 コントロールのイベントをサブスクライブするには、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] またはコードを使用できますが、コードではイベントの処理しかできません。  次の例では、<xref:System.Windows.Controls.Button> の `Click` イベントをサブスクライブする方法を示します。  
  
 [!code-xml[ControlsOverview#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8) ] [!code-vb [ControlsOverview#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 次の例は、<xref:System.Windows.Controls.Button> の `Click` イベントを処理しています。  
  
 [!code-csharp[ControlsOverview#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9) ] [!code-vb [ControlsOverview#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>   
## <a name="rich-content-in-controls"></a>コントロールでのリッチ コンテンツ  
 <xref:System.Windows.Controls.Control> クラスを継承するほとんどのクラスに、リッチ コンテンツを格納する機能があります。 たとえば、<xref:System.Windows.Controls.Label> には、文字列、<xref:System.Windows.Controls.Image>、<xref:System.Windows.Controls.Panel> など、任意のオブジェクトを格納できます。  以下のクラスは、リッチ コンテンツをサポートし、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のほとんどのコントロールの基本クラスとして機能します。  
  
-   <xref:System.Windows.Controls.ContentControl>-- このクラスを継承するクラスには、<xref:System.Windows.Controls.Label>、<xref:System.Windows.Controls.Button>、<xref:System.Windows.Controls.ToolTip> などがあります。  
  
-   <xref:System.Windows.Controls.ItemsControl>-- このクラスを継承するクラスには、<xref:System.Windows.Controls.ListBox>、<xref:System.Windows.Controls.Menu>、<xref:System.Windows.Controls.Primitives.StatusBar> などがあります。  
  
-   <xref:System.Windows.Controls.HeaderedContentControl>-- このクラスを継承するクラスには、<xref:System.Windows.Controls.TabItem>、<xref:System.Windows.Controls.GroupBox>、<xref:System.Windows.Controls.Expander> などがあります。  
  
-   <xref:System.Windows.Controls.HeaderedItemsControl>-- このクラスを継承するクラスには、<xref:System.Windows.Controls.MenuItem>、<xref:System.Windows.Controls.TreeViewItem>、<xref:System.Windows.Controls.ToolBar> などがあります。  
  
-  
  
 これらの基本クラスの詳細については、「[WPF のコンテンツ モデル](../../../../docs/framework/wpf/controls/wpf-content-model.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [カテゴリ別のコントロール](../../../../docs/framework/wpf/controls/controls-by-category.md)   
 [コントロール ライブラリ](../../../../docs/framework/wpf/controls/control-library.md)   
 [データ テンプレートの概要](../../../../docs/framework/wpf/data/data-templating-overview.md)   
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [入力](../../../../docs/framework/wpf/advanced/input-wpf.md)   
 [コマンドを有効にする](../../../../docs/framework/wpf/advanced/how-to-enable-a-command.md)   
 [チュートリアル : カスタム アニメーション ボタンの作成](../../../../docs/framework/wpf/controls/walkthroughs-create-a-custom-animated-button.md)   
 [コントロールのカスタマイズ](../../../../docs/framework/wpf/controls/control-customization.md)
