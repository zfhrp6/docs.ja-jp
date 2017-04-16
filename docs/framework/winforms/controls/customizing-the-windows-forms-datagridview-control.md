---
title: "Windows フォーム DataGridView コントロールのカスタマイズ | Microsoft Docs"
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
  - "データ グリッド, カスタマイズ"
  - "DataGridView コントロール [Windows フォーム], カスタマイズ"
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Windows フォーム DataGridView コントロールのカスタマイズ
`DataGridView` コントロールには、セル、行、列の外観と基本動作 \(操作性\) を調整するためのさまざまなプロパティが用意されています。  ただし、<xref:System.Windows.Forms.DataGridViewCellStyle> クラスの機能を越えるカスタマイズが必要な場合には、コントロール用のオーナー描画を実装したり、カスタムのセル、列、行を作成して機能を拡張したりすることもできます。  
  
 セルと行を独自に描画するには、`DataGridView` のさまざまな描画イベントを使用します。  既存の機能を修正したり、新機能を実装したりするには、既存の `DataGridViewCell`、`DataGridViewColumn`、および `DataGridViewRow` 型から派生した独自の型を作成します。  また、新しい編集機能を実装するには、セルが編集モードになったときに特定のコントロールを表示する派生型を作成します。  
  
## このセクションの内容  
 [方法 : Windows フォームの DataGridView コントロールのセルの外観をカスタマイズする](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)  
 <xref:System.Windows.Forms.DataGridView.CellPainting> イベントを使用してセルを手動で描画する方法について説明します。  
  
 [方法 : Windows フォームの DataGridView コントロールの行の外観をカスタマイズする](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)  
 <xref:System.Windows.Forms.DataGridView.RowPrePaint> イベントと <xref:System.Windows.Forms.DataGridView.RowPostPaint> イベントを使用して、カスタムのグラデーション背景や複数の列にまたがる内容を含んだ行を描画する方法について説明します。  
  
 [方法 : Windows フォーム DataGridView コントロールのセルと列を、それぞれの動作と外観を拡張してカスタマイズする](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 `DataGridViewCell` および `DataGridViewColumn` から派生したカスタム型を作成して、セルにマウス ポインターが置かれたときにそのセルを強調表示する方法について説明します。  
  
 [方法 : Windows フォーム DataGridView コントロールのボタン列にあるボタンを無効にする](../../../../docs/framework/winforms/controls/disable-buttons-in-a-button-column-in-the-datagrid.md)  
 <xref:System.Windows.Forms.DataGridViewButtonCell> および <xref:System.Windows.Forms.DataGridViewButtonColumn> から派生したカスタム型を作成して、ボタン列に無効のボタンを表示する方法について説明します。  
  
 [方法 : Windows フォーム DataGridView Cells でコントロールをホストする](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 `IDataGridViewEditingControl` インターフェイスを実装し、`DataGridViewCell` および `DataGridViewColumn` から派生したカスタム型を作成して、セルが編集モードのときに <xref:System.Windows.Forms.DateTimePicker> コントロールが表示されるようにする方法について説明します。  
  
## 関連項目  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView> コントロールの参照ドキュメントを提供します。  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <xref:System.Windows.Forms.DataGridViewCell> クラスの参照ドキュメントを提供します。  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <xref:System.Windows.Forms.DataGridViewRow> クラスの参照ドキュメントを提供します。  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <xref:System.Windows.Forms.DataGridViewColumn> クラスの参照ドキュメントを提供します。  
  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 <xref:System.Windows.Forms.IDataGridViewEditingControl> インターフェイスの参照ドキュメントを提供します。  
  
## 関連項目  
 [Windows フォームの DataGridView コントロールの基本的な書式設定およびスタイル設定](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 コントロールの基本の外観およびセル データの表示形式を変更する方法を説明するトピックを示します。  
  
## 参照  
 [DataGridView コントロール](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)   
 [Windows フォーム DataGridView コントロールの列型](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)