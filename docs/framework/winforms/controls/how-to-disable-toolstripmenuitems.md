---
title: "方法 : ToolStripMenuItems を無効にする | Microsoft Docs"
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
  - "無効化 (メニュー項目を)"
  - "メニュー項目, 無効化"
  - "メニュー項目, 有効化"
  - "メニュー, 無効化 (メニュー項目を)"
  - "ToolStripMenuItem, 無効化"
  - "ToolStripMenuItem, 有効化"
ms.assetid: bcc1da84-50fd-41d2-8475-103b581d5654
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : ToolStripMenuItems を無効にする
ユーザーのアクティビティに応じてメニュー項目を有効および無効にすることによって、ユーザーが実行できるコマンドを制限したり、増やしたりできます。  メニュー項目は作成時に既定で有効になっていますが、これは <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> プロパティを介して調整できます。  このプロパティはデザイン時に **\[プロパティ\]** ウィンドウで操作できます。また、コード内で設定することによりプログラムで操作できます。  
  
### プログラムによって、メニュー項目を無効にするには  
  
-   メニュー項目のプロパティを設定するメソッド内で、コードを追加して <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> プロパティを `false` に設定します。  
  
    ```vb  
    MenuItem1.Enabled = False  
    ```  
  
    ```csharp  
    menuItem1.Enabled = false;  
    ```  
  
    ```cpp  
    menuItem1->Enabled = false;  
    ```  
  
    > [!TIP]
    >  メニュー内の最初の、つまりトップレベルのメニュー項目を無効にすると、そのメニューに含まれるすべてのメニュー項目が非表示になります。ただし、無効にはなりません。  同様に、サブメニュー項目を持つメニュー項目を無効にすると、サブメニュー項目が非表示になりますが、無効にはなりません。  指定したメニューのすべてのコマンドをユーザーが使用できない場合は、ユーザー インターフェイスを簡潔にするために、メニュー全体を非表示にし、無効にするようにプログラミングすることをお勧めします。  メニューを非表示にしただけの場合、ショートカット キーを使用してメニュー コマンドにアクセスできるため、メニューを非表示にして無効にし、さらにメニュー内のすべての項目とサブメニュー項目を無効にする必要があります。  トップレベルのメニュー項目の <xref:System.Windows.Forms.ToolStripItem.Visible%2A> プロパティを `false` に設定してメニュー全体を非表示にします。  
  
## 参照  
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ToolStripMenuItem>   
 [方法 : ToolStripMenuItems を非表示にする](../../../../docs/framework/winforms/controls/how-to-hide-toolstripmenuitems.md)   
 [MenuStrip コントロールの概要](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)