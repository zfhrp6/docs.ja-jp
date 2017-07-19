---
title: "RichTextBox コントロールの概要 (Windows フォーム) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RichTextBox"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "RichTextBox コントロール [Windows フォーム], RichTextBox コントロールの概要"
  - "テキスト ボックス, テキスト ボックスの概要"
ms.assetid: 95081194-3dd4-4b84-9545-dd373e491eca
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# RichTextBox コントロールの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.RichTextBox> コントロールは、書式付きテキストの表示、入力、および操作を行うために使用されます。  <xref:System.Windows.Forms.RichTextBox> コントロールは、<xref:System.Windows.Forms.TextBox> コントロールのすべての機能を備えている他、フォント、色、およびリンクを表示したり、ファイルからテキストや埋め込みイメージを読み込んだり、指定した文字を検索したりできます。  通常、<xref:System.Windows.Forms.RichTextBox> コントロールは、Microsoft Word などのワード プロセッシング アプリケーションと同様のテキスト操作および表示機能を提供します。  <xref:System.Windows.Forms.TextBox> コントロールと同様に、<xref:System.Windows.Forms.RichTextBox> コントロールはスクロール バーを表示できます。ただし、<xref:System.Windows.Forms.TextBox> コントロールとは異なり、既定の設定では必要に応じて垂直スクロール バーと水平スクロール バーの両方が表示され、追加のスクロール バー設定もあります。  
  
## RichTextBox コントロールの操作  
 <xref:System.Windows.Forms.TextBox> コントロールと同様に、表示されるテキストは <xref:System.Windows.Forms.RichTextBox.Text%2A> プロパティによって設定されます。  <xref:System.Windows.Forms.RichTextBox> コントロールには、テキストの書式を指定する多くのプロパティがあります。  各プロパティの詳細については、「[方法 : Windows フォームの RichTextBox コントロールのフォント属性を設定する](../../../../docs/framework/winforms/controls/how-to-set-font-attributes-for-the-windows-forms-richtextbox-control.md)」と「[方法 : Windows フォームの RichTextBox コントロールを使用してインデント、ぶら下げインデント、および箇条書き段落を設定する](../../../../docs/framework/winforms/controls/set-indents-hanging-indents-bulleted-paragraphs-with-wf-richtextbox.md)」を参照してください。  ファイルを操作するために、<xref:System.Windows.Forms.RichTextBox.LoadFile%2A> メソッドおよび <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> メソッドを使用すると、プレーンテキスト、Unicode プレーンテキスト、リッチ テキスト形式 \(RTF\) などの複数のファイル形式を表示し、書き込むことができます。  使用できるファイル形式の一覧については、「[RichTextBoxStreamType 列挙](frlrfSystemWindowsFormsRichTextBoxStreamTypeClassTopic)」を参照してください。  <xref:System.Windows.Forms.RichTextBox.Find%2A> メソッドを使用すると、テキストの文字列や特定の文字を検索できます。  
  
 また、<xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> プロパティを `true` に設定し、<xref:System.Windows.Forms.RichTextBox.LinkClicked> イベントを処理するコードを記述することで、Web スタイルのリンクに <xref:System.Windows.Forms.RichTextBox> コントロールを使用することもできます。  詳細については、「[方法 : Windows フォームの RichTextBox コントロールを使用して Web スタイルのリンクを表示する](../../../../docs/framework/winforms/controls/how-to-display-web-style-links-with-the-windows-forms-richtextbox-control.md)」を参照してください。  コントロール内のテキストの一部またはすべてをユーザーが操作できないようにするには、<xref:System.Windows.Forms.RichTextBox.SelectionProtected%2A> プロパティを `true` に設定します。  
  
 <xref:System.Windows.Forms.RichTextBox> コントロール内のほとんどの編集操作は、<xref:System.Windows.Forms.TextBoxBase.Undo%2A> メソッドおよび <xref:System.Windows.Forms.RichTextBox.Redo%2A> メソッドを呼び出すと、元に戻したりやり直したりできます。  <xref:System.Windows.Forms.RichTextBox.CanRedo%2A> メソッドを使用すると、ユーザーが最後に元に戻した動作をコントロールに再び適用できるかどうかを決定できます。  
  
## 参照  
 <xref:System.Windows.Forms.RichTextBox>   
 [RichTextBox コントロール](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)   
 [TextBox コントロールの概要](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)