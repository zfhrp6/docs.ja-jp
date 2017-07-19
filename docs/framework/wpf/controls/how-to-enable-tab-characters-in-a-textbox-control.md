---
title: "方法 : TextBox コントロールでタブ文字を有効にする | Microsoft Docs"
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
  - "タブ文字, 有効化"
  - "TextBox コントロール, 有効化 (タブ文字を)"
ms.assetid: 14b1b064-61f7-4958-be63-88d85b868d03
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : TextBox コントロールでタブ文字を有効にする
<xref:System.Windows.Controls.TextBox> コントロールの通常入力としてタブ文字を受け入れられるようにする方法を次の例に示します。  
  
## 使用例  
 <xref:System.Windows.Controls.TextBox> コントロールの入力としてタブ文字を受け入れられるようにするには、<xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsTab%2A> 属性を **true** に設定します。  
  
 [!code-xml[TextBox_EnablingTab#_AcceptsTab](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_EnablingTab/CS/Window1.xaml#_acceptstab)]  
  
## 参照  
 [TextBox の概要](../../../../docs/framework/wpf/controls/textbox-overview.md)   
 [RichTextBox の概要](../../../../docs/framework/wpf/controls/richtextbox-overview.md)