---
title: "方法 : 複数行の TextBox コントロールを作成する | Microsoft Docs"
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
  - "TextBox コントロール, 複数行 (テキストの)"
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : 複数行の TextBox コントロールを作成する
この例では、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] を使用して、複数行のテキストが収まるように自動的に拡大する <xref:System.Windows.Controls.TextBox> コントロールを定義する方法を説明します。  
  
## 使用例  
 <xref:System.Windows.Controls.TextBox.TextWrapping%2A> 属性を **Wrap** に設定すると、入力したテキストが <xref:System.Windows.Controls.TextBox> コントロールの端に達すると次の行に折り返されます。<xref:System.Windows.Controls.TextBox> コントロールのサイズは、新しい行が収まるように必要に応じて自動的に調整されます。  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> 属性を **true** に設定した場合は、Enter キーを押すたびに新しい行が挿入されます。このときも、<xref:System.Windows.Controls.TextBox> は新しい行が収まるように必要に応じて自動的に調整されます。  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> 属性を設定すると <xref:System.Windows.Controls.TextBox> にスクロール バーが追加され、<xref:System.Windows.Controls.TextBox> がそれを囲むフレームまたはウィンドウのサイズよりも大きくなった場合は、<xref:System.Windows.Controls.TextBox> の内容をスクロールすることができます。  
  
 [!code-xml[TextBox_MiscCode#_MultilineTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## 参照  
 <xref:System.Windows.TextWrapping>   
 [TextBox の概要](../../../../docs/framework/wpf/controls/textbox-overview.md)   
 [RichTextBox の概要](../../../../docs/framework/wpf/controls/richtextbox-overview.md)