---
title: "方法 : デザイナーを使用して TreeNode にショートカット メニューを割り当てる | Microsoft Docs"
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
  - "ショートカット メニュー, 接続 (TreeNodes に)"
  - "TreeNode, 割り当て (ショートカット メニューをデザイナーを使用して)"
ms.assetid: 8e45e184-1313-4f8f-90ff-2cd5789b2268
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : デザイナーを使用して TreeNode にショートカット メニューを割り当てる
Windows フォーム <xref:System.Windows.Forms.TreeView> コントロールは、Windows オペレーティング システムの Windows エクスプローラーの左ペインに表示されるファイルとフォルダーと同様のノードの階層構造を表示します。  <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> プロパティを設定すると、ユーザーは、<xref:System.Windows.Forms.TreeView> コントロールを右クリックしたときにコンテキストに従った操作を選択できます。  また、<xref:System.Windows.Forms.ContextMenuStrip> コンポーネントを個々の <xref:System.Windows.Forms.TreeNode> 項目に関連付けることによって、カスタマイズされたショートカット メニュー機能を <xref:System.Windows.Forms.TreeView> コントロールに追加できます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### デザイン時に、ショートカット メニューを TreeNode に関連付けるには  
  
1.  <xref:System.Windows.Forms.TreeView> コントロールをフォームに追加し、必要に応じて、<xref:System.Windows.Forms.TreeView> にノードを追加します。  詳細については、「[方法 : Windows フォーム TreeView コントロールでノードを追加および削除する](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)」を参照してください。  
  
2.  <xref:System.Windows.Forms.ContextMenuStrip> コンポーネントをフォームに追加し、実行時に使用できるようにするノード レベルの操作を表すメニュー項目をショートカット メニューに追加します。  詳細については、「[方法 : メニュー項目を ContextMenuStrip に追加する](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md)」を参照してください。  
  
3.  <xref:System.Windows.Forms.TreeView> コントロールの **\[TreeNode エディター\]** ダイアログ ボックスを再び開き、編集するノードを選択します。次に、追加したショートカット メニューに <xref:System.Windows.Forms.ContextMenuStrip> プロパティを設定します。  
  
4.  このプロパティを設定すると、ノードを右クリックしたときにショートカット メニューが表示されるようになります。  
  
     さらに、これらのメニュー項目に対する <xref:System.Windows.Forms.ToolStripItem.Click> イベントを処理するコードも記述する必要があります。  
  
## 参照  
 [TreeView コントロール](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)   
 [TreeView コントロールの概要](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)   
 [ContextMenuStrip コントロール](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)