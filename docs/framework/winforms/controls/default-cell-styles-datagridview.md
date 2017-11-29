---
title: "方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの既定のセル スタイルとデータ形式を設定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], setting styles
- data formats
- data [Windows Forms], setting formats
ms.assetid: fc6da49f-8942-41da-b49f-b2afc38cc656
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 28f81efa3d9f63127ad9748aaba9ce3483246a69
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-default-cell-styles-and-data-formats-for-the-windows-forms-datagridview-control-using-the-designer"></a>方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの既定のセル スタイルとデータ形式を設定する
<xref:System.Windows.Forms.DataGridView>コントロールを使用する既定のセル スタイルを指定し、コントロール全体の特定の列に対して、行ヘッダーおよび列ヘッダー、および交互の行台帳効果を作成するデータ形式します。 コントロール全体の設定の既定のスタイルは、既定のスタイルが交互の行と列設定によって上書きされます。 さらに、個々 の行とセルのコードに設定するスタイルは、既定のスタイルをオーバーライドします。  
  
 セルのスタイルの詳細については、次を参照してください。 [Windows フォーム DataGridView コントロールのセル スタイル](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)です。 交互の行のスタイルを設定するを参照してください。[する方法: 交互の行のスタイルを Windows フォーム DataGridView コントロールを使用して、デザイナー設定](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md)です。  
  
 使用してスタイルを設定することも、<xref:System.Windows.Forms.DataGridView.RowTemplate%2A>プロパティをコントロールに追加されるすべての行に影響します。 行テンプレートの詳細については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールで行のカスタマイズ、行テンプレートを使用して](../../../../docs/framework/winforms/controls/use-the-row-template-to-customize-rows-in-the-datagrid.md)です。  
  
 次の手順が必要な**Windows アプリケーション**が含まれているフォーム プロジェクト、<xref:System.Windows.Forms.DataGridView>コントロール。 このようなプロジェクトの設定の詳細については、次を参照してください。[する方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)と[する方法: Windows フォームにコントロールを追加](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-set-default-styles-for-all-cells-in-the-control"></a>コントロール内のすべてのセルの既定のスタイルを設定するには  
  
1.  選択、<xref:System.Windows.Forms.DataGridView>デザイナーで制御します。  
  
2.  **プロパティ**ウィンドウで、省略記号ボタン (![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) の横に、 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>、 <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>、または<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>プロパティです。 **CellStyle ビルダー**  ダイアログ ボックスが表示されます。  
  
3.  使用してプロパティを設定してスタイルを定義、**プレビュー**ウィンドウ選択内容を確認します。  
  
> [!NOTE]
>  Visual スタイルが有効な場合、行および列ヘッダー (以外の<xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) が自動的には、現在のテーマでスタイルをオーバーライドする、<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>と<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>プロパティの値。  
>   
>  選択された複数のセル スタイルを設定することができます<xref:System.Windows.Forms.DataGridView>セル スタイル プロパティを変更するのと同じ値がある場合にのみ、デザイナーの使用を制御します。 そのプロパティの任意のセルのスタイルが異なる場合、**プロパティ**の windows、 **CellStyle ビルダー**  ダイアログ ボックスは空白になります。  
  
### <a name="to-set-default-styles-for-cells-in-individual-columns"></a>個々 の列のセルの既定のスタイルを設定するには  
  
1.  右クリックし、<xref:System.Windows.Forms.DataGridView>デザイナーで制御し、選択**列の編集**です。  
  
2.  列を選択して、**選択されている列** ボックスの一覧です。  
  
3.  **列のプロパティ**グリッドで、省略記号ボタン (![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) の横に、<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A>プロパティ。 **CellStyle ビルダー**  ダイアログ ボックスが表示されます。  
  
4.  使用してプロパティを設定してスタイルを定義、**プレビュー**ウィンドウ選択内容を確認します。  
  
### <a name="to-format-data-in-cells"></a>セル内のデータの書式を設定するには  
  
1.  使用して、前述の手順のいずれかを表示、 **CellStyle ビルダー**  ダイアログ ボックスが既定のセル スタイル プロパティに関連します。  
  
2.  **CellStyle ビルダー**  ダイアログ ボックスで、省略記号ボタンをクリックして (![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) の横に、 <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A>プロパティ。 **書式指定文字列** ダイアログ ボックスが表示されます。  
  
3.  形式の種類を選択し、表示する小数点以下桁数の数) などの型の詳細の変更を使用して、**サンプル**ボックス選択内容を確認します。  
  
4.  バインドする場合、<xref:System.Windows.Forms.DataGridView>によって null 値を含む、入力がデータ ソースへのコントロール、 **Null 値**テキスト ボックス。 セルの値が null 参照に等しい場合に、この値が表示されます (`Nothing` Visual basic) または<xref:System.DBNull.Value?displayProperty=nameWithType>です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A?displayProperty=nameWithType>  
 [Windows フォーム DataGridView コントロールでのセルのスタイル](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [方法: デザイナーを使用して Windows フォーム DataGridView コントロールに交互の行のスタイルを設定する](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md)  
 [方法: Windows アプリケーション プロジェクトの作成](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [方法: Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
