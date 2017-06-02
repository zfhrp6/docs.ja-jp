---
title: "方法 : Windows フォーム DataGridView コントロールの選択されたセル、行、および列を取得する | Microsoft Docs"
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
  - "DataGridView コントロール [Windows フォーム], 取得 (選択項目を)"
  - "取得 (選択項目を), DataGridView コントロール [Windows フォーム]"
  - "選択, DataGridView コントロール [Windows フォーム]"
ms.assetid: d93c4b5b-498e-49bc-982a-2229d61778e4
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 方法 : Windows フォーム DataGridView コントロールの選択されたセル、行、および列を取得する
選択されたセル、行、または列を <xref:System.Windows.Forms.DataGridView> コントロールから取得するには、それぞれ <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> プロパティ、<xref:System.Windows.Forms.DataGridView.SelectedRows%2A> プロパティ、または <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> プロパティを使用します。  次の手順では、選択されたセルを取得し、行インデックスと列インデックスを <xref:System.Windows.Forms.MessageBox> に表示します。  
  
### DataGridView コントロールの選択されたセルを取得するには  
  
-   <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> プロパティを使用します。  
  
    > [!NOTE]
    >  多数のセルが表示されないようにするには、<xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> メソッドを使用します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### DataGridView コントロールの選択された行を取得するには  
  
-   <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> プロパティを使用します。  ユーザーが行を選択できるようにするには、<xref:System.Windows.Forms.DataGridView.SelectionMode%2A> プロパティを <xref:System.Windows.Forms.DataGridViewSelectionMode> または <xref:System.Windows.Forms.DataGridViewSelectionMode> に設定する必要があります。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### DataGridView コントロールの選択された列を取得するには  
  
-   <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> プロパティを使用します。  ユーザーが列を選択できるようにするには、<xref:System.Windows.Forms.DataGridView.SelectionMode%2A> プロパティを <xref:System.Windows.Forms.DataGridViewSelectionMode> または <xref:System.Windows.Forms.DataGridViewSelectionMode> に設定する必要があります。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   それぞれに <xref:System.Windows.Forms.Control.Click> イベントのハンドラーが割り当てられた、`selectedCellsButton`、`selectedRowsButton`、および `selectedColumnsButton` という名前の <xref:System.Windows.Forms.Button> コントロール。  
  
-   `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。  
  
-   <xref:System?displayProperty=fullName> アセンブリ、<xref:System.Windows.Forms?displayProperty=fullName> アセンブリ、および <xref:System.Text?displayProperty=fullName> アセンブリへの参照。  
  
## 信頼性の高いプログラミング  
 ここで説明するコレクションは、多数のセル、行、または列が選択されている場合は効率的に実行されません。  大量のデータを持つコレクションを使用する方法の詳細については、「[Windows フォーム DataGridView コントロールを拡張するための推奨される手順](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>   
 <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>   
 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>   
 <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>   
 <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>   
 [Windows フォーム DataGridView コントロールでの選択およびクリップボードの使用](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)