---
title: "方法 : Windows フォーム DataGridView コントロールの各セルにツールヒントを追加する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "データ グリッド, 追加 (ツールヒントを)"
  - "DataGridView コントロール [Windows フォーム], 追加 (ツールヒントを)"
  - "ツールヒント [Windows フォーム], 追加 (データ グリッドに)"
ms.assetid: 2a81f9de-d58b-4ea8-bc0b-8d93c2f4cf78
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : Windows フォーム DataGridView コントロールの各セルにツールヒントを追加する
既定では、ツールヒントは、小さすぎて全体の内容を表示できない <xref:System.Windows.Forms.DataGridView> セルの値を表示するために使用されます。  ただし、この動作をオーバーライドして、ツールヒントのテキスト値を個々のセルに設定することもできます。  これは、セルに関する追加情報を表示したり、セルの内容の代替説明を提供したりする場合に便利です。  たとえば、ステータス アイコンを表示する行がある場合に、ツールヒントを使用して説明を提供できます。  
  
 <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=fullName> プロパティを `false` に設定して、セル レベルのツールヒントの表示を無効にすることもできます。  
  
### ツールヒントをセルに追加するには  
  
-   <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=fullName> プロパティを設定します。  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## コードのコンパイル  
  
-   この例には、次の項目が必要です。  
  
-   1 ～ 4 個のアスタリスク記号 \("\*"\) から成る文字列値を表示するための `Rating` という名前の列を含む `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。  このコントロールの <xref:System.Windows.Forms.DataGridView.CellFormatting> イベントは、例に示すイベント ハンドラー メソッドに関連付けられている必要があります。  
  
-   <xref:System?displayProperty=fullName> アセンブリおよび <xref:System.Windows.Forms?displayProperty=fullName> アセンブリへの参照。  
  
## 信頼性の高いプログラミング  
 <xref:System.Windows.Forms.DataGridView> コントロールを外部データ ソースにバインドする場合や、仮想モードを実装して独自のデータ ソースを提供する場合には、パフォーマンスが低下することがあります。  大量のデータを処理する際のパフォーマンスの低下を防止するには、複数のセルの <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> プロパティを設定する代わりに、<xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> イベントを処理します。  このイベントを処理する場合、セルの <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> プロパティの値を取得するとイベントが発生し、イベント ハンドラーでの指定に基づいて <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=fullName> プロパティの値が返されます。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewCell>   
 <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=fullName>   
 [Windows フォーム DataGridView コントロールのセル、行、および列を使用したプログラミング](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)