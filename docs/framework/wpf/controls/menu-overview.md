---
title: "メニューの概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Menu control [WPF]
- controls [WPF], Menu
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 81611e7c5f509314b10e3188106870bdc67dfb0e
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="menu-overview"></a>メニューの概要
<xref:System.Windows.Controls.Menu>クラスでは、コマンドおよび階層の順序でイベント ハンドラーに関連付けられている要素を整理することができます。 各<xref:System.Windows.Controls.Menu>要素のコレクションを含みます<xref:System.Windows.Controls.MenuItem>要素。  
  
  
<a name="menu_control"></a>   
## <a name="menu-control"></a>メニュー コントロール  
 <xref:System.Windows.Controls.Menu>コントロール コマンドまたはアプリケーションのオプションを指定する項目の一覧が表示されます。 通常をクリックすると、<xref:System.Windows.Controls.MenuItem>サブメニューを開くかにより、アプリケーションは、コマンドを実行します。  
  
<a name="creating_menus"></a>   
## <a name="creating-menus"></a>メニューの作成  
 次の例を作成、<xref:System.Windows.Controls.Menu>内のテキストを操作する、<xref:System.Windows.Controls.TextBox>です。 <xref:System.Windows.Controls.Menu>が含まれています<xref:System.Windows.Controls.MenuItem>使用するオブジェクト、 <xref:System.Windows.Controls.MenuItem.Command%2A>、 <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>、および<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>プロパティおよび<xref:System.Windows.Controls.MenuItem.Checked>、 <xref:System.Windows.Controls.MenuItem.Unchecked>、および<xref:System.Windows.Controls.MenuItem.Click>イベント。  
  
 [!code-xaml[MenuItemCommandsAndEvents#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>   
## <a name="menuitems-with-keyboard-shortcuts"></a>キーボード ショートカット付きのメニュー項目  
 キーボード ショートカットは、キーボードで入力できる文字の組み合わせ<xref:System.Windows.Controls.Menu>コマンド。 たとえば、**コピー**のショートカットは CTRL+C です。 キーボード ショートカットやメニュー項目に使用する 2 つのプロパティ-<xref:System.Windows.Controls.MenuItem.InputGestureText%2A>または<xref:System.Windows.Controls.MenuItem.Command%2A>です。  
  
<a name="menus_inputgesturetext"></a>   
### <a name="inputgesturetext"></a>InputGestureText  
 次の例を使用する方法を示しています、<xref:System.Windows.Controls.MenuItem.InputGestureText%2A>にキーボード ショートカット テキストを割り当てるプロパティを<xref:System.Windows.Controls.MenuItem>コントロール。 これは、キーボード ショートカットをメニュー項目に配置するだけです。  コマンドでは関連付けません、<xref:System.Windows.Controls.MenuItem>です。 アプリケーションでは、アクションを実行するために、ユーザーの入力を処理する必要があります。  
  
 [!code-xaml[MenuEvent#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>   
### <a name="command"></a>コマンド  
 使用する次の例に示します、<xref:System.Windows.Controls.MenuItem.Command%2A>プロパティに関連付けるには、**開く**と**保存**コマンドと<xref:System.Windows.Controls.MenuItem>コントロール。 コマンドのプロパティはコマンドに関連付けるだけでなく、 <xref:System.Windows.Controls.MenuItem>、もショートカットとして使用する入力ジェスチャ テキストを提供しています。  
  
 [!code-xaml[MenuEvent#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 <xref:System.Windows.Controls.MenuItem>クラスもあります、<xref:System.Windows.Controls.MenuItem.CommandTarget%2A>プロパティをコマンドが発生した要素を指定します。 場合<xref:System.Windows.Controls.MenuItem.CommandTarget%2A>が設定された場合、キーボード フォーカスを持つ要素は、コマンドを受信します。 コマンドの詳細については、[Commanding Overview](../../../../docs/framework/wpf/advanced/commanding-overview.md)を参照してください。  
  
<a name="menu_styling"></a>   
## <a name="menu-styling"></a>メニューのスタイル指定  
 コントロールのスタイル設定を大幅に変更の動作と外観<xref:System.Windows.Controls.Menu>をカスタム コントロールを記述しなくても制御します。 視覚プロパティの設定に加えて適用することも、<xref:System.Windows.Style>コントロールの各部分に、プロパティを使用してコントロールの一部の動作を変更または追加部分を追加またはコントロールのレイアウトを変更します。 次の例では、いくつかの方法を追加する、<xref:System.Windows.Style>を<xref:System.Windows.Controls.Menu>コントロール。  
  
 最初のコード例では定義、<xref:System.Windows.Style>と呼ばれる`Simple`を自分のスタイルで現在のシステム設定を使用する方法を示しています。 このコードは、`MenuHighlightBrush`の色をメニューの背景色として、 `MenuTextBrush`の色をメニューの前景色として割り当てます。 ブラシを割り当てるには、リソース キーを使用することに注意してください。  
  
 [!code-xaml[MenuStylesSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 次のサンプルは<xref:System.Windows.Trigger>要素の外観を変更できる、<xref:System.Windows.Controls.MenuItem>で発生するイベントに応答、<xref:System.Windows.Controls.Menu>です。 上でマウスを移動すると、 <xref:System.Windows.Controls.Menu>、前景色を指定し、メニュー項目のフォント特性を変更します。  
  
 [!code-xaml[MenuStylesSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a>関連項目  
 [WPF Controls Gallery Sample](http://go.microsoft.com/fwlink/?LinkID=160053)
