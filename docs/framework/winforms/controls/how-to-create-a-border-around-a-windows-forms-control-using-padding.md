---
title: "方法 : 埋め込みを使用して Windows フォーム コントロールの周囲に境界線を作成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "コントロール [Windows フォーム], Margin プロパティ"
  - "コントロール [Windows フォーム], アウトライン"
  - "コントロール [Windows フォーム], Padding プロパティ"
  - "Margin プロパティ [Windows フォーム]"
  - "マージン"
  - "マージン, Windows フォーム"
  - "Padding プロパティ [Windows フォーム]"
  - "埋め込み, Windows フォーム"
ms.assetid: bac7ed4d-a163-4259-98bd-155a36345890
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法 : 埋め込みを使用して Windows フォーム コントロールの周囲に境界線を作成する
<xref:System.Windows.Forms.RichTextBox> コントロールの周囲に境界線つまり外枠を作成する方法を次のコード例に示します。  この例では、<xref:System.Windows.Forms.Panel> コントロールの <xref:System.Windows.Forms.Padding> プロパティの値を 5 に設定し、子の <xref:System.Windows.Forms.RichTextBox> コントロールの <xref:System.Windows.Forms.Control.Dock%2A> プロパティを <xref:System.Windows.Forms.DockStyle> に設定します。  <xref:System.Windows.Forms.Panel> コントロールの <xref:System.Windows.Forms.Control.BackColor%2A> は、<xref:System.Drawing.Color.Blue%2A> に設定します。これによって <xref:System.Windows.Forms.RichTextBox> コントロールの周囲に青い境界線が作成されます。  
  
## 使用例  
 [!code-csharp[System.Windows.Forms.Padding#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Padding/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.Padding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Padding/VB/Form1.vb#1)]  
  
## 参照  
 <xref:System.Windows.Forms.Padding>   
 [Windows フォーム コントロールでのマージンと埋め込み](../../../../docs/framework/winforms/controls/margin-and-padding-in-windows-forms-controls.md)