---
title: "方法 : Windows フォーム DataGridView コントロール内の列の並べ替えモードを設定する | Microsoft Docs"
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
  - "データ グリッド, 並べ替え (データの)"
  - "DataGridView コントロール [Windows フォーム], 並べ替えモード"
  - "並べ替え, データ グリッド"
ms.assetid: 57dfed60-a608-40d5-86f9-d65686ffb325
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : Windows フォーム DataGridView コントロール内の列の並べ替えモードを設定する
<xref:System.Windows.Forms.DataGridView> コントロールでは、テキスト ボックスの列は既定で自動的に並べ替えられますが、その他のタイプの列は自動的には並べ替えられません。  これらの既定値をオーバーライドする必要が生じることがあります。  たとえば、テキスト、数値、または列挙型のセル値の代わりにイメージを表示できます。  イメージは並べ替えることができませんが、イメージが表す基になる値は並べ替えることができます。  
  
 <xref:System.Windows.Forms.DataGridView> コントロールでは、列の <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> プロパティ値によって、その列の並べ替え動作が決定されます。  
  
 「[方法 : Windows フォーム DataGridView コントロールのデータの書式設定をカスタマイズする](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)」の `Priority` 列の処理方法を次の手順に示します。  この列はイメージ列であり、既定では並べ替えられません。  ただし、実際には文字列であるセル値を含むため、自動的に並べ替えることができます。  
  
### 列に対して並べ替えモードを設定するには  
  
-   <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=fullName> プロパティを設定します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   `Priority` という名前の列を含む `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。  
  
-   <xref:System?displayProperty=fullName> アセンブリおよび <xref:System.Windows.Forms?displayProperty=fullName> アセンブリへの参照。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=fullName>   
 [Windows フォームの DataGridView コントロールでのデータの並べ替え](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロール内の列の並べ替えモード](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)   
 [方法 : Windows フォーム DataGridView コントロールの並べ替え機能をカスタマイズする](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)