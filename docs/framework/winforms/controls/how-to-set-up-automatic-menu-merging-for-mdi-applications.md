---
title: "方法 : MDI アプリケーションでメニューの自動マージを設定する | Microsoft Docs"
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
  - "MenuStrip, マージ"
  - "マージ, 自動メニュー"
ms.assetid: 55e32cad-1141-4a56-aa33-d9543ca3d393
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法 : MDI アプリケーションでメニューの自動マージを設定する
ここでは、<xref:System.Windows.Forms.MenuStrip> を使用して、マルチ ドキュメント インターフェイス \(MDI\) アプリケーションで自動マージを設定する基本的な手順を説明します。  
  
### メニューの自動マージを設定するには  
  
1.  <xref:System.Windows.Forms.Form.IsMdiContainer%2A> プロパティを `true` に設定して、MDI 親フォームを作成します。  
  
2.  MDI 親フォームに <xref:System.Windows.Forms.MenuStrip> を追加し、<xref:System.Windows.Forms.Form.MainMenuStrip%2A> プロパティをその <xref:System.Windows.Forms.MenuStrip> に設定します。  
  
3.  MDI 子フォームを作成し、その <xref:System.Windows.Forms.Form.MdiParent%2A> プロパティを親フォームの名前に設定します。  
  
4.  MDI 子フォームに <xref:System.Windows.Forms.MenuStrip> を追加します。  
  
5.  子フォームで、<xref:System.Windows.Forms.MenuStrip> の <xref:System.Windows.Forms.ToolStripItem.Visible%2A> プロパティを `false` に設定します。  
  
6.  子フォームがアクティブ化されたときに親フォームの <xref:System.Windows.Forms.MenuStrip> にマージするメニュー項目を子フォームの <xref:System.Windows.Forms.MenuStrip> に追加します。  
  
7.  子フォームの <xref:System.Windows.Forms.MenuStrip> のメニュー項目で <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> プロパティを使用して、各項目を親フォームにマージする方法を制御します。  
  
## 参照  
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ToolStripMenuItem>   
 [MenuStrip コントロールの概要](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)