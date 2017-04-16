---
title: "方法 : ショートカット メニューを TreeView ノードに追加する | Microsoft Docs"
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
  - "ショートカット メニュー, 追加 (TreeView コントロールに)"
  - "ツリー ノード (TreeView コントロールの), ショートカット メニュー"
  - "TreeView コントロール [Windows フォーム], 追加 (ショートカット メニューを)"
ms.assetid: a23c6752-fd8f-44ad-b781-bab37962fc7c
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : ショートカット メニューを TreeView ノードに追加する
Windows フォーム <xref:System.Windows.Forms.TreeView> \(ツリー ビュー\) コントロールは、Windows エクスプローラーの左側のペインに表示されるファイルやフォルダーと同じような形式で、ノードを階層表示します。  <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> プロパティを設定すると、ユーザーは、<xref:System.Windows.Forms.TreeView> コントロールを右クリックしたときにコンテキストに従った操作を選択できます。  また、<xref:System.Windows.Forms.ContextMenuStrip> コンポーネントを個々の <xref:System.Windows.Forms.TreeNode> 項目に関連付けることによって、カスタマイズされたショートカット メニュー機能を <xref:System.Windows.Forms.TreeView> コントロールに追加できます。  
  
### プログラムでショートカット メニューを TreeNode に関連付けるには  
  
1.  適切なプロパティ設定で <xref:System.Windows.Forms.TreeView> コントロールをインスタンス化し、ルート <xref:System.Windows.Forms.TreeNode> を作成し、サブノードを追加します。  
  
2.  <xref:System.Windows.Forms.ContextMenuStrip> コンポーネントをインスタンス化し、実行時に使用できるようにする各操作の <xref:System.Windows.Forms.ToolStripMenuItem> を追加します。  
  
3.  適切な <xref:System.Windows.Forms.TreeNode> の <xref:System.Windows.Forms.TreeNode.ContextMenuStrip%2A> プロパティを、作成するショートカットに設定します。  
  
4.  このプロパティを設定すると、ノードを右クリックしたときにショートカット メニューが表示されるようになります。  
  
 <xref:System.Windows.Forms.TreeView> のルート <xref:System.Windows.Forms.TreeNode> に関連付けられた、基本的な <xref:System.Windows.Forms.TreeView> と <xref:System.Windows.Forms.ContextMenuStrip> を作成するコード例を次に示します。  開発する <xref:System.Windows.Forms.TreeView> に合わせてメニューの選択肢をカスタマイズする必要があります。  さらに、これらのメニュー項目に対する <xref:System.Windows.Forms.ToolStripItem.Click> イベントを処理するコードも記述する必要があります。  
  
 [!code-cpp[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/cpp/Form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/VB/Form1.vb#1)]  
  
## 参照  
 <xref:System.Windows.Forms.ContextMenuStrip>   
 [TreeView コントロール](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)