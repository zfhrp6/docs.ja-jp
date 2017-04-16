---
title: "ContextMenu の概要 | Microsoft Docs"
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
  - "ContextMenu コントロール [WPF], ContextMenu コントロールの概要"
  - "コントロール, ContextMenu"
ms.assetid: 16909c42-799a-4561-91e0-7d69dcfeea91
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 24
---
# ContextMenu の概要
<xref:System.Windows.Controls.ContextMenu> クラスは、コンテキスト固有の <xref:System.Windows.Controls.Menu> を使用して機能を公開する要素を表します。  通常、ユーザーはマウス ボタンを右クリックすることで、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] に <xref:System.Windows.Controls.ContextMenu> を公開します。  ここでは、<xref:System.Windows.Controls.ContextMenu> 要素について説明し、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] とコードでそれを使用する例を示します。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="contextmenu_control"></a>   
## ContextMenu コントロール  
 <xref:System.Windows.Controls.ContextMenu> は特定のコントロールに結合されます。  <xref:System.Windows.Controls.ContextMenu> 要素を使用すると、<xref:System.Windows.Controls.Button> などの特定のコントロールに関連付けられているコマンドやオプションを指定する項目の一覧を、ユーザーに提供できます。  ユーザーは、コントロールを右クリックすることで、メニューを表示します。  通常、<xref:System.Windows.Controls.MenuItem> をクリックすると、サブメニューが開くか、アプリケーションがコマンドを実行します。  
  
<a name="creating_contextmenus"></a>   
## ContextMenu の作成  
 サブメニューのある <xref:System.Windows.Controls.ContextMenu> を作成する方法を次の例に示します。  <xref:System.Windows.Controls.ContextMenu> コントロールは、ボタン コントロールに結合されます。  
  
 [!code-xml[ContextMenu#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>   
## ContextMenu へのスタイルの適用  
 コントロールの <xref:System.Windows.Style> を使用すると、カスタム コントロールを作成しなくても、<xref:System.Windows.Controls.ContextMenu> の外観や動作を大幅に変更できます。  視覚プロパティの設定に加えて、コントロールの一部にスタイルを適用することもできます。  たとえば、プロパティを使用したコントロールの動作を一部変更したり、<xref:System.Windows.Controls.ContextMenu> に対するパーツの追加やレイアウトの変更を行ったりすることができます。  <xref:System.Windows.Controls.ContextMenu> コントロールにスタイルを追加するいくつかの方法を次の例に示します。  
  
 最初の例は、`SimpleSysResources` という名前のスタイルを定義し、スタイルで現在のシステム設定を使用する方法を示しています。  この例では、<xref:System.Windows.Controls.ContextMenu> の <xref:System.Windows.Controls.Control.Background%2A> の色として <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> を割り当て、<xref:System.Windows.Controls.Control.Foreground%2A> の色として <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> を割り当てています。  
  
```  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=   
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=   
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 次の例では、<xref:System.Windows.Trigger> 要素を使用して、<xref:System.Windows.Controls.ContextMenu> で発生するイベントに応じて <xref:System.Windows.Controls.Menu> の外観を変更しています。  ユーザーがメニューの上にマウスを移動すると、<xref:System.Windows.Controls.ContextMenu> 項目の外観が変わります。  
  
```  
<Style x:Key="Triggers" TargetType="{x:Type MenuItem}">  
  <Style.Triggers>  
    <Trigger Property="MenuItem.IsMouseOver" Value="true">  
      <Setter Property = "FontSize" Value="16"/>  
      <Setter Property = "FontStyle" Value="Italic"/>  
      <Setter Property = "Foreground" Value="Red"/>  
    </Trigger>  
  </Style.Triggers>  
</Style>  
```  
  
## 参照  
 <xref:System.Windows.Controls.ContextMenu>   
 <xref:System.Windows.Style>   
 <xref:System.Windows.Controls.Menu>   
 <xref:System.Windows.Controls.MenuItem>   
 [ContextMenu](../../../../docs/framework/wpf/controls/contextmenu.md)   
 [ContextMenu のスタイルとテンプレート](../../../../docs/framework/wpf/controls/contextmenu-styles-and-templates.md)   
 [WPF コントロール ギャラリーのサンプル](http://go.microsoft.com/fwlink/?LinkID=160053)