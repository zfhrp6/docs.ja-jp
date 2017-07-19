---
title: "方法 : TextBox コントロールのテキスト コンテンツを設定する | Microsoft Docs"
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
  - "テキスト コンテンツ, 設定"
  - "TextBox コントロール, 設定 (テキスト コンテンツを)"
ms.assetid: bcd25fc7-a52f-4453-b802-2c8d2b335ab8
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : TextBox コントロールのテキスト コンテンツを設定する
この例では、<xref:System.Windows.Controls.TextBox.Text%2A> プロパティを使用して、<xref:System.Windows.Controls.TextBox> コントロールの初期のテキスト コンテンツを設定する方法を示します。  
  
 **メモ** この例の [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] バージョンでは、各ボタンの <xref:System.Windows.Controls.TextBox> コンテンツのテキストの前後に `<TextBox.Text>` タグを使用することもできますが、<xref:System.Windows.Controls.TextBox> は <xref:System.Windows.Controls.TextBox.Text%2A> プロパティに  <xref:System.Windows.Markup.ContentPropertyAttribute> 属性を適用するため、この処理は必要ありません。  詳細については、「[XAML の概要 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)」を参照してください。  
  
## 使用例  
 [!code-xml[TextBox_MiscCode#_TextBoxSetTextXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]  
  
## 使用例  
 [!code-csharp[TextBox_MiscCode#_TextBoxSetText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
 [!code-vb[TextBox_MiscCode#_TextBoxSetText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]  
  
## 参照  
 [TextBox の概要](../../../../docs/framework/wpf/controls/textbox-overview.md)   
 [RichTextBox の概要](../../../../docs/framework/wpf/controls/richtextbox-overview.md)