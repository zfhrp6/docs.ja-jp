---
title: 'チュートリアル: Windows フォーム DataGridView コントロールの 2 つを使用してマスター/詳細フォームを作成します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], displaying on Windows Forms
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: c5fa29e8-47f7-4691-829b-0e697a691f36
ms.openlocfilehash: 38f7c6197fb3ee79119e41ab9620bc3aa2b21900
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529442"
---
# <a name="walkthrough-creating-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>チュートリアル : Windows フォームの 2 つの DataGridView コントロールを使用したマスター/詳細形式のフォームの作成
使用するための最も一般的なシナリオの 1 つ、<xref:System.Windows.Forms.DataGridView>コントロールは、*マスター/詳細*フォーム、2 つのデータベース テーブル間の親/子リレーションシップが表示されます。 詳細テーブルが、対応する子データの更新をマスター テーブルの行を選択します。  
  
 間の相互作用を使用して、簡単には、マスター/詳細形式のフォームを実装する、<xref:System.Windows.Forms.DataGridView>コントロールと<xref:System.Windows.Forms.BindingSource>コンポーネントです。 このチュートリアルでは、2 つを使用してフォームを作成します<xref:System.Windows.Forms.DataGridView>コントロールと 2 つ<xref:System.Windows.Forms.BindingSource>コンポーネントです。 Northwind SQL Server サンプル データベースのテーブルに関連する 2 つのフォームが表示されます:`Customers`と`Orders`です。 Master データベース内のすべての顧客を表示するフォームが完了したら、<xref:System.Windows.Forms.DataGridView>詳細に選択した顧客のすべての注文<xref:System.Windows.Forms.DataGridView>です。  
  
 このトピックの「単一のリストとしてコードをコピーするに、を参照してください。[する方法:、マスター/詳細形式を使用して 2 つ Windows フォーム DataGridView コントロールの作成](../../../../docs/framework/winforms/controls/create-a-master-detail-form-using-two-datagridviews.md)です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   SQL Server の Northwind サンプル データベースがあるサーバーにアクセスします。  
  
## <a name="creating-the-form"></a>フォームの作成  
  
#### <a name="to-create-a-masterdetail-form"></a>マスター/詳細フォームを作成するには  
  
1.  派生するクラスを作成する<xref:System.Windows.Forms.Form>は 2 つと<xref:System.Windows.Forms.DataGridView>コントロールと 2 つ<xref:System.Windows.Forms.BindingSource>コンポーネントです。 次のコードは、基本的な形式の初期化を提供し、含まれています、`Main`メソッドです。 フォームを作成する、Visual Studio デザイナーを使用する場合は、このコードの代わりに、デザイナーの生成されたコードを使用しますが、変数の宣言には、ここに表示される名前を使用してください。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#02)]  
  
2.  データベースへの接続の詳細を処理するためのフォームのクラス定義内のメソッドを実装します。 この例では、`GetData`メンバーを追加する方法、<xref:System.Data.DataSet>オブジェクトを追加、<xref:System.Data.DataRelation>データ セット、およびバインドするオブジェクト、<xref:System.Windows.Forms.BindingSource>コンポーネントです。 `connectionString` 変数は、使用しているデータベースに合った値に設定してください。  
  
    > [!IMPORTANT]
    >  接続文字列内に機密情報 (パスワードなど) を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。 データベースへのアクセスを制御する方法としては、Windows 認証 (統合セキュリティとも呼ばれます) を使用する方が安全です。 詳細については、「[接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)」を参照してください。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#20)]  
  
3.  フォームの用のハンドラーを実装<xref:System.Windows.Forms.Form.Load>をバインドするイベント、<xref:System.Windows.Forms.DataGridView>コントロールを<xref:System.Windows.Forms.BindingSource>コンポーネントとの呼び出し、`GetData`メソッドです。 次の例には、サイズを変更するコードが含まれています。<xref:System.Windows.Forms.DataGridView>に合わせて、表示されるデータの列です。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#10)]  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
 フォームをテストして、期待どおりに動作することを確認します。  
  
#### <a name="to-test-the-form"></a>フォームをテストするには  
  
-   アプリケーションをコンパイルして実行します。  
  
     2 つが表示されます<xref:System.Windows.Forms.DataGridView>には、1 つです。 上では、Northwind から顧客`Customers`テーブル、および下部には、`Orders`選択した顧客に対応します。 上で複数の異なる行を選択すると<xref:System.Windows.Forms.DataGridView>、下の内容<xref:System.Windows.Forms.DataGridView>それに応じて変更します。  
  
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
 [Windows フォーム DataGridView コントロールでのデータの表示](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [方法: Windows フォームの 2 つの DataGridView コントロールを使用してマスター/詳細形式のフォームを作成する](../../../../docs/framework/winforms/controls/create-a-master-detail-form-using-two-datagridviews.md)  
 [接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)
