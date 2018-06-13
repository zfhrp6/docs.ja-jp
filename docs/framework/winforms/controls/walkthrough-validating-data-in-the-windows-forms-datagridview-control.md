---
title: 'チュートリアル : Windows フォーム DataGridView コントロールのデータの妥当性検査'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validating data [Windows Forms], Windows Forms
- data [Windows Forms], validation
- DataGridView control [Windows Forms], data validation
- data grids [Windows Forms], validating data
- data validation [Windows Forms], Windows Forms
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: a4f1d015-2969-430c-8ea2-b612d179c290
ms.openlocfilehash: 8ad8caef5db13b1f917a6c27da523d3ded915d84
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540964"
---
# <a name="walkthrough-validating-data-in-the-windows-forms-datagridview-control"></a>チュートリアル : Windows フォーム DataGridView コントロールのデータの妥当性検査
データ エントリの機能をユーザーに表示するときに頻繁に、フォームに入力データを検証する必要があります。 <xref:System.Windows.Forms.DataGridView>クラスには、データがデータ ストアにコミットする前に検証を実行する便利な方法が用意されています。 データを検証するには、処理することにより、<xref:System.Windows.Forms.DataGridView.CellValidating>によって発生するイベント、<xref:System.Windows.Forms.DataGridView>現在のセルが変更されたとき。  
  
 このチュートリアルから行を取得する、 `Customers` 、Northwind サンプル データベースのテーブルに表示して、<xref:System.Windows.Forms.DataGridView>コントロール。 ユーザーが内のセルを編集するときに、`CompanyName`列と、セルのままにすると、<xref:System.Windows.Forms.DataGridView.CellValidating>イベント ハンドラーは新しい会社名の文字列を新しい値が空の文字列である場合は空ではありません確認を検査して、<xref:System.Windows.Forms.DataGridView>により、ユーザーのカーソル。セルから空でない文字列を入力するまでです。  
  
 このトピックの「単一のリストとしてコードをコピーするに、を参照してください。[する方法: Windows フォーム DataGridView コントロール内データの検証](../../../../docs/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control.md)です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   SQL Server の Northwind サンプル データベースがあるサーバーにアクセスします。  
  
## <a name="creating-the-form"></a>フォームの作成  
  
#### <a name="to-validate-data-entered-in-a-datagridview"></a>DataGridView で入力したデータを検証するには  
  
1.  派生するクラスを作成する<xref:System.Windows.Forms.Form>が含まれています、<xref:System.Windows.Forms.DataGridView>コントロールと<xref:System.Windows.Forms.BindingSource>コンポーネントです。  
  
     次のコード例は、基本的な初期化を提供しが含まれています、`Main`メソッドです。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#02)]  
  
2.  データベースへの接続の詳細を処理するためのフォームのクラス定義内のメソッドを実装します。  
  
     このコード例では、`GetData`設定されてを返すメソッド<xref:System.Data.DataTable>オブジェクト。 設定することを必ず、`connectionString`変数をデータベースを適切な値にします。  
  
    > [!IMPORTANT]
    >  接続文字列内に機密情報 (パスワードなど) を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。 データベースへのアクセスを制御するより安全な方法は、Windows 認証とも呼ばれる統合セキュリティを使用します。 詳細については、「[接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)」を参照してください。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#30)]  
  
3.  フォームの用のハンドラーを実装<xref:System.Windows.Forms.Form.Load>を初期化するイベント、<xref:System.Windows.Forms.DataGridView>と<xref:System.Windows.Forms.BindingSource>し、データ バインディングを設定します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#10)]  
  
4.  ハンドラーを実装、<xref:System.Windows.Forms.DataGridView>コントロールの<xref:System.Windows.Forms.DataGridView.CellValidating>と<xref:System.Windows.Forms.DataGridView.CellEndEdit>イベント。  
  
     <xref:System.Windows.Forms.DataGridView.CellValidating>イベント ハンドラーが判断したかどうかのセルの値、`CompanyName`列は空です。 セルの値には、検証が失敗した場合、設定、<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>のプロパティ、<xref:System.Windows.Forms.DataGridViewCellValidatingEventArgs?displayProperty=nameWithType>クラスを`true`です。 これにより、<xref:System.Windows.Forms.DataGridView>コントロールをセルからカーソルを防ぐためにします。 設定、<xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A>説明の文字列には、行のプロパティです。 これには、エラー テキストを含むツールヒントにエラー アイコンが表示されます。 <xref:System.Windows.Forms.DataGridView.CellEndEdit> 、イベント ハンドラーを設定、<xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A>の行に空の文字列のプロパティです。 <xref:System.Windows.Forms.DataGridView.CellEndEdit>セルが編集モードは、検証が失敗した場合に行うことはできませんに終了する場合にのみ発生します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#20)]  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
 フォームをテストして、期待どおりに動作することを確認します。  
  
#### <a name="to-test-the-form"></a>フォームをテストするには  
  
-   アプリケーションをコンパイルして実行します。  
  
     表示されます、<xref:System.Windows.Forms.DataGridView>からのデータが格納された、`Customers`テーブル。 内のセルをダブルクリックすると、`CompanyName`列、値を編集することができます。 すべての文字を削除して、セルを終了する TAB キーを押して、<xref:System.Windows.Forms.DataGridView>終了できないようにします。 セルに空でない文字列を入力すると、<xref:System.Windows.Forms.DataGridView>コントロールでは、セルを終了することができます。  
  
## <a name="next-steps"></a>次の手順  
 このアプリケーションでは、基本を理解、<xref:System.Windows.Forms.DataGridView>コントロールの機能です。 動作と外観をカスタマイズすることができます、<xref:System.Windows.Forms.DataGridView>いくつかの方法で制御します。  
  
-   境界線とヘッダーのスタイルを変更します。 詳細については、次を参照してください。[する方法: 境界と Windows フォーム DataGridView コントロールでのグリッド線のスタイルを変更する](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md)です。  
  
-   有効にするか、ユーザー入力を制限、<xref:System.Windows.Forms.DataGridView>コントロール。 詳細については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールで防止行の追加および削除](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)、と[する方法: Windows フォーム DataGridView コントロールで列読み取り専用のため](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)です。  
  
-   データベースに関連するエラーのユーザー入力を確認してください。 詳細については、次を参照してください。[チュートリアル: Windows フォーム DataGridView コントロールでのデータ入力中に発生したエラーの処理](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)です。  
  
-   仮想モードを使用して、非常に大きなデータ セットを処理します。 詳細については、次を参照してください。[チュートリアル: Windows フォーム DataGridView コントロールでの仮想モードを実装する](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)です。  
  
-   セルの外観をカスタマイズします。 詳細については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールのセルの外観をカスタマイズ](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)と[する方法: フォントの設定と Windows フォーム DataGridView コントロールでの色のスタイル](../../../../docs/framework/winforms/controls/how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [Windows フォーム DataGridView コントロールでのデータ入力](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [方法: Windows フォーム DataGridView コントロールのデータを検証する](../../../../docs/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control.md)  
 [チュートリアル: Windows フォーム DataGridView コントロールでのデータ入力中に発生したエラーの処理](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 [接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)
