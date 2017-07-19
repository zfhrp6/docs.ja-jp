---
title: "方法 : Windows フォームの ToolStrip オーバーフローを管理する | Microsoft Docs"
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
  - "CanOverflow プロパティ"
  - "例 [Windows フォーム], ツール バー"
  - "Overflow プロパティ"
  - "ツール バー [Windows フォーム], 管理 (オーバーフローを)"
  - "ToolStrip コントロール [Windows フォーム], 管理 (オーバーフローを)"
ms.assetid: fa10e0ad-4cbf-4c0d-9082-359c2f855d4e
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : Windows フォームの ToolStrip オーバーフローを管理する
<xref:System.Windows.Forms.ToolStrip> コントロールのすべての項目が割り当てられた領域に収まらないときは、その <xref:System.Windows.Forms.ToolStrip> に対してオーバーフロー機能を有効にして、特定の <xref:System.Windows.Forms.ToolStripItem> のオーバーフロー動作を指定できます。  
  
 フォームの現在のサイズを前提に <xref:System.Windows.Forms.ToolStrip> に割り当てられた領域を超える領域を必要とする <xref:System.Windows.Forms.ToolStripItem> を追加すると、<xref:System.Windows.Forms.ToolStrip> 上に <xref:System.Windows.Forms.ToolStripOverflowButton> が自動的に表示されます。  <xref:System.Windows.Forms.ToolStripOverflowButton> が表示されると、オーバーフローが有効になった項目がオーバーフローのドロップダウン メニューに移動します。  これによって、さまざまなフォーム サイズに合うように <xref:System.Windows.Forms.ToolStrip> 項目を調整する方法をカスタマイズし、優先順位を付けることができます。  また、<xref:System.Windows.Forms.ToolStripItem.Placement%2A> プロパティと <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=fullName> プロパティ、および <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> イベントを使用することによって、オーバーフロー状態になったときの項目の外観を変更することもできます。  デザイン時または実行時にフォームを拡大すると、より多くの <xref:System.Windows.Forms.ToolStripItem> がメイン <xref:System.Windows.Forms.ToolStrip> に表示され、フォームのサイズを縮小しない限り <xref:System.Windows.Forms.ToolStripOverflowButton> は表示されないことがあります。  
  
### ToolStrip コントロールのオーバーフローを有効にするには  
  
-   <xref:System.Windows.Forms.ToolStrip> の <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> プロパティが `false` に設定されていないことを確認します。  既定値は、`True` です。  
  
     <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> が `True` \(既定値\) の場合、<xref:System.Windows.Forms.ToolStripItem> の内容が水平の <xref:System.Windows.Forms.ToolStrip> の幅または垂直の <xref:System.Windows.Forms.ToolStrip> の高さを超えると、<xref:System.Windows.Forms.ToolStripItem> がオーバーフローのドロップダウン メニューに送られます。  
  
### 特定の ToolStripItem のオーバーフロー動作を指定するには  
  
-   <xref:System.Windows.Forms.ToolStripItem> の <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> プロパティを任意の値に設定します。  設定できる値は、`Always`、`Never`、および `AsNeeded` です。  既定値は `AsNeeded` です。  
  
    ```vb  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never  
  
    ```  
  
    ```csharp  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never;  
  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.ToolStripOverflowButton>   
 <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>   
 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>   
 [ToolStrip コントロールの概要](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)   
 [ToolStrip コントロールのアーキテクチャ](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)   
 [ToolStrip テクノロジの概要](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)