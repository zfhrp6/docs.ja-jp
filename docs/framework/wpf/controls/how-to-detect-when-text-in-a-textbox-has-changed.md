---
title: "方法 : TextBox のテキストがいつ変更されたかを検出する | Microsoft Docs"
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
  - "検出 (テキストの変更を)"
  - "テキストの変更, 検出"
  - "TextBox コントロール, 検出 (テキストの変更を)"
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : TextBox のテキストがいつ変更されたかを検出する
この例では、<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> イベントを使用して、<xref:System.Windows.Controls.TextBox> コントロール内のテキストが変わるたびにメソッドを実行する 1 つの方法を示します。  
  
 変更用にモニターする <xref:System.Windows.Controls.TextBox> コントロールを含む [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] の分離コード クラスでは、<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> イベントの実行時に呼び出し用メソッドを挿入します。  このメソッドには、<xref:System.Windows.Controls.TextChangedEventHandler> デリゲートで想定された署名に一致する署名を含める必要があります。  
  
 イベント ハンドラーは、<xref:System.Windows.Controls.TextBox> コントロールの内容が変更されるたびにユーザーまたはプログラムによって呼び出されます。  
  
 **メモ :** このイベントは、<xref:System.Windows.Controls.TextBox> コントロールが作成され、テキストが初めて読み込まれるときに実行されます。  
  
## 使用例  
 <xref:System.Windows.Controls.TextBox> コントロールを定義する [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] で、<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> 属性に、イベント ハンドラーのメソッド名と一致する値を指定します。  
  
 [!code-xml[TextBox_MiscCode#_TextChangedXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]  
  
## 使用例  
 変更用にモニターする <xref:System.Windows.Controls.TextBox> コントロールを含む [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] の分離コード クラスでは、<xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> イベントの実行時に呼び出し用メソッドを挿入します。  このメソッドには、<xref:System.Windows.Controls.TextChangedEventHandler> デリゲートで想定された署名に一致する署名を含める必要があります。  
  
 [!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
 [!code-vb[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]  
  
 イベント ハンドラーは、<xref:System.Windows.Controls.TextBox> コントロールの内容が変更されるたびにユーザーまたはプログラムによって呼び出されます。  
  
 **メモ :** このイベントは、<xref:System.Windows.Controls.TextBox> コントロールが作成され、テキストが初めて読み込まれるときに実行されます。  
  
 コメント  
  
## 参照  
 <xref:System.Windows.Controls.TextChangedEventArgs>   
 [TextBox の概要](../../../../docs/framework/wpf/controls/textbox-overview.md)   
 [RichTextBox の概要](../../../../docs/framework/wpf/controls/richtextbox-overview.md)