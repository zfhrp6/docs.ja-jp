---
title: "方法 : ContextMenuStrip のオープン イベントを処理する | Microsoft Docs"
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
  - "コンテキスト メニュー, イベント処理"
  - "ContextMenuStrip コントロール [Windows フォーム]"
  - "イベント処理, コンテキスト メニュー"
  - "ショートカット メニュー, イベント処理"
  - "ToolStrip コントロール [Windows フォーム]"
ms.assetid: b661b3dd-7815-4cc2-a1aa-a9a391ab3427
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法 : ContextMenuStrip のオープン イベントを処理する
<xref:System.Windows.Forms.ToolStripDropDown.Opening> イベントを処理することにより、<xref:System.Windows.Forms.ContextMenuStrip> コントロールの動作をカスタマイズできます。  
  
## 使用例  
 <xref:System.Windows.Forms.ToolStripDropDown.Opening> イベントを処理する方法を次のコード例に示します。  このイベント ハンドラーでは、<xref:System.Windows.Forms.ContextMenuStrip> コントロールに項目を動的に追加します。  完全なコード例については、「[方法 : ToolStrip の項目を動的に追加する](../../../../docs/framework/winforms/controls/how-to-add-toolstrip-items-dynamically.md)」を参照してください。  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#42)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#42)]  
  
 <xref:System.ComponentModel.CancelEventArgs.Cancel%2A?displayProperty=fullName> プロパティを `true` に設定して、メニューが開かないようにします。  
  
## 参照  
 <xref:System.Windows.Forms.ContextMenuStrip>   
 <xref:System.ComponentModel.CancelEventArgs.Cancel%2A>   
 <xref:System.Windows.Forms.ToolStripDropDown>   
 [ToolStrip コントロール](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)