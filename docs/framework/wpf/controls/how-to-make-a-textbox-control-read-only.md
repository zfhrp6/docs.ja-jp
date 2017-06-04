---
title: "方法 : TextBox コントロールを読み取り専用にする | Microsoft Docs"
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
  - "読み取り専用の TextBox コントロール"
  - "TextBox コントロール (読み取り専用)"
ms.assetid: e707ec59-8b22-473e-b77c-3060a237517a
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : TextBox コントロールを読み取り専用にする
この例では、<xref:System.Windows.Controls.TextBox> コントロールをユーザーが入力または変更できないように構成する方法を示します。  
  
## 使用例  
 ユーザーが <xref:System.Windows.Controls.TextBox> コントロールの内容を変更できないようにするには、<xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> 属性を **true** に設定します。  
  
 [!code-xml[TextBox_MiscCode#_ReadOnlyTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_readonlytextboxxaml)]  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> 属性が適用されるのはユーザー入力だけです。[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] での <xref:System.Windows.Controls.TextBox> コントロールの記述で設定されているテキスト、または <xref:System.Windows.Controls.TextBox.Text%2A> プロパティでプログラムを使用して設定されるテキストは影響を受けません。  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> の既定値は **false** です。  
  
## 参照  
 [TextBox の概要](../../../../docs/framework/wpf/controls/textbox-overview.md)   
 [RichTextBox の概要](../../../../docs/framework/wpf/controls/richtextbox-overview.md)