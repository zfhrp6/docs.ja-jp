---
title: "方法 : Windows フォーム内で実行時に ToolStrip 項目を並べ替えできるようにする | Microsoft Docs"
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
  - "AllowItemReorder プロパティ"
  - "例 [Windows フォーム], ツール バー"
  - "ツール バー [Windows フォーム], 再整列 (コントロールを)"
  - "ToolStrip コントロール [Windows フォーム], 例"
  - "ToolStrip コントロール [Windows フォーム], 並べ替え (項目を)"
ms.assetid: 8480b69a-379f-4dc2-8dcf-365ed93692b2
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : Windows フォーム内で実行時に ToolStrip 項目を並べ替えできるようにする
ユーザーが <xref:System.Windows.Forms.ToolStrip> で <xref:System.Windows.Forms.ToolStripItem> コントロールを再整列できるようにできます。  
  
### 実行時での ToolStripItem の再整列を有効にするには  
  
-   <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> プロパティを `true` に設定します。  既定では、<xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> は `false` に設定されています。  
  
     実行時には、ユーザーは Alt キーを押したままマウスの左ボタンをクリックして <xref:System.Windows.Forms.ToolStripItem> を <xref:System.Windows.Forms.ToolStrip> 上の別の場所にドラッグします。  
  
    ```vb  
    toolStrip1.AllowItemReorder = True  
  
    ```  
  
    ```csharp  
    toolStrip1.AllowItemReorder = true;  
  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>   
 [ToolStrip コントロールの概要](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)   
 [ToolStrip コントロールのアーキテクチャ](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)   
 [ToolStrip テクノロジの概要](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)