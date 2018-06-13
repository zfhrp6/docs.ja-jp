---
title: 'チュートリアル : バインドされていない Windows フォーム DataGridView コントロールの作成'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], displaying without binding to data source
- DataGridView control [Windows Forms], unbound data
- DataGridView control [Windows Forms], displaying data without binding to a data source
- data [Windows Forms], unbound
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 5a8d6afa-1b4b-4b24-8db8-501086ffdebe
ms.openlocfilehash: 26c2241f4b0a3b23255de15b3d0c9f8bdd15de02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541155"
---
# <a name="walkthrough-creating-an-unbound-windows-forms-datagridview-control"></a>チュートリアル : バインドされていない Windows フォーム DataGridView コントロールの作成
頻繁にデータベースから発生していない表形式のデータを表示することがあります。 たとえば、文字列の 2 次元配列の内容を表示することがあります。 <xref:System.Windows.Forms.DataGridView>クラスには、データ ソースにバインドせずにデータを表示する簡単で高度にカスタマイズ可能な方法が用意されています。 このチュートリアルで作成する方法、<xref:System.Windows.Forms.DataGridView>制御および管理が追加および「バインドされていない」モードでの行の削除。 既定では、ユーザーは、新しい行を追加できます。 行の追加を防ぐためには、設定、<xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A>プロパティは`false`します。  
  
 このトピックの「単一のリストとしてコードをコピーするに、を参照してください。[する方法: バインドされていない Windows フォームの DataGridView コントロールの作成](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md)です。  
  
## <a name="creating-the-form"></a>フォームの作成  
  
#### <a name="to-use-an-unbound-datagridview-control"></a>バインドされていない DataGridView コントロールを使用するには  
  
1.  派生するクラスを作成する<xref:System.Windows.Forms.Form>し、次の変数宣言が含まれていますと`Main`メソッドです。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#02)]  
  
2.  実装する`SetupLayout`フォームのレイアウトを設定するフォームのクラス定義内のメソッドです。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#20)]  
  
3.  作成、`SetupDataGridView`を設定するメソッド、<xref:System.Windows.Forms.DataGridView>およびプロパティの列です。  
  
     このメソッドは最初に、追加、<xref:System.Windows.Forms.DataGridView>コントロールをフォームの<xref:System.Windows.Forms.Control.Controls%2A>コレクション。 次に、表示する列の数が設定を使用して、<xref:System.Windows.Forms.DataGridView.ColumnCount%2A>プロパティです。 設定して、列ヘッダーの既定のスタイルを設定、 <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A>、 <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>、および<xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A>のプロパティ、<xref:System.Windows.Forms.DataGridViewCellStyle>によって返される、<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>プロパティです。  
  
     レイアウトと外観のプロパティが設定され、列名の割り当てられます。 このメソッドの終了時に、<xref:System.Windows.Forms.DataGridView>コントロールが事前設定する準備ができています。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#30)]  
  
4.  作成、`PopulateDataGridView`行を追加する方法、<xref:System.Windows.Forms.DataGridView>コントロール。  
  
     各行は、曲とその関連情報を表します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#40)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#40)]  
  
5.  インプレースのユーティリティ メソッドでは、イベント ハンドラーをアタッチできます。  
  
     処理する、**追加**と**削除**ボタンの<xref:System.Windows.Forms.Control.Click>イベントと、フォームの<xref:System.Windows.Forms.Form.Load>イベント、および<xref:System.Windows.Forms.DataGridView>コントロールの<xref:System.Windows.Forms.DataGridView.CellFormatting>イベント。  
  
     ときに、**追加**ボタンの<xref:System.Windows.Forms.Control.Click>イベントが発生すると、新しい空の行を追加する、<xref:System.Windows.Forms.DataGridView>です。  
  
     ときに、**削除**ボタンの<xref:System.Windows.Forms.Control.Click>イベントは、選択した行が削除されたである場合を除き、ユーザーは、新しいレコードの行が新しい行を追加します。 この行は、最後の行では常に、<xref:System.Windows.Forms.DataGridView>コントロール。  
  
     ときに、フォームの<xref:System.Windows.Forms.Form.Load>のイベントが発生、 `SetupLayout`、 `SetupDataGridView`、および`PopulateDataGridView`ユーティリティ メソッドが呼び出されます。  
  
     ときに、<xref:System.Windows.Forms.DataGridView.CellFormatting>イベントが発生すると、各セルに、`Date`セルの値を解析できない場合を除き、列を長い形式の日付として書式設定します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#10)]  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
 フォームをテストして、期待どおりに動作することを確認します。  
  
#### <a name="to-test-the-form"></a>フォームをテストするには  
  
-   F5 キーを押してアプリケーションを実行します。  
  
     表示されます、<xref:System.Windows.Forms.DataGridView>に曲を表示するコントロール`PopulateDataGridView`です。 新しい行を追加することができます、**行の追加** ボタン、およびするがで選択した行を削除、**行の削除**ボタンをクリックします。 バインドされていない<xref:System.Windows.Forms.DataGridView>コントロールは、データ ストアとそのデータは、任意の外部ソースに依存しないなど、<xref:System.Data.DataSet>または配列。  
  
## <a name="next-steps"></a>次の手順  
 このアプリケーションでは、基本を理解、<xref:System.Windows.Forms.DataGridView>コントロールの機能です。 動作と外観をカスタマイズすることができます、<xref:System.Windows.Forms.DataGridView>いくつかの方法で制御します。  
  
-   境界線とヘッダーのスタイルを変更します。 詳細については、次を参照してください。[する方法: 境界と Windows フォーム DataGridView コントロールでのグリッド線のスタイルを変更する](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md)です。  
  
-   有効にするか、ユーザー入力を制限、<xref:System.Windows.Forms.DataGridView>コントロール。 詳細については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールで防止行の追加および削除](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)、と[する方法: Windows フォーム DataGridView コントロールで列読み取り専用のため](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)です。  
  
-   データベースに関連するエラーのユーザー入力を確認してください。 詳細については、次を参照してください。[チュートリアル: Windows フォーム DataGridView コントロールでのデータ入力中に発生したエラーの処理](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)です。  
  
-   仮想モードを使用して、非常に大きなデータ セットを処理します。 詳細については、次を参照してください。[チュートリアル: Windows フォーム DataGridView コントロールでの仮想モードを実装する](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)です。  
  
-   セルの外観をカスタマイズします。 詳細については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールのセルの外観をカスタマイズ](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)と[する方法: Windows フォーム DataGridView コントロールの既定のセル スタイルの設定](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.DataGridView>  
 [Windows フォーム DataGridView コントロールでのデータの表示](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [方法: 連結されていない Windows フォーム DataGridView コントロールを作成する](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md)  
 [Windows フォーム DataGridView コントロールでのデータ表示モード](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
