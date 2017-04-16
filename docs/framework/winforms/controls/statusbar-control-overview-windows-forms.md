---
title: "StatusBar コントロールの概要 (Windows フォーム) | Microsoft Docs"
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
  - "StatusBar"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "ステータス バー"
  - "StatusBar コントロール [Windows フォーム], StatusBar コントロールの概要"
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# StatusBar コントロールの概要 (Windows フォーム)
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> コントロールと <xref:System.Windows.Forms.ToolStripStatusLabel> コントロールは、<xref:System.Windows.Forms.StatusBar> コントロールおよび <xref:System.Windows.Forms.StatusBarPanel> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.StatusBar> コントロールおよび <xref:System.Windows.Forms.StatusBarPanel> コントロールは、下位互換性を保つ目的および将来使用する目的で、必要に応じて保持できます。  
  
 Windows フォームの [StatusBar コントロール](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) 、フォーム上で領域として使用され、通常はウィンドウの下端に表示されます。アプリケーションは、このコントロールにさまざまなステータス情報を表示できます。  <xref:System.Windows.Forms.StatusBar> コントロールでは、コントロール上にステータス バー パネルを用意できます。このパネルでは、状態を示すテキストやアイコン、またはプロセスが進行中であることを伝えるアニメーション化された一連のアイコンを表示します。たとえば、[!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] では、文書が保存中であることが表示されます。  
  
## StatusBar コントロールの使用  
 Internet Explorer では、マウスがハイパーリンクの上に置かれたときに、ステータス バーにページの URL が表示されます。[!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] では、ページ番号、セクション番号、および、上書きや変更履歴などの編集モードの情報が表示されます。[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] では、ドッキング可能なウィンドウの操作方法 \(ドッキングと切り離し\) など、状況に応じた情報がステータス バーに表示されます。  
  
 <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> プロパティに `false` \(既定値\) を設定し、表示するテキストをステータス バーの <xref:System.Windows.Forms.StatusBar.Text%2A> プロパティに設定することで、ステータス バーにメッセージを表示できます。  <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> プロパティに `true` を設定し、<xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> の <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> メソッドを使用することで、ステータス バーを複数のパネルに分割して、複数の種類の情報を表示できます。  
  
## 参照  
 <xref:System.Windows.Forms.StatusBar>   
 <xref:System.Windows.Forms.ToolStripStatusLabel>   
 [方法 : Windows フォームの StatusBar コントロールでクリックされたパネルを確認する](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)