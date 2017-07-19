---
title: "方法 : TextBox でカスタム コンテキスト メニューを使用する | Microsoft Docs"
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
  - "コンテキスト メニュー, カスタム"
  - "カスタム コンテキスト メニュー"
  - "メニュー, カスタム"
  - "TextBox コントロール, カスタム コンテキスト メニュー"
ms.assetid: 842d3cd5-6fa0-4be4-8d90-6c7466213b1c
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : TextBox でカスタム コンテキスト メニューを使用する
この例では、<xref:System.Windows.Controls.TextBox> に対する単純なカスタム コンテキスト メニューを定義および実装する方法を示します。  
  
## 使用例  
 次の [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] の例では、カスタム コンテキスト メニューを持つ <xref:System.Windows.Controls.TextBox> コントロールを定義しています。  
  
 コンテキスト メニューを定義するには、<xref:System.Windows.Controls.ContextMenu> 要素を使用します。  コンテキスト メニュー自体は、一連の <xref:System.Windows.Controls.MenuItem> 要素と <xref:System.Windows.Controls.Separator> 要素で構成されます。  各 <xref:System.Windows.Controls.MenuItem> 要素は、コンテキスト メニュー内のコマンドを定義します。<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> 属性は、メニュー コマンドの表示テキストを定義し、<xref:System.Windows.Controls.MenuItem.Click> 属性は各メニュー項目に対するハンドラー メソッドを指定します。  <xref:System.Windows.Controls.Separator> は、前後のメニュー項目の間に区切り線を表示するための要素です。  
  
 [!code-xml[TextBox_ContextMenu#_TextBox_ContextMenuXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml#_textbox_contextmenuxaml)]  
  
## 使用例  
 上記で定義したコンテキスト メニューの実装コード、およびコンテキスト メニューを有効または無効にするコードを次の例に示します。  <xref:System.Windows.Controls.ContextMenu.Opened> イベントを使用して、<xref:System.Windows.Controls.TextBox> の現在の状態に応じて特定のコマンドを動的に有効または無効にする処理を行います。  
  
 既定のコンテキスト メニューに戻すには、<xref:System.Windows.DependencyObject.ClearValue%2A> メソッドを使用して <xref:System.Windows.FrameworkElement.ContextMenu%2A> プロパティの値を消去します。  コンテキスト メニュー全体を無効にするには、<xref:System.Windows.FrameworkElement.ContextMenu%2A> プロパティを null 参照 \(Visual Basic の場合は `Nothing`\) に設定します。  
  
 [!code-csharp[TextBox_ContextMenu#_TextBox_ContextMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml.cs#_textbox_contextmenu)]
 [!code-vb[TextBox_ContextMenu#_TextBox_ContextMenu](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_ContextMenu/VisualBasic/Window1.xaml.vb#_textbox_contextmenu)]  
  
## 参照  
 [コンテキスト メニューでスペル チェックを使用する](../../../../docs/framework/wpf/controls/how-to-use-spell-checking-with-a-context-menu.md)   
 [TextBox の概要](../../../../docs/framework/wpf/controls/textbox-overview.md)   
 [RichTextBox の概要](../../../../docs/framework/wpf/controls/richtextbox-overview.md)