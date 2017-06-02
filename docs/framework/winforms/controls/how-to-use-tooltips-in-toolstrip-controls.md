---
title: "方法 : ToolStrip コントロールにツールヒントを使用する | Microsoft Docs"
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
  - "ツール バー [Windows フォーム], 追加 (ツールヒントを)"
  - "ToolStrip コントロール [Windows フォーム], 追加 (ツールヒントを)"
  - "ツールヒント [Windows フォーム], 追加"
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : ToolStrip コントロールにツールヒントを使用する
<xref:System.Windows.Forms.ToolStrip> コントロールの <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> プロパティに `true` を設定することで、必要なコントロールに対して <xref:System.Windows.Forms.ToolTip> を表示できます。  
  
### ツールヒントを表示するには  
  
-   コントロールの <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> プロパティを `true` に設定します。  
  
     <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=fullName> の既定値は、`true` です。また、<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=fullName> と <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=fullName> の既定値は、`false` です。  
  
### ToolStripButton のツールヒント テキストに ToolTipText プロパティを使用するには  
  
1.  ボタンの <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> プロパティを `true` に設定します。  
  
2.  ボタンの <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=fullName> プロパティを `false` に設定します。  
  
     <xref:System.Windows.Forms.ToolStripButton>、<xref:System.Windows.Forms.ToolStripDropDownButton>、および <xref:System.Windows.Forms.ToolStripSplitButton> の `AutoToolTip` プロパティは、既定では `true` です。  
  
     <xref:System.Windows.Forms.ToolStripButton> は、既定では、<xref:System.Windows.Forms.ToolTip> テキストに対してその `Text` プロパティを使用します。  <xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolTip> にカスタム テキストを表示するには、この手順に従ってください。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStripItemDisplayStyle> を <xref:System.Windows.Forms.ToolStripItemDisplayStyle> または <xref:System.Windows.Forms.ToolStripItemDisplayStyle> に設定すると、ボタンにテキストは表示されませんが、ツールヒントは変わらず表示されます。  
  
## 参照  
 <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>   
 <xref:System.Windows.Forms.ToolStripButton>   
 <xref:System.Windows.Forms.ToolStripDropDownButton>   
 <xref:System.Windows.Forms.ToolStripSplitButton>   
 [ToolStrip コントロールの概要](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)