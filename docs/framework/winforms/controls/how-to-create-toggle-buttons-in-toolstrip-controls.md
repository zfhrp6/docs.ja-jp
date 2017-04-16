---
title: "方法 : ToolStrip コントロールにトグル ボタンを作成する | Microsoft Docs"
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
  - "トグル ボタン, 作成"
  - "ToolStrip コントロール [Windows フォーム], 作成 (トグル ボタンを)"
ms.assetid: d9c197df-4c65-43f2-beee-b68b52b2befc
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : ToolStrip コントロールにトグル ボタンを作成する
ユーザーがトグル ボタンをクリックすると、ボタンはくぼんだように表示され、ユーザーがボタンをもう一度クリックするまでくぼんだ外観を保持します。  
  
### 切り替えのある ToolStripButton を作成するには  
  
-   次のようなコードを使用します。  このコードでは、フォームに <xref:System.Windows.Forms.ToolStrip> コントロールが含まれていること、およびその <xref:System.Windows.Forms.ToolStrip.Items%2A> コレクションに `toolStripButton1` という名前の <xref:System.Windows.Forms.ToolStripButton> が含まれていることを前提としています。  また、`toolStripButton1_CheckedChanged` という名前のイベント ハンドラーがあることも前提としています。  
  
     \[Visual Basic\]  
  
    ```  
    toolStripButton1.CheckOnClick = True  
    toolStripButton1.CheckedChanged AddressOf _  
    EventHandler(toolStripButton1_CheckedChanged);  
  
    ```  
  
     \[C\#\]  
  
    ```  
    toolStripButton1.CheckOnClick = true;  
    toolStripButton1.CheckedChanged += new _  
    EventHandler(toolStripButton1_CheckedChanged);  
  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.ToolStripButton>   
 [ToolStrip コントロールの概要](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)