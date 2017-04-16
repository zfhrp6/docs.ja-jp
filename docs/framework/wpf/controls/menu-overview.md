---
title: "メニューの概要 | Microsoft Docs"
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
  - "メニュー コントロール"
  - "メニュー コントロール"
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# メニューの概要
<xref:System.Windows.Controls.Menu>クラスでは、コマンドおよび階層の順序でイベント ハンドラーに関連付けられている要素を整理することができます。 各<xref:System.Windows.Controls.Menu>要素のコレクションを格納する<xref:System.Windows.Controls.MenuItem>要素。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="menu_control"></a>   
## <a name="menu-control"></a>メニュー コントロール  
 <xref:System.Windows.Controls.Menu>コントロールは、コマンドまたはアプリケーションのオプションを指定する項目の一覧を表示します。 通常をクリックすると、 <xref:System.Windows.Controls.MenuItem>サブメニューを開くかによって、コマンドを実行するアプリケーション。  
  
<a name="creating_menus"></a>   
## <a name="creating-menus"></a>メニューを作成します。  
 次の例を作成し、 [] メニューの <xref:System.Windows.Controls.Menu>でテキストを操作、 <xref:System.Windows.Controls.TextBox>します。 [] メニューの <xref:System.Windows.Controls.Menu>が含まれています<xref:System.Windows.Controls.MenuItem>を使用するオブジェクト、<xref:System.Windows.Controls.MenuItem.Command%2A>、 <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>、および<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>プロパティおよび<xref:System.Windows.Controls.MenuItem.Checked>、<xref:System.Windows.Controls.MenuItem.Unchecked>と<xref:System.Windows.Controls.MenuItem.Click>イベントです。  
  
 [!code-xml[MenuItemCommandsAndEvents#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>   
## <a name="menuitems-with-keyboard-shortcuts"></a>キーボード ショートカットの MenuItems  
 ショートカット キーは、キーボードで入力できる文字の組み合わせ<xref:System.Windows.Controls.Menu>コマンドです。 たとえば、ショートカット キーを**コピー**は CTRL キーを押しながら C キー。 ショートカット キーとメニュー項目を使用する&2; つのプロパティ-<xref:System.Windows.Controls.MenuItem.InputGestureText%2A>または<xref:System.Windows.Controls.MenuItem.Command%2A>します。  
  
<a name="menus_inputgesturetext"></a>   
### <a name="inputgesturetext"></a>InputGestureText  
 次の例を使用する方法を示しています、 <xref:System.Windows.Controls.MenuItem.InputGestureText%2A>にキーボード ショートカットのテキストを割り当てるプロパティを<xref:System.Windows.Controls.MenuItem>コントロールです。 キーボード ショートカット メニュー項目にのみ生じます。  コマンドでは関連付けられません、 <xref:System.Windows.Controls.MenuItem>します。 アプリケーションでは、アクションを実行するために、ユーザーの入力を処理する必要があります。  
  
 [!code-xml[MenuEvent#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>   
### <a name="command"></a>コマンド  
 使用する例を次に示します、<xref:System.Windows.Controls.MenuItem.Command%2A>プロパティに関連付けるには、**開く**と**保存**コマンドと<xref:System.Windows.Controls.MenuItem>コントロールです。 Command プロパティがコマンドに関連付けるだけでなく、 <xref:System.Windows.Controls.MenuItem>、もショートカットとして使用する入力ジェスチャのテキストを提供しています。  
  
 [!code-xml[MenuEvent#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 <xref:System.Windows.Controls.MenuItem>クラスもあります、 <xref:System.Windows.Controls.MenuItem.CommandTarget%2A>プロパティをコマンドが発生する要素を指定します。 場合<xref:System.Windows.Controls.MenuItem.CommandTarget%2A>未設定、キーボード フォーカスを持つ要素は、コマンドを受信します。 コマンドの詳細については、次を参照してください。[コマンドの実行の概要](../../../../docs/framework/wpf/advanced/commanding-overview.md)します。  
  
<a name="menu_styling"></a>   
## <a name="menu-styling"></a>メニューのスタイル設定  
 コントロールのスタイル設定を大幅に変更の動作と外観<xref:System.Windows.Controls.Menu>カスタム コントロールを記述しなくても制御します。 視覚プロパティの設定だけでなく適用することも、<xref:System.Windows.Style>コントロールの各部分にプロパティを使用してコントロールの一部の動作を変更または追加のパーツを追加またはコントロールのレイアウトを変更します。 次の例では、いくつかの方法で追加、<xref:System.Windows.Style>に、<xref:System.Windows.Controls.Menu>コントロールです。  
  
 最初のコード例で定義、<xref:System.Windows.Style>と呼ばれる`Simple`自分のスタイルの現在のシステム設定を使用する方法を示します。 色を代入して、 `MenuHighlightBrush`  メニューの背景色として、 `MenuTextBrush`  メニューの前景色として。 ブラシを割り当てるには、リソース キーを使用することに注意してください。  
  
 [!code-xml[MenuStylesSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 次のサンプルは<xref:System.Windows.Trigger>要素の外観を変更するための<xref:System.Windows.Controls.MenuItem>で発生するイベントに応答、<xref:System.Windows.Controls.Menu>します。 上でマウスを移動すると、<xref:System.Windows.Controls.Menu>、前景色を指定し、メニュー項目のフォント特性を変更します。  
  
 [!code-xml[MenuStylesSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a>関連項目  
 [WPF コントロール ギャラリーのサンプル](http://go.microsoft.com/fwlink/?LinkID=160053)