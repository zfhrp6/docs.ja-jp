---
title: "方法 : メニュー項目を ContextMenuStrip に追加する | Microsoft Docs"
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
  - "コンテキスト メニュー, 追加 (メニュー項目を)"
  - "ContextMenuStrips, 追加 (メニュー項目を)"
  - "ショートカット メニュー, 追加 (アイテムを)"
ms.assetid: 1ec14776-3ea2-4752-bd22-4fae0fd19e1a
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : メニュー項目を ContextMenuStrip に追加する
<xref:System.Windows.Forms.ContextMenuStrip> には、単一のメニュー項目を追加できます。同時に複数のメニュー項目を追加することもできます。  
  
### 単一のメニュー項目を ContextMenuStrip に追加するには  
  
-   単一のメニュー項目を <xref:System.Windows.Forms.ContextMenuStrip> に追加するには、<xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> メソッドを使用します。  
  
     \[Visual Basic\]  
  
    ```  
    Me.contextMenuStrip1.Items.Add(Me.toolStripMenuItem1)  
    ```  
  
    ```csharp  
    this.contextMenuStrip1.Items.Add(toolStripMenuItem1);  
    ```  
  
### 複数のメニュー項目を ContextMenuStrip に追加するには  
  
-   複数のメニュー項目を <xref:System.Windows.Forms.ContextMenuStrip> に追加するには、<xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> メソッドを使用します。  
  
     \[Visual Basic\]  
  
    ```  
    Me.contextMenuStrip1.Items.AddRange(New _  
       System.Windows.Forms.ToolStripItem() {Me.toolStripMenuItem1, _  
          Me.toolStripMenuItem2})  
    ```  
  
    ```csharp  
    this.contextMenuStrip1.Items.AddRange(new   
       System.Windows.Forms.ToolStripItem[] {  
          this.toolStripMenuItem1, this.toolStripMenuItem2});  
    ```  
  
## 参照  
 [ContextMenuStrip コントロール](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)