---
title: Windows フォーム DataGridView コントロールのカスタマイズ
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], customization
- DataGridView control [Windows Forms], customization
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
ms.openlocfilehash: 92bbace4d0869aca67025f1e4ac8c451fe073219
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529845"
---
# <a name="customizing-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロールのカスタマイズ
`DataGridView`コントロールの基本的な動作 (ルック アンド フィール) のセル、行、列と外観を調整するために使用できるいくつかのプロパティを提供します。 機能以外に特別なニーズがあるかどうか、<xref:System.Windows.Forms.DataGridViewCellStyle>クラス、ただし、またオーナー描画コントロールを実装したり、カスタムのセル、列、および行を作成してそのような機能を拡張します。  
  
 描画するセルおよび行自分で、さまざまな処理できる`DataGridView`描画イベント。 を既存の機能を変更または新しい機能を提供する、既存のファイルから派生した独自の型を作成することができます`DataGridViewCell`、 `DataGridViewColumn`、および`DataGridViewRow`型です。 コントロールを表示するセルが編集モードの場合、任意の派生型を作成することで、新しい編集機能を指定することもできます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: Windows フォームの DataGridView コントロールのセルの外観をカスタマイズする](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)  
 処理する方法について説明します、<xref:System.Windows.Forms.DataGridView.CellPainting>セルを手動で描画するためにイベント。  
  
 [方法: Windows フォームの DataGridView コントロールの行の外観をカスタマイズする](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)  
 処理する方法について説明します、<xref:System.Windows.Forms.DataGridView.RowPrePaint>と<xref:System.Windows.Forms.DataGridView.RowPostPaint>にまたがる複数の列のカスタムのグラデーションの背景を持つ行を描画してコンテンツをするためにイベント。  
  
 [方法: Windows フォーム DataGridView コントロールのセルと列を、それぞれの動作と外観を拡張してカスタマイズする](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 派生したカスタムの型を作成する方法について説明`DataGridViewCell`と`DataGridViewColumn`にマウス ポインターを合わせると、セルを強調表示するためにします。  
  
 [方法: Windows フォーム DataGridView コントロールのボタン列にあるボタンを無効にする](../../../../docs/framework/winforms/controls/disable-buttons-in-a-button-column-in-the-datagrid.md)  
 派生したカスタムの型を作成する方法について説明<xref:System.Windows.Forms.DataGridViewButtonCell>と<xref:System.Windows.Forms.DataGridViewButtonColumn>ボタン列に無効になっているボタンを表示するためにします。  
  
 [方法: Windows フォーム DataGridView Cells でコントロールをホストする](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 実装する方法について説明します、`IDataGridViewEditingControl`インターフェイスの種類を作成するカスタムから派生した`DataGridViewCell`と`DataGridViewColumn`を表示するために、<xref:System.Windows.Forms.DateTimePicker>セルが編集モードの場合を制御します。  
  
## <a name="reference"></a>参照  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView> コントロールのリファレンス ドキュメントを提供します。  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 リファレンス ドキュメントを提供、<xref:System.Windows.Forms.DataGridViewCell>クラスです。  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 リファレンス ドキュメントを提供、<xref:System.Windows.Forms.DataGridViewRow>クラスです。  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 リファレンス ドキュメントを提供、<xref:System.Windows.Forms.DataGridViewColumn>クラスです。  
  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 リファレンス ドキュメントを提供、<xref:System.Windows.Forms.IDataGridViewEditingControl>インターフェイスです。  
  
## <a name="related-sections"></a>関連項目  
 [Windows フォームの DataGridView コントロールの基本的な書式設定およびスタイル設定](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 コントロールの基本の外観およびセル データの書式設定を変更する方法を説明するトピックを示します。  
  
## <a name="see-also"></a>関連項目  
 [DataGridView コントロール](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [Windows フォーム DataGridView コントロールの列型](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
