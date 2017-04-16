---
title: "方法 : マウス ポインターが ToolStripItem 上にあることを検出する | Microsoft Docs"
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
  - "マウス, 検出 (ツール バーでの動きを)"
  - "ツール バー [Windows フォーム], 検出 (マウスの動きを)"
  - "ToolStrip コントロール [Windows フォーム], 検出 (マウスの動きを)"
  - "ToolStripItem クラス, 検出 (マウスの動きを)"
ms.assetid: d38b5082-aba7-4f6c-841b-bd9714e307fd
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : マウス ポインターが ToolStripItem 上にあることを検出する
マウス ポインターが <xref:System.Windows.Forms.ToolStripItem> 上にあることを検出するには、次の手順に従ってください。  
  
### ポインターが ToolStripItem 上にあることを検出するには  
  
-   <xref:System.Windows.Forms.ToolStripItem.CanSelect%2A> が `true` である項目に対して <xref:System.Windows.Forms.ToolStripItem.Selected%2A> プロパティを使用します。  
  
     これによって、<xref:System.Windows.Forms.ToolStripItem.MouseEnter> イベントと <xref:System.Windows.Forms.ToolStripItem.MouseLeave> イベントを同期する必要がなくなります。  
  
## 参照  
 <xref:System.Windows.Forms.ToolStripItem>   
 <xref:System.Windows.Forms.ToolStripItem.Selected%2A>   
 [ToolStrip コントロールの概要](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)