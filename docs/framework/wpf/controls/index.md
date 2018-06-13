---
title: コントロール
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
ms.openlocfilehash: 11c9c2cdd9e485fb87f5d8ead7790ded0428f7dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558292"
---
# <a name="controls"></a>コントロール
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] など、ほぼすべての Windows アプリケーションで使用される共通の UI コンポーネントの多くに付属して<xref:System.Windows.Controls.Button>、 <xref:System.Windows.Controls.Label>、 <xref:System.Windows.Controls.TextBox>、 <xref:System.Windows.Controls.Menu>、および<xref:System.Windows.Controls.ListBox>です。 これまで、これらのオブジェクトはコントロールと呼ばれてきました。 中に、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] SDK で引き続き疎アプリケーションでは、表示されているオブジェクトを表す任意のクラスを意味する「コントロール」という用語を使用するクラスが継承する必要がないことを確認することが重要、<xref:System.Windows.Controls.Control>表示に存在するクラス。 継承するクラス、<xref:System.Windows.Controls.Control>クラスが含まれて、 <xref:System.Windows.Controls.ControlTemplate>、これにより、根本的に、新しいサブクラスを作成することがなく、コントロールの外観を変更するコントロールのコンシューマーです。  このトピックについて説明方法コントロール (両方ものからは継承、<xref:System.Windows.Controls.Control>クラスとそうでないもの) でよく使用される[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]です。  

<a name="creating_an_instance_of_a_control"></a>   
## <a name="creating-an-instance-of-a-control"></a>コントロールのインスタンスの作成  
 コントロールをアプリケーションに追加するにはいずれかを使用して[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]またはコード。  次の例では、ユーザーに姓と名の入力を求める単純なアプリケーションの作成方法を示します。  この例は、6 つのコントロールを作成します。 2 つのラベル、2 つのテキスト ボックスとボタンが 2 つの[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]します。 どのコントロールも同じ方法で作成できます。  
  
 [!code-xaml[ControlsOverview#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 次の例では、同じアプリケーションをコードで作成します。 簡略化のための作成、 <xref:System.Windows.Controls.Grid>、 `grid1`、サンプルから除外されています。 `grid1` 上記のように同じ列と行の定義を持つ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]例です。  
  
 [!code-csharp[ControlsOverview#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>   
## <a name="changing-the-appearance-of-a-control"></a>コントロールの外観の変更  
 通常は、アプリケーションの外観に合わせてコントロールの外観を変更します。 コントロールの外観を変更するには、目的に応じて、次のいずれかの手順を実行します。  
  
-   コントロールのプロパティ値を変更します。  
  
-   作成、<xref:System.Windows.Style>コントロール。  
  
-   新しい<xref:System.Windows.Controls.ControlTemplate>コントロール。  
  
### <a name="changing-a-controls-property-value"></a>コントロールのプロパティ値の変更  
 多くのコントロールは、プロパティ、コントロールの表示方法などを変更することを持つ、<xref:System.Windows.Controls.Control.Background%2A>の<xref:System.Windows.Controls.Button>です。 両方の値のプロパティを設定することができます[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]とコード。 次の例のセット、 <xref:System.Windows.Controls.Control.Background%2A>、 <xref:System.Windows.Controls.Control.FontSize%2A>、および<xref:System.Windows.Controls.Control.FontWeight%2A>プロパティを<xref:System.Windows.Controls.Button>で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]です。  
  
 [!code-xaml[ControlsOverview#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 次の例では、同じプロパティをコードで設定しています。  
  
 [!code-csharp[ControlsOverview#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>コントロールのスタイル作成  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 作成することで、アプリケーション内の各インスタンスのプロパティを設定する代わりに、コントロールの外観を指定することができます、<xref:System.Windows.Style>です。 次の例を作成、<xref:System.Windows.Style>それぞれに適用されている<xref:System.Windows.Controls.Button>アプリケーションにします。 <xref:System.Windows.Style> 定義されている定義が通常[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]で、 <xref:System.Windows.ResourceDictionary>、ように、<xref:System.Windows.FrameworkElement.Resources%2A>のプロパティ、<xref:System.Windows.FrameworkElement>です。  
  
 [!code-xaml[ControlsOverview#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 スタイルにキーを割り当てる場合や内でそのキーを指定することによって、特定の種類の特定のコントロールのみにスタイルを適用することも、`Style`コントロールのプロパティです。  スタイルの詳細については、次を参照してください。[スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)です。  
  
### <a name="creating-a-controltemplate"></a>ControlTemplate の作成  
 A <xref:System.Windows.Style> 、一度に複数のコントロールのプロパティを設定することができますの外観をカスタマイズすることがあります、<xref:System.Windows.Controls.Control>作成することで行うことができますを超える、<xref:System.Windows.Style>です。 継承するクラス、<xref:System.Windows.Controls.Control>クラスが、 <xref:System.Windows.Controls.ControlTemplate>、構造との外観を定義する、<xref:System.Windows.Controls.Control>です。 <xref:System.Windows.Controls.Control.Template%2A>のプロパティ、<xref:System.Windows.Controls.Control>ができるようにするためにパブリックで、 <xref:System.Windows.Controls.Control> 、<xref:System.Windows.Controls.ControlTemplate>既定とは異なる。 多くの場合を指定できます、新しい<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Control>の外観をカスタマイズするコントロールから継承する代わりに、<xref:System.Windows.Controls.Control>です。  
  
 非常に共通のコントロールを検討してください<xref:System.Windows.Controls.Button>です。  主な動作、<xref:System.Windows.Controls.Button>は、ユーザーがクリックしたときに何らかのアクションを実行するアプリケーションを有効にします。  既定では、<xref:System.Windows.Controls.Button>で[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]発生四角形として表示されます。  アプリケーションの開発中にすることができますの動作を利用、 <xref:System.Windows.Controls.Button>--。 つまり、処理することにより、ボタンのクリック イベント--がボタンのプロパティを変更することによって行うことができますを超えるボタンの外観を変更する可能性があります。  この場合、作成、新しい<xref:System.Windows.Controls.ControlTemplate>です。  
  
 次の例を作成、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Button>です。  <xref:System.Windows.Controls.ControlTemplate>を作成、<xref:System.Windows.Controls.Button>角の丸いとグラデーションの背景を使用します。  <xref:System.Windows.Controls.ControlTemplate>が含まれています、<xref:System.Windows.Controls.Border>が<xref:System.Windows.Controls.Border.Background%2A>は、 <xref:System.Windows.Media.LinearGradientBrush> 、2 つ<xref:System.Windows.Media.GradientStop>オブジェクト。  最初の<xref:System.Windows.Media.GradientStop>データ バインディングを使用して、バインド、<xref:System.Windows.Media.GradientStop.Color%2A>のプロパティ、<xref:System.Windows.Media.GradientStop>ボタンの背景の色にします。  設定すると、<xref:System.Windows.Controls.Control.Background%2A>のプロパティ、 <xref:System.Windows.Controls.Button>、その値の色が 1 つ目として使用される<xref:System.Windows.Media.GradientStop>です。 データ バインディングの詳細については、「[データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)」を参照してください。 例でも作成、<xref:System.Windows.Trigger>の外観を変更する、<xref:System.Windows.Controls.Button>とき<xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A>は`true`します。  
  
 [!code-xaml[ControlsOverview#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xaml[ControlsOverview#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
>  <xref:System.Windows.Controls.Control.Background%2A>のプロパティ、<xref:System.Windows.Controls.Button>に設定する必要があります、<xref:System.Windows.Media.SolidColorBrush>の例が適切に機能します。  
  
<a name="subscribing_to_events"></a>   
## <a name="subscribing-to-events"></a>イベントのサブスクライブ  
 いずれかを使用して、コントロールのイベントにサブスクライブできます[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]コードが処理できるコード内のイベントまたはします。  次の例をサブスクライブする方法を示しています、`Click`のイベント、<xref:System.Windows.Controls.Button>です。  
  
 [!code-xaml[ControlsOverview#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 次の例のハンドル、`Click`のイベント、<xref:System.Windows.Controls.Button>です。  
  
 [!code-csharp[ControlsOverview#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>   
## <a name="rich-content-in-controls"></a>コントロールでのリッチ コンテンツ  
 ほとんどのクラスから継承する、<xref:System.Windows.Controls.Control>クラス豊富なコンテンツを格納する容量があります。 たとえば、<xref:System.Windows.Controls.Label>文字列など、任意のオブジェクトを含めることができます、 <xref:System.Windows.Controls.Image>、または<xref:System.Windows.Controls.Panel>です。  次のクラスは、豊富なコンテンツのサポートを提供し、ほとんどのコントロールの基本クラスとして機能[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]します。  
  
-   <xref:System.Windows.Controls.ContentControl>-このクラスから継承したクラスの例としては<xref:System.Windows.Controls.Label>、 <xref:System.Windows.Controls.Button>、および<xref:System.Windows.Controls.ToolTip>です。  
  
-   <xref:System.Windows.Controls.ItemsControl>-このクラスから継承したクラスの例としては<xref:System.Windows.Controls.ListBox>、 <xref:System.Windows.Controls.Menu>、および<xref:System.Windows.Controls.Primitives.StatusBar>です。  
  
-   <xref:System.Windows.Controls.HeaderedContentControl>-このクラスから継承したクラスの例としては<xref:System.Windows.Controls.TabItem>、 <xref:System.Windows.Controls.GroupBox>、および<xref:System.Windows.Controls.Expander>です。  
  
-   <xref:System.Windows.Controls.HeaderedItemsControl>-このクラスから継承したクラスの例としては<xref:System.Windows.Controls.MenuItem>、 <xref:System.Windows.Controls.TreeViewItem>、および<xref:System.Windows.Controls.ToolBar>です。  
  
-  
  
 これらの基本クラスの詳細については、次を参照してください。 [WPF コンテンツ モデル](../../../../docs/framework/wpf/controls/wpf-content-model.md)です。  
  
## <a name="see-also"></a>関連項目  
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [カテゴリ別のコントロール](../../../../docs/framework/wpf/controls/controls-by-category.md)  
 [コントロール ライブラリ](../../../../docs/framework/wpf/controls/control-library.md)  
 [データ テンプレートの概要](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [入力](../../../../docs/framework/wpf/advanced/input-wpf.md)  
 [コマンドを有効にする](../../../../docs/framework/wpf/advanced/how-to-enable-a-command.md)  
 [チュートリアル: カスタム アニメーション ボタンの作成](../../../../docs/framework/wpf/controls/walkthroughs-create-a-custom-animated-button.md)  
 [コントロールのカスタマイズ](../../../../docs/framework/wpf/controls/control-customization.md)
