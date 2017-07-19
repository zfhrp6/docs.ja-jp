---
title: "方法 : Windows フォーム内の ToolStrip 項目の間隔と配置を変更する | Microsoft Docs"
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
  - "ツール バー [Windows フォーム], 配置 (項目を)"
  - "ToolStrip コントロール [Windows フォーム], 配置 (項目を)"
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : Windows フォーム内の ToolStrip 項目の間隔と配置を変更する
<xref:System.Windows.Forms.ToolStrip> コントロールは、サイズ調整、<xref:System.Windows.Forms.ToolStripItem> コントロールの間隔、<xref:System.Windows.Forms.ToolStrip> 上へのコントロールの配置、および <xref:System.Windows.Forms.ToolStrip> に相対的なコントロールの間隔などのレイアウト機能を完全にサポートします。  
  
 <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> プロパティの既定値は `true` であるため、<xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> プロパティを `false` に設定しない限り、コントロールのサイズは自動的に調整されます。  
  
### ToolStripItem のサイズを手動で調整するには  
  
1.  関連するコントロールの <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> プロパティを `false` に設定します。  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
  
    ```  
  
2.  関連する <xref:System.Windows.Forms.ToolStripItem> の <xref:System.Windows.Forms.ToolStripItem.Size%2A> プロパティを任意の値に設定します。  
  
### ToolStripItem の間隔を設定するには  
  
1.  関連するコントロールの <xref:System.Windows.Forms.ToolStripItem.Margin%2A> プロパティに任意の値 \(ピクセル単位\) を挿入します。  
  
     <xref:System.Windows.Forms.ToolStripItem.Margin%2A> プロパティの値で、項目と隣接する項目の間隔 \(順に左、上、右、および下\) を指定します。  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding   
        (3, 0, 3, 0);  
  
    ```  
  
### ToolStripItem を ToolStrip の右側に配置するには  
  
1.  関連するコントロールの <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> プロパティを <xref:System.Windows.Forms.ToolStripItemAlignment> に設定します。  既定では、<xref:System.Windows.Forms.ToolStripItem.Alignment%2A> は <xref:System.Windows.Forms.ToolStripItemAlignment> に設定され、コントロールは <xref:System.Windows.Forms.ToolStrip> の左側に配置されます。  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =   
        System.Windows.Forms.ToolStripItemAlignment.Right;  
  
    ```  
  
### ToolStrip 上の ToolStrip 項目を並べ替えるには  
  
-   <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> プロパティを任意の <xref:System.Windows.Forms.ToolStripLayoutStyle> の値に設定します。  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =   
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.Control.Layout>   
 <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>   
 <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>   
 <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>   
 <xref:System.Windows.Forms.ToolStripItem.Placement%2A>   
 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>   
 [ToolStrip コントロールの概要](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)   
 [ToolStrip コントロールのアーキテクチャ](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)   
 [ToolStrip テクノロジの概要](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)