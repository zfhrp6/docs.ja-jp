---
title: "ToolStripContainer コントロールの概要 | Microsoft Docs"
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
  - "ToolStripContainer"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "ツール バー [Windows フォーム], ビルトイン ラフティング"
  - "ToolStripContainer コントロール [Windows フォーム], ToolStripContainer コントロールの概要"
ms.assetid: c7d63bff-64e2-4a63-bd89-d31bc96dacb8
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# ToolStripContainer コントロールの概要
<xref:System.Windows.Forms.ToolStripContainer> には、<xref:System.Windows.Forms.ToolStrip>、<xref:System.Windows.Forms.MenuStrip>、および <xref:System.Windows.Forms.StatusStrip> の各コントロールの配置およびラフティングのためのパネルが、上下左右のそれぞれの側にあります。  複数の <xref:System.Windows.Forms.ToolStrip> コントロールを左右の <xref:System.Windows.Forms.ToolStripContainer> に配置すると、コントロールは垂直方向に積み重ねられます。  上または下の <xref:System.Windows.Forms.ToolStripContainer> に配置すると、コントロールは水平方向に積み重ねられます。  <xref:System.Windows.Forms.ToolStripContainer> の中央の <xref:System.Windows.Forms.ToolStripContentPanel> を使用すると、従来のコントロールをフォーム上に配置できます。  
  
 すべての <xref:System.Windows.Forms.ToolStripContainer> コントロールは、デザイン時に直接選択して削除できます。  <xref:System.Windows.Forms.ToolStripContainer> の各パネルは展開および折りたたみが可能で、内部のコントロールに合わせてサイズ調整されます。  
  
### ToolStripContainer の重要なメンバー  
  
|名前|Description|  
|--------|-----------------|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanel%2A>|<xref:System.Windows.Forms.ToolStripContainer> の下側パネルを取得します。|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanelVisible%2A>|<xref:System.Windows.Forms.ToolStripContainer> の下パネルが表示されるかどうかを示す値を取得または設定します。|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanel%2A>|<xref:System.Windows.Forms.ToolStripContainer> の左パネルを取得します。|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanelVisible%2A>|<xref:System.Windows.Forms.ToolStripContainer> の左パネルが表示されるかどうかを示す値を取得または設定します。|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanel%2A>|<xref:System.Windows.Forms.ToolStripContainer> の右パネルを取得します。|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanelVisible%2A>|<xref:System.Windows.Forms.ToolStripContainer> の右パネルが表示されるかどうかを示す値を取得または設定します。|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A>|<xref:System.Windows.Forms.ToolStripContainer> の上パネルを取得します。|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanelVisible%2A>|<xref:System.Windows.Forms.ToolStripContainer> の上パネルが表示されるかどうかを示す値を取得または設定します。|  
  
## 参照  
 <xref:System.Windows.Forms.ToolStripContainer>   
 <xref:System.Windows.Forms.ToolStripContentPanel>