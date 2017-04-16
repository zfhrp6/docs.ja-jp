---
title: "ToolStripPanel コントロールの概要 | Microsoft Docs"
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
  - "ToolStripPanel"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "ツール バー [Windows フォーム]"
  - "ToolStripPanel コントロール [Windows フォーム], ToolStripPanel コントロールの概要"
ms.assetid: ce54a60c-5eba-4b4c-bd77-cf0748a666cc
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# ToolStripPanel コントロールの概要
<xref:System.Windows.Forms.ToolStripPanel> は、<xref:System.Windows.Forms.ToolStrip>、<xref:System.Windows.Forms.MenuStrip>、および <xref:System.Windows.Forms.StatusStrip> の各コントロールを配置およびラフティングするための単一の領域です。  <xref:System.Windows.Forms.ToolStripPanel> の <xref:System.Windows.Forms.ToolStripPanelRow.Orientation%2A> に基づいて、複数の <xref:System.Windows.Forms.ToolStrip> コントロールが垂直または水平に並びます。  
  
### ToolStripPanel の重要なメンバー  
  
|名前|Description|  
|--------|-----------------|  
|<xref:System.Windows.Forms.ToolStripPanel.Orientation%2A>|<xref:System.Windows.Forms.ToolStripPanel> の向きが水平方向であるか垂直方向であるかを示す値を取得または設定します。|  
|<xref:System.Windows.Forms.ToolStripPanel.Renderer%2A>|<xref:System.Windows.Forms.ToolStripPanel> の外観のカスタマイズに使用する <xref:System.Windows.Forms.ToolStripRenderer> を取得または設定します。|  
|<xref:System.Windows.Forms.ToolStripPanel.RenderMode%2A>|<xref:System.Windows.Forms.ToolStripPanel> に適用される描画スタイルを取得または設定します。|  
|<xref:System.Windows.Forms.ToolStripPanel.RowMargin%2A>|<xref:System.Windows.Forms.ToolStripPanelRow> と <xref:System.Windows.Forms.ToolStripPanel> の間隔をピクセル単位で取得または設定します。|  
|<xref:System.Windows.Forms.ToolStripPanel.Rows%2A>|この <xref:System.Windows.Forms.ToolStripPanel> の <xref:System.Windows.Forms.ToolStripPanelRow> を取得します。|  
|<xref:System.Windows.Forms.ToolStripPanel.Join%2A>|<xref:System.Windows.Forms.ToolStrip> を <xref:System.Windows.Forms.ToolStripPanel> に追加します。|  
  
## 参照  
 <xref:System.Windows.Forms.ToolStripContainer>   
 <xref:System.Windows.Forms.ToolStripContentPanel>   
 [ToolStrip Sample](http://msdn.microsoft.com/ja-jp/b7352439-184a-4a3a-b2ad-07465d3af9ed)