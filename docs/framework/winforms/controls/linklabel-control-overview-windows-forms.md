---
title: "LinkLabel コントロールの概要 (Windows フォーム) | Microsoft Docs"
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
  - "LinkLabel"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Label コントロール [Windows フォーム], Label コントロールの概要"
  - "LinkLabel コントロール [Windows フォーム], LinkLabel コントロールの概要"
  - "リンク, LinkLabel コントロール"
ms.assetid: 9e248549-10ca-43a3-bb5e-60f583d369f1
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# LinkLabel コントロールの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.LinkLabel> コントロールを使用すると、Web スタイルのリンクを Windows フォーム アプリケーションに追加できます。  <xref:System.Windows.Forms.LinkLabel> コントロールは、<xref:System.Windows.Forms.Label> コントロールを使用できるすべての項目に使用できます。テキストの一部をファイル、フォルダー、または Web ページへのリンクとして設定することもできます。  
  
## LinkLabel コントロールで可能なこと  
 <xref:System.Windows.Forms.Label> コントロールには、<xref:System.Windows.Forms.LinkLabel> コントロールのすべてのプロパティ、メソッド、およびイベントに加えて、ハイパーリンクとリンクの色を設定するプロパティがあります。  <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> プロパティでは、リンクをアクティブにするテキストの領域を設定します。  <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> プロパティ、<xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> プロパティ、および <xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A> プロパティでは、リンクの色を設定します。  <xref:System.Windows.Forms.LinkLabel.LinkClicked> イベントでは、リンク テキストを選択したときの動作を指定します。  
  
 <xref:System.Windows.Forms.LinkLabel> コントロールの最も単純な用途は <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> プロパティを使用した単一リンクの表示ですが、<xref:System.Windows.Forms.LinkLabel.Links%2A> プロパティを使用することによって複数のハイパーリンクを表示することもできます。  <xref:System.Windows.Forms.LinkLabel.Links%2A> プロパティを使用すると、リンクのコレクションにアクセスできます。  また、各 <xref:System.Windows.Forms.LinkLabel.Link> オブジェクトの <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> プロパティ内にデータを指定することもできます。  <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> プロパティの値は、表示するファイルの場所や Web サイトのアドレスを格納するために使用できます。  
  
## 参照  
 <xref:System.Windows.Forms.LinkLabel>   
 [Label コントロールの概要](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)   
 [方法 : Windows フォーム LinkLabel コントロールでオブジェクトまたは Web ページにリンクする](../../../../docs/framework/winforms/controls/link-to-an-object-or-web-page-with-wf-linklabel-control.md)   
 [方法 : Windows フォーム LinkLabel コントロールの表示形式を変更する](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)