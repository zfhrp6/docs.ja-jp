---
title: "方法 : Windows フォーム DataGridView コントロールのセルの変更に基づいてカスタム動作を実行する | Microsoft Docs"
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
  - "セル, 検出 (変更を)"
  - "データ グリッド, 検出 (セルの変更を)"
  - "DataGridView コントロール [Windows フォーム], 検出 (セルの変更を)"
ms.assetid: 7fa44d01-97f4-4ccb-a149-bc72628d2c36
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : Windows フォーム DataGridView コントロールのセルの変更に基づいてカスタム動作を実行する
<xref:System.Windows.Forms.DataGridView> コントロールには多数のイベントがあり、これらを使用して <xref:System.Windows.Forms.DataGridView> セルの状態の変更を検出できます。  最もよく使用されるイベントは <xref:System.Windows.Forms.DataGridView.CellValueChanged> イベントと <xref:System.Windows.Forms.DataGridView.CellStateChanged> イベントの 2 つです。  
  
### DataGridView セルの値の変更を検出するには  
  
-   <xref:System.Windows.Forms.DataGridView.CellValueChanged> イベントのハンドラーを記述します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#130)]  
  
### DataGridView セルの状態の変更を検出するには  
  
-   <xref:System.Windows.Forms.DataGridView.CellStateChanged> イベントのハンドラーを記述します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#135](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#135)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#135](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#135)]  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。  C\# の場合は、イベント ハンドラーを対応するイベントに接続しておく必要があります。  
  
-   <xref:System?displayProperty=fullName> アセンブリおよび <xref:System.Windows.Forms?displayProperty=fullName> アセンブリへの参照。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.CellValueChanged?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.CellStateChanged?displayProperty=fullName>   
 [Windows フォーム DataGridView コントロールのセル、行、および列を使用したプログラミング](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)   
 [チュートリアル : Windows フォーム DataGridView コントロールのデータの妥当性検査](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)