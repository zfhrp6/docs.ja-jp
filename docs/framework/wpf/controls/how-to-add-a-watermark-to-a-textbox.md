---
title: "方法: TextBox にウォーターマークを追加する | Microsoft Docs"
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
  - "背景イメージを使用して TextBox の操作性を高める [WPF]"
  - "表示 (ユーザー入力を支援するためにテキスト ボックス内に背景イメージを) [WPF]"
ms.assetid: df89bdd8-a0fb-45e0-b312-dd53332d01a8
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法: TextBox にウォーターマークを追加する
<xref:System.Windows.Controls.TextBox> 内に説明の背景イメージを表示することによって <xref:System.Windows.Controls.TextBox> の操作性を高める方法を次の例に示します。この背景イメージは、ユーザーがテキストを入力するまで表示され、入力が行われた時点で削除されます。  また、背景イメージは、ユーザーが入力を削除すると、再び復元されます。  次の図を参照してください。  
  
 ![背景イメージを含む TextBox](../../../../docs/framework/wpf/controls/media/editing-textbox-using-background-image.png "Editing\_TextBox\_using\_background\_image")  
  
> [!NOTE]
>  この例では、<xref:System.Windows.Controls.TextBox> の <xref:System.Windows.Controls.TextBox.Text%2A> プロパティを操作するのではなく、背景イメージが使用されています。それは、背景イメージがデータ バインディングに干渉しないためです。  
  
## 使用例  
 [!code-xml[TextBoxMiscSnippets_snip#TextBoxBackgroundExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml#textboxbackgroundexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml.cs#textboxbackgroundcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/textbox_with_background_image.xaml.vb#textboxbackgroundcodeexamplewholepage)]  
  
## 参照  
 [TextBox の概要](../../../../docs/framework/wpf/controls/textbox-overview.md)   
 [RichTextBox の概要](../../../../docs/framework/wpf/controls/richtextbox-overview.md)