---
title: "方法 : ToolStrip を ToolStripContainer からフォームに移動する | Microsoft Docs"
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
  - "ToolStrip コントロール [Windows フォーム], 親 (フォームの)"
  - "Windows フォーム, 親 (ToolStrip コントロールの)"
ms.assetid: a1c94a7f-6fc5-4e4c-84cf-ff11dc573d33
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : ToolStrip を ToolStripContainer からフォームに移動する
<xref:System.Windows.Forms.ToolStrip> を <xref:System.Windows.Forms.ToolStripContainer> からフォームに移動するには、次の手順に従います。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### ToolStrip を ToolStripContainer からフォームに移動するには  
  
1.  <xref:System.Windows.Forms.ToolStrip> を選択します。  
  
2.  Ctrl キーを押しながら X キーを押すか、または <xref:System.Windows.Forms.ToolStrip> を右クリックし、コンテキスト メニューの **\[切り取り\]** をクリックして、<xref:System.Windows.Forms.ToolStrip> を切り取ります。  
  
3.  フォームを選択します。  
  
4.  Ctrl キーを押しながら V キーを押すか、または **\[編集\]** メニューの **\[貼り付け\]** をクリックして <xref:System.Windows.Forms.ToolStrip> を貼り付けます。  
  
5.  <xref:System.Windows.Forms.ToolStrip> の <xref:System.Windows.Forms.ToolStrip.Dock%2A> プロパティを **\[Top\]** に設定します。  
  
## 参照  
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.ToolStripContainer>   
 [ToolStrip コントロールの概要](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)