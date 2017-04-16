---
title: "方法 : RichTextBox からテキスト コンテンツを抽出する | Microsoft Docs"
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
  - "コンテンツ, 抽出"
  - "抽出 (テキスト コンテンツを)"
  - "RichTextBox コントロール, 抽出 (テキスト コンテンツを)"
  - "テキスト コンテンツ, 抽出"
ms.assetid: f13c093f-1a05-45b3-ac8f-c9ea5e4a11c5
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : RichTextBox からテキスト コンテンツを抽出する
この例では、<xref:System.Windows.Controls.RichTextBox> のコンテンツをプレーン テキストとして抽出する方法を示します。  
  
## 使用例  
 次の [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] コードは、簡単なコンテンツを含む <xref:System.Windows.Controls.RichTextBox> コントロールを記述しています。  
  
 [!code-xml[RichTextBoxSnippets#_RTB_XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml#_rtb_xaml)]  
  
## 使用例  
 次のコードでは、引数として <xref:System.Windows.Controls.RichTextBox> を受け取り、<xref:System.Windows.Controls.RichTextBox> のプレーン テキスト コンテンツを表す文字列を返すメソッドを実装します。  
  
 このメソッドは、抽出するコンテンツの範囲を示す <xref:System.Windows.Documents.FlowDocument.ContentStart%2A> および <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> を使用して、<xref:System.Windows.Controls.RichTextBox> のコンテンツから新しい <xref:System.Windows.Documents.TextRange> を作成します。  <xref:System.Windows.Documents.FlowDocument.ContentStart%2A> プロパティと <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> プロパティはそれぞれ <xref:System.Windows.Documents.TextPointer> を返し、<xref:System.Windows.Controls.RichTextBox> のコンテンツを表す基の FlowDocument でアクセスできます。  <xref:System.Windows.Documents.TextRange> は Text プロパティを提供し、<xref:System.Windows.Documents.TextRange> のプレーン テキスト部分を文字列として返します。  
  
 [!code-csharp[RichTextBoxSnippets#_RTB_StringFrom](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml.cs#_rtb_stringfrom)]
 [!code-vb[RichTextBoxSnippets#_RTB_StringFrom](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxSnippets/visualbasic/window1.xaml.vb#_rtb_stringfrom)]  
  
## 参照  
 [RichTextBox の概要](../../../../docs/framework/wpf/controls/richtextbox-overview.md)   
 [TextBox の概要](../../../../docs/framework/wpf/controls/textbox-overview.md)