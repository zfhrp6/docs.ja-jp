---
title: "チュートリアル : Windows フォームの 2 つの DataGridView コントロールを使用したマスター/詳細形式のフォームの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "02/15/2017"
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
  - "DataGridView コントロール [Windows フォーム], マスター/詳細形式のフォーム"
  - "マスター/詳細リスト, 表示 (Windows フォームに)"
  - "親/子テーブル, 表示 (Windows フォームに)"
  - "チュートリアル [Windows フォーム], DataGridView コントロール"
ms.assetid: c5fa29e8-47f7-4691-829b-0e697a691f36
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# チュートリアル : Windows フォームの 2 つの DataGridView コントロールを使用したマスター/詳細形式のフォームの作成
<xref:System.Windows.Forms.DataGridView> コントロールの使用用途で特によくあるのが、*マスター\/詳細形式*のフォームです。これは、2 つのデータベース テーブル間の親子のリレーションシップを表示するフォームです。  マスター テーブルの行を選択すると、それに対応する子データによって詳細テーブルが更新されます。  
  
 <xref:System.Windows.Forms.DataGridView> コントロールと <xref:System.Windows.Forms.BindingSource> コンポーネントの間の対応を使用すると、マスター\/詳細形式のフォームを簡単に実装できます。  このチュートリアルでは、2 つの <xref:System.Windows.Forms.DataGridView> コントロールと 2 つの <xref:System.Windows.Forms.BindingSource> コンポーネントを使用してフォームを作成します。  このフォームには、`Customers` と `Orders` という、SQL Server の Northwind サンプル データベースの互いに関連付けられた 2 つのテーブルが表示されます。  完成したフォームでは、データベースに格納されているすべての顧客がマスター <xref:System.Windows.Forms.DataGridView> に表示され、選択した顧客に対応するすべての注文が詳細 <xref:System.Windows.Forms.DataGridView> に表示されます。  
  
 このトピックのコードを単一のリストとしてコピーするには、「[方法 : Windows フォームの 2 つの DataGridView コントロールを使用してマスター\/詳細形式のフォームを作成する](../../../../docs/framework/winforms/controls/create-a-master-detail-form-using-two-datagrids.md)」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   Northwind SQL Server サンプル データベースがインストールされたサーバーへのアクセス  
  
## フォームの作成  
  
#### マスター\/詳細形式のフォームを作成するには  
  
1.  <xref:System.Windows.Forms.Form> から派生した、2 つの <xref:System.Windows.Forms.DataGridView> コントロールと 2 つの <xref:System.Windows.Forms.BindingSource> コンポーネントを持つクラスを作成します。  次のコードは、基本的な形式の初期化処理です。この中には `Main` メソッドも含まれています。  [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] デザイナーを使用してフォームを作成した場合には、デザイナーによって生成されたコードをこのコードの代わりに使用できますが、この変数宣言で示されている名前を必ず使用してください。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#02)]  
  
2.  データベースへの接続の詳細を処理するためのメソッドを、フォームのクラス定義に実装します。  この例では、`GetData` というメソッドを使用しています。このメソッドでは、<xref:System.Data.DataSet> オブジェクトにレコードを読み込み、<xref:System.Data.DataRelation> オブジェクトをデータセットに追加し、<xref:System.Windows.Forms.BindingSource> コンポーネントをバインドします。  `connectionString` 変数の値は、使用するデータベースに合わせた適切な値に設定してください。  
  
    > [!IMPORTANT]
    >  接続文字列内にパスワードなどの機密情報を格納すると、アプリケーションのセキュリティに影響を及ぼすことがあります。  データベースへのアクセスを制御する方法としては、Windows 認証 \(統合セキュリティとも呼ばれます\) を使用する方が安全です。  詳細については、「[接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)」を参照してください。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#20)]  
  
3.  フォームの <xref:System.Windows.Forms.Form.Load> イベントのハンドラーを実装します。この中では、<xref:System.Windows.Forms.DataGridView> コントロールを <xref:System.Windows.Forms.BindingSource> コンポーネントにバインドし、`GetData` メソッドを呼び出します。  次の例には、表示するデータに合わせて <xref:System.Windows.Forms.DataGridView> の列のサイズを変更するコードが含まれています。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#10)]  
  
## アプリケーションのテスト  
 フォームをテストして、期待どおりに動作することを確認します。  
  
#### フォームをテストするには  
  
-   アプリケーションをコンパイルして実行します。  
  
     2 つの <xref:System.Windows.Forms.DataGridView> コントロールが上下に並んで表示されます。  Northwind の `Customers` テーブルの顧客が上に表示され、選択した顧客に対応する `Orders` が下に表示されます。  上の <xref:System.Windows.Forms.DataGridView> で別の行を選択すると、それに応じて下の <xref:System.Windows.Forms.DataGridView> の内容が変更されます。  
  
## 次の手順  
 このアプリケーションでは、<xref:System.Windows.Forms.DataGridView> コントロールの機能について基本を理解できます。  次のような方法を使用すると、<xref:System.Windows.Forms.DataGridView> コントロールの外観および動作をカスタマイズできます。  
  
-   輪郭およびヘッダー スタイルを変更します。  詳細については、「[方法 : Windows フォーム DataGridView コントロールの境界線とグリッド線のスタイルを変更する](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md)」を参照してください。  
  
-   <xref:System.Windows.Forms.DataGridView> コントロールへのユーザー入力の許可または制限。  詳細については、「[方法 : Windows フォーム DataGridView コントロールで行が追加および削除されないようにする](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)」および「[方法 : Windows フォームの DataGridView コントロールで列を読み取り専用にする](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
-   <xref:System.Windows.Forms.DataGridView> コントロールへのユーザー入力を検証します。  詳細については、「[チュートリアル : Windows フォーム DataGridView コントロールのデータの妥当性検査](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
-   仮想モードを使用した大量のデータの処理。  詳細については、「[チュートリアル : Windows フォーム DataGridView コントロールでの仮想モードの実装](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)」を参照してください。  
  
-   セルの外観をカスタマイズします。  詳細については、「[方法 : Windows フォームの DataGridView コントロールのセルの外観をカスタマイズする](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)」および「[方法 : Windows フォーム DataGridView コントロールの既定のセル スタイルを設定する](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.BindingSource>   
 [Windows フォーム DataGridView コントロールでのデータの表示](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)   
 [方法 : Windows フォームの 2 つの DataGridView コントロールを使用してマスター\/詳細形式のフォームを作成する](../../../../docs/framework/winforms/controls/create-a-master-detail-form-using-two-datagrids.md)   
 [接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)