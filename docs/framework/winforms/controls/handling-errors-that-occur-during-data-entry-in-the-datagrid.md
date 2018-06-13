---
title: 'チュートリアル : Windows フォーム DataGridView コントロールでのデータ入力中に発生したエラーの処理'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- error handling [Windows Forms], dataGridView control
- data grids [Windows Forms], error handling
- DataGridView control [Windows Forms], error handling
- data entry [Windows Forms], error handling
- error handling [Windows Forms], data entry
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 30a68b85-d3af-4946-83c1-1e2d010d0511
ms.openlocfilehash: 92525d1818160f5645b95948910547c7d1541897
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529235"
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a>チュートリアル : Windows フォーム DataGridView コントロールでのデータ入力中に発生したエラーの処理
データ エントリのアプリケーションに必要な機能は、基になるデータ ストアからのエラーを処理します。 Windows フォーム<xref:System.Windows.Forms.DataGridView>コントロール、これにより、簡単を公開する、<xref:System.Windows.Forms.DataGridView.DataError>データ ストアは、制約違反または破損したビジネス ルールが検出されたときに発生するイベントです。  
  
 このチュートリアルから行を取得する、 `Customers` 、Northwind サンプル データベースのテーブルに表示して、<xref:System.Windows.Forms.DataGridView>コントロール。 重複しているときに`CustomerID`の新しい行または編集された既存の行の値が検出された、<xref:System.Windows.Forms.DataGridView.DataError>イベントが発生する、表示することによって処理される<xref:System.Windows.Forms.MessageBox>例外を説明します。  
  
 このトピックの「単一のリストとしてコードをコピーするに、を参照してください。[する方法: 処理エラーを発生中にデータ入力 Windows フォーム DataGridView コントロールで](../../../../docs/framework/winforms/controls/handle-errors-that-occur-during-data-entry-in-the-datagrid.md)です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   SQL Server の Northwind サンプル データベースがあるサーバーにアクセスします。  
  
## <a name="creating-the-form"></a>フォームの作成  
  
#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a>DataGridView コントロールでのデータ エントリ エラーを処理するには  
  
1.  派生するクラスを作成する<xref:System.Windows.Forms.Form>が含まれています、<xref:System.Windows.Forms.DataGridView>コントロールと<xref:System.Windows.Forms.BindingSource>コンポーネントです。  
  
     次のコード例は、基本的な初期化を提供しが含まれています、`Main`メソッドです。  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]  
  
2.  データベースへの接続の詳細を処理するためのフォームのクラス定義内のメソッドを実装します。  
  
     このコード例では、`GetData`設定されてを返すメソッド<xref:System.Data.DataTable>オブジェクト。 設定することを必ず、`connectionString`変数をデータベースを適切な値にします。  
  
    > [!IMPORTANT]
    >  接続文字列内に機密情報 (パスワードなど) を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。 データベースへのアクセスを制御する方法としては、Windows 認証 (統合セキュリティとも呼ばれます) を使用する方が安全です。 詳細については、「[接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)」を参照してください。  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]  
  
3.  フォームの用のハンドラーを実装<xref:System.Windows.Forms.Form.Load>を初期化するイベント、<xref:System.Windows.Forms.DataGridView>と<xref:System.Windows.Forms.BindingSource>し、データ バインディングを設定します。  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]  
  
4.  処理、<xref:System.Windows.Forms.DataGridView.DataError>でイベントを<xref:System.Windows.Forms.DataGridView>です。  
  
     コミット操作の場合は、エラーのコンテキストでエラーを表示、<xref:System.Windows.Forms.MessageBox>です。  
  
     [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridView.DataError#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
 フォームをテストして、期待どおりに動作することを確認します。  
  
#### <a name="to-test-the-form"></a>フォームをテストするには  
  
-   F5 キーを押してアプリケーションを実行します。  
  
     表示されます、<xref:System.Windows.Forms.DataGridView>コントロール Customers テーブルからデータを格納します。 重複した値を入力する場合`CustomerID`編集をコミットし、セルの値が自動的に元に戻すおよびが表示されます、<xref:System.Windows.Forms.MessageBox>データ エントリ エラーを表示します。  
  
## <a name="next-steps"></a>次の手順  
 このアプリケーションでは、基本を理解、<xref:System.Windows.Forms.DataGridView>コントロールの機能です。 動作と外観をカスタマイズすることができます、<xref:System.Windows.Forms.DataGridView>いくつかの方法で制御します。  
  
-   境界線とヘッダーのスタイルを変更します。 詳細については、次を参照してください。[する方法: 境界と Windows フォーム DataGridView コントロールでのグリッド線のスタイルを変更する](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md)です。  
  
-   有効にするか、ユーザー入力を制限、<xref:System.Windows.Forms.DataGridView>コントロール。 詳細については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールで防止行の追加および削除](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)、と[する方法: Windows フォーム DataGridView コントロールで列読み取り専用のため](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)です。  
  
-   ユーザー入力を検証して、<xref:System.Windows.Forms.DataGridView>コントロール。 詳細については、次を参照してください。[チュートリアル: Windows フォーム DataGridView コントロール内のデータの検証](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)です。  
  
-   仮想モードを使用して、非常に大きなデータ セットを処理します。 詳細については、次を参照してください。[チュートリアル: Windows フォーム DataGridView コントロールでの仮想モードを実装する](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)です。  
  
-   セルの外観をカスタマイズします。 詳細については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールのセルの外観をカスタマイズ](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)と[する方法: Windows フォーム DataGridView コントロールの既定のセル スタイルの設定](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [Windows フォーム DataGridView コントロールでのデータ入力](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [方法: Windows フォーム DataGridView コントロールでのデータ入力中に発生したエラーを処理する](../../../../docs/framework/winforms/controls/handle-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 [チュートリアル: Windows フォーム DataGridView コントロールのデータの妥当性検査](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)  
 [接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)
