---
title: "プログラムによる RichTextBox での選択の変更 | Microsoft Docs"
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
  - "変更 (RichTextBox での選択を) [WPF]"
  - "変更 (テキスト ボックスでの選択を) [WPF]"
ms.assetid: f1213205-1ad7-4cd2-b115-460173cc5aa3
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# プログラムによる RichTextBox での選択の変更
この例では、<xref:System.Windows.Controls.RichTextBox> での現在の選択をプログラムで変更する方法を示します。  この選択は、ユーザーがユーザー インターフェイスを使用してコンテンツを選択することと同じです。  
  
## 使用例  
 次の [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] コードは、簡単なコンテンツを含む <xref:System.Windows.Controls.RichTextBox> コントロールを記述しています。  
  
 [!code-xml[RichTextBoxMiscSnippets_snip#ChangeSelectionProgrammaticalyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/ChangeSelectionProgrammaticaly.xaml#changeselectionprogrammaticalyexamplewholepage)]  
  
## 使用例  
 次のコードは、ユーザーが <xref:System.Windows.Controls.RichTextBox> の内部をクリックしたときに任意のテキストをプログラムで選択します。  
  
 [!code-csharp[RichTextBoxMiscSnippets_snip#ChangeSelectionProgrammaticalyCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/ChangeSelectionProgrammaticaly.xaml.cs#changeselectionprogrammaticalycodeexamplewholepage)]
 [!code-vb[RichTextBoxMiscSnippets_snip#ChangeSelectionProgrammaticalyCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/ChangeSelectionProgrammaticaly.xaml.vb#changeselectionprogrammaticalycodeexamplewholepage)]  
  
## 参照  
 [RichTextBox の概要](../../../../docs/framework/wpf/controls/richtextbox-overview.md)   
 [TextBox の概要](../../../../docs/framework/wpf/controls/textbox-overview.md)