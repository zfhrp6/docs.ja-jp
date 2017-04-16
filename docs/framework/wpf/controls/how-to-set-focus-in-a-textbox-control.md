---
title: "方法 : TextBox コントロールにフォーカスを設定する | Microsoft Docs"
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
  - "フォーカス, 設定"
  - "TextBox コントロール, 設定 (フォーカスを)"
ms.assetid: 24b61b45-dc2d-425e-9839-b017af7ab86f
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : TextBox コントロールにフォーカスを設定する
<xref:System.Windows.UIElement.Focus%2A> メソッドを使用して、<xref:System.Windows.Controls.TextBox> コントロールにフォーカスを設定する方法を次の例に示します。  
  
## 使用例  
 次の [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 例は、*tbFocusMe* という名前の単純な <xref:System.Windows.Controls.TextBox> コントロールを示しています。  
  
 [!code-xml[TextBox_MiscCode#_TextBoxFocusXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxfocusxaml)]  
  
## 使用例  
 次の例では、<xref:System.Windows.UIElement.Focus%2A> メソッドを呼び出して、*tbFocusMe* という名前の <xref:System.Windows.Controls.TextBox> コントロールにフォーカスを設定しています。  
  
 [!code-csharp[TextBox_MiscCode#_FocusTextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_focustextbox)]
 [!code-vb[TextBox_MiscCode#_FocusTextBox](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_focustextbox)]  
  
## 参照  
 <xref:System.Windows.UIElement.Focusable%2A>   
 <xref:System.Windows.UIElement.IsFocused%2A>   
 [TextBox の概要](../../../../docs/framework/wpf/controls/textbox-overview.md)   
 [RichTextBox の概要](../../../../docs/framework/wpf/controls/richtextbox-overview.md)