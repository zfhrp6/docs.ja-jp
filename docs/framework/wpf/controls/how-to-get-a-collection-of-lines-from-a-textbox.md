---
title: "方法 : TextBox から行のコレクションを取得する | Microsoft Docs"
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
  - "線, 取得 (コレクションを)"
  - "TextBox コントロール, 取得 (行のコレクションを)"
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法 : TextBox から行のコレクションを取得する
この例では、<xref:System.Windows.Controls.TextBox> からテキスト行のコレクションを取得する方法を示します。  
  
## 使用例  
 次の例は、<xref:System.Windows.Controls.TextBox> を引数とし、**TextBox** 内のテキスト行を含む <xref:System.Collections.Specialized.StringCollection> を返す単純なメソッドを示しています。  <xref:System.Windows.Controls.TextBox.LineCount%2A> プロパティは、**TextBox** 内の現在の行数を確認するために使用し、<xref:System.Windows.Controls.TextBox.GetLineText%2A> メソッドは、各行を抽出してそれを行のコレクションに追加するために使用します。  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## 参照  
 [TextBox の概要](../../../../docs/framework/wpf/controls/textbox-overview.md)   
 [RichTextBox の概要](../../../../docs/framework/wpf/controls/richtextbox-overview.md)