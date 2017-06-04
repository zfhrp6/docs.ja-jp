---
title: "方法 : Windows フォームの DataGridView コントロールのセルの外観をカスタマイズする | Microsoft Docs"
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
  - "セル, カスタマイズ (DataGridView コントロール内の)"
  - "データ グリッド, カスタマイズ (セルを)"
  - "DataGridView コントロール [Windows フォーム], カスタマイズ (セルを)"
ms.assetid: 478b20c9-625c-4116-9c5c-5a16e6f4ec67
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : Windows フォームの DataGridView コントロールのセルの外観をカスタマイズする
セルの外観は、<xref:System.Windows.Forms.DataGridView> コントロールの <xref:System.Windows.Forms.DataGridView.CellPainting> イベントを処理することでカスタマイズできます。  <xref:System.Windows.Forms.DataGridView> コントロールの <xref:System.Drawing.Graphics> は、<xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> の <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> から抽出できます。  この <xref:System.Drawing.Graphics> を使用すると、<xref:System.Windows.Forms.DataGridView> コントロール全体の外観に影響しますが、通常は現在描画中のセルの外観だけをカスタマイズする必要があります。  <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> の <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> プロパティを使用すると、描画操作を現在描画中のセルだけに制限できます。  
  
 次のコード例では、<xref:System.Windows.Forms.DataGridView> コントロールの配色を使用して `ContactName` 列のすべてのセルを描画します。  各セルのテキスト コンテンツは <xref:System.Drawing.Color.Crimson%2A> で描画され、くぼんで表示される四角形は <xref:System.Windows.Forms.DataGridView> コントロールの <xref:System.Windows.Forms.DataGridView.GridColor%2A> プロパティと同じ色で描画されます。  
  
## 使用例  
 [!code-csharp[System.Windows.Forms.DataGridViewCellPainting#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms.DataGridViewCellPainting#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/VB/form1.vb#10)]  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   Northwind サンプル データベース内の Customers テーブルの列など、`ContactName` 列を含む、`dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。  
  
-   System、System.Windows.Forms、System.Drawing の各アセンブリへの参照。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.CellPainting>   
 [Windows フォーム DataGridView コントロールのカスタマイズ](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)