---
title: "方法 : Windows フォーム内の ToolStrip テキストとイメージの外観を変更する | Microsoft Docs"
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
  - "例 [Windows フォーム], ツール バー"
  - "ツール バー [Windows フォーム], 外観"
  - "ツール バー [Windows フォーム], イメージ"
  - "ツール バー [Windows フォーム], テキスト"
  - "ToolStrip コントロール [Windows フォーム], 外観"
  - "ToolStrip コントロール [Windows フォーム], イメージ"
  - "ToolStrip コントロール [Windows フォーム], テキスト"
ms.assetid: d62dc9d1-2edd-4dfa-aed7-1335d6e13d86
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : Windows フォーム内の ToolStrip テキストとイメージの外観を変更する
テキストとイメージを <xref:System.Windows.Forms.ToolStripItem> に表示するかどうか、また、テキスト、イメージ、および <xref:System.Windows.Forms.ToolStrip> の相対位置を制御できます。  
  
### ToolStripItem に表示するものを定義するには  
  
-   <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> プロパティに目的の値を設定します。  設定できる値は、`Image`、`ImageAndText`、`None`、および `Text` です。  既定値は、`ImageAndText` です。  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
  
    ```  
  
### ToolStripItem 上でテキストを揃えるには  
  
-   <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> プロパティに目的の値を設定します。  設定できる値は、Top、Middle、Bottom と Left、Center、Right の組み合わせです。  既定値は、`MiddleCenter` です。  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
  
    ```  
  
### ToolStripItem 上でイメージを揃えるには  
  
-   <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> プロパティに目的の値を設定します。  設定できる値は、Top、Middle、Bottom と Left、Center、Right の組み合わせです。  既定値は、`MiddleLeft` です。  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
  
    ```  
  
### ToolStripItem のテキストとイメージの相対的な表示位置を定義するには  
  
-   <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> プロパティに目的の値を設定します。  設定できる値は、`ImageAboveText`、`ImageBeforeText`、`Overlay`、`TextAboveImage`、および `TextBeforeImage` です。  既定値は、`ImageBeforeText` です。  
  
    ```vb  
    ToolStripButton1.TextImageRelation = _  
        System.Windows.Forms.TextImageRelation.ImageAboveText  
  
    ```  
  
    ```csharp  
    toolStripButton1.TextImageRelation = System.Windows.Forms.TextImageRelation.ImageAboveText;  
  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.ToolStrip>   
 [ToolStrip コントロールの概要](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)   
 [ToolStrip コントロールのアーキテクチャ](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)   
 [ToolStrip テクノロジの概要](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)