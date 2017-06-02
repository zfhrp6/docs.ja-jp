---
title: "方法 : Windows フォーム DataGridView コントロールの境界線とグリッド線のスタイルを変更する | Microsoft Docs"
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
  - "データ グリッド, 変更 (境界線スタイルを)"
  - "データ グリッド, 変更 (グリッド線スタイルを)"
  - "DataGridView コントロール [Windows フォーム], 境界線スタイル"
  - "DataGridView コントロール [Windows フォーム], グリッド線スタイル"
  - "グリッド線, 変更 (スタイルを)"
ms.assetid: 2f413c7a-4025-4171-8e3a-66ef908ea583
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : Windows フォーム DataGridView コントロールの境界線とグリッド線のスタイルを変更する
<xref:System.Windows.Forms.DataGridView> コントロールを使用すると、コントロールの境界線とグリッド線の外観をカスタマイズしてユーザーの操作性を向上できます。  コントロール内のセルの境界線スタイルだけでなく、グリッド線の色やコントロールの境界線スタイルも変更できます。  通常のセル、行のヘッダー セル、および列のヘッダー セルに対して、異なるセル境界線スタイルを適用することもできます。  
  
> [!NOTE]
>  グリッド線の色は、<xref:System.Windows.Forms.DataGridViewCellBorderStyle> 列挙体の <xref:System.Windows.Forms.DataGridViewCellBorderStyle> 値、<xref:System.Windows.Forms.DataGridViewCellBorderStyle> 値、および <xref:System.Windows.Forms.DataGridViewCellBorderStyle> 値、および <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> 列挙体の <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> 値だけで使用できます。  これらの列挙体のその他の値には、オペレーティング システムによって指定された色が使用されます。  また、<xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=fullName> メソッドにより Windows XP および Windows Server 2003 ファミリ上で visual スタイルが有効になっている場合は、<xref:System.Windows.Forms.DataGridView.GridColor%2A> プロパティ値は使用されません。  
  
### グリッド線の色をプログラムで変更するには  
  
-   <xref:System.Windows.Forms.DataGridView.GridColor%2A> プロパティを設定します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#031](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#031)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#031](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#031)]  
  
### DataGridView コントロール全体の境界線スタイルをプログラムで変更するには  
  
-   <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> プロパティを <xref:System.Windows.Forms.BorderStyle> 列挙値のいずれかに設定します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#032](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#032)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#032](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#032)]  
  
### DataGridView セルの境界線スタイルをプログラムで変更するには  
  
-   <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>、<xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>、および <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A> の各プロパティを設定します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#033](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#033)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#033](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#033)]  
  
## 使用例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#030](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#030)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#030](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#030)]  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。  
  
-   <xref:System?displayProperty=fullName> アセンブリ、<xref:System.Windows.Forms?displayProperty=fullName> アセンブリ、および <xref:System.Drawing?displayProperty=fullName> アセンブリへの参照。  
  
## 参照  
 <xref:System.Windows.Forms.BorderStyle>   
 <xref:System.Windows.Forms.DataGridView.BorderStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.GridColor%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewCellBorderStyle>   
 <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>   
 [Windows フォームの DataGridView コントロールの基本的な書式設定およびスタイル設定](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)