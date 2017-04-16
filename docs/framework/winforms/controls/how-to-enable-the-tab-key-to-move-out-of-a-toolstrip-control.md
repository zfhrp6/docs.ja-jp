---
title: "方法 : Tab キーで ToolStrip コントロールから移動できるようにする | Microsoft Docs"
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
  - "コントロール [Windows フォーム], 移動"
  - "TAB キー, 有効化"
  - "ToolStrip コントロール [Windows フォーム], 移動"
ms.assetid: 40f9e88b-09a3-428e-8da8-c00bb65079c6
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : Tab キーで ToolStrip コントロールから移動できるようにする
ユーザーが Tab キーを押して <xref:System.Windows.Forms.ToolStrip> からタブ オーダーの次のコントロールに移動できるようにするには、次の手順に従ってください。  
  
 ユーザーが Tab キーを最初に押すと、<xref:System.Windows.Forms.ToolStrip> がこれを受け入れます。ユーザーは方向キーで <xref:System.Windows.Forms.ToolStrip> 内の項目を選択できます。  ユーザーが Tab キーをもう一度押すと、タブ オーダーの次のコントロールに移動します。  
  
### ユーザーが Tab キーを押して ToolStrip から次のコントロールに移動できるようにするには  
  
-   <xref:System.Windows.Forms.ToolStrip> の <xref:System.Windows.Forms.ToolStrip.TabStop%2A> プロパティを `true` に設定します。  
  
## 参照  
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.ToolStrip.TabStop%2A>   
 [ToolStrip コントロールの概要](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)