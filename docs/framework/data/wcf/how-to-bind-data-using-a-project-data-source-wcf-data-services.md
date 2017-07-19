---
title: "方法: プロジェクト データ ソースを使用してデータをバインドする (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "データ バインディング, WCF Data Services"
  - "WCF Data Services, データ バインディング"
ms.assetid: 2477af0a-676f-44f7-b73d-e66208785509
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 方法: プロジェクト データ ソースを使用してデータをバインドする (WCF Data Services)
生成されたデータ オブジェクトに基づいて [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クライアント アプリケーション内にデータ ソースを作成できます。  **\[サービス参照の追加\]** ダイアログを使用して参照をデータ サービスに追加すると、生成されたクライアント データ クラスと一緒にプロジェクト データ ソースが作成されます。データ サービスが公開する各エンティティ セットに対して 1 つのデータ ソースが作成されます。  **\[データ ソース\]** ウィンドウからデータ ソースの項目をデザイナーにドラッグして、サービスのデータを表示するフォームを作成できます。  これらの項目は、データ ソースにバインドされているコントロールになります。  実行中、このデータ ソースは <xref:System.Data.Services.Client.DataServiceCollection%601> クラスのインスタンスにバインドされます。このインスタンスには、クエリによってデータ サービスに返されるオブジェクトが挿入されます。  詳細については、「[コントロールへのデータのバインド](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)」を参照してください。  
  
 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。  このサービスおよびクライアント データ クラスは、[WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)を完了したときに作成されます。  
  
### WPF ウィンドウでプロジェクト データ ソースを使用するには  
  
1.  WPF プロジェクトで Northwind データ サービスへの参照を追加します。  詳細については、「[方法: データ サービス参照を追加する](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)」を参照してください。  
  
2.  **\[データ ソース\]** ウィンドウで **\[NorthwindEntities\]** プロジェクト データ ソースの \[`Customers`\] ノードを展開します。  
  
3.  **\[CustomerID\]** 項目をクリックし、一覧から **\[ComboBox\]** を選択して **\[CustomerID\]** 項目を **\[Customers\]** ノードからデザイナーにドラッグします。  
  
     ウィンドウの XAML ファイルに次のオブジェクト要素が作成されます。  
  
    -   `customersViewSource` という名前の <xref:System.Windows.Data.CollectionViewSource> 要素。  最上位レベルの <xref:System.Windows.Controls.Grid> オブジェクト要素の <xref:System.Windows.FrameworkElement.DataContext%2A> プロパティが、この新しい <xref:System.Windows.Data.CollectionViewSource> に設定されます。  
  
    -   `CustomerID` という名前のデータ バインド <xref:System.Windows.Controls.ComboBox>。  
  
    -   <xref:System.Windows.Controls.Label>  
  
4.  **\[Orders\]** ナビゲーション プロパティをデザイナーにドラッグします。  
  
     ウィンドウの XAML ファイルに次の追加オブジェクト要素が作成されます。  
  
    -   `customersOrdersViewSource` という名前の 2 番目の <xref:System.Windows.Data.CollectionViewSource> 要素。このソースは `customerViewSource` です。  
  
    -   `ordersDataGrid` という名前のデータ バインド <xref:System.Windows.Controls.DataGrid> コントロール。  
  
5.  \(省略可能\) 追加の項目を **\[Customers\]** ノードからデザイナーにドラッグします。  
  
6.  フォームのコード ページを開き、次に示す `using` ステートメント \(Visual Basic の場合は `Imports`\) を追加します。  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersUsingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf2.xaml.cs#customersordersusingwpf)]  
  
7.  フォームを定義する部分クラスで、<xref:System.Data.Objects.ObjectContext> インスタンスを作成し、`customerID` の定数を定義する次のコードを追加します。  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf2.xaml.cs#customersordersdefinitionwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf2.xaml.vb#customersordersdefinitionwpf)]  
  
8.  デザイナーでウィンドウを選択します。  
  
    > [!NOTE]
    >  ウィンドウ内にある内容を選択するのではなく、ウィンドウ自身を選択します。  ウィンドウを選択すると、**\[プロパティ\]** ウィンドウの上部近くの **\[名前\]** テキスト ボックスにウィンドウ名が表示されます。  
  
9. **\[プロパティ\]** ウィンドウで、**\[イベント\]** ボタンをクリックします。  
  
10. **\[Loaded\]** イベントを見つけて、このイベントの横にあるドロップダウン リストをダブルクリックします。  
  
     Visual Studio でウィンドウの分離コード ファイルが開き、<xref:System.Windows.FrameworkElement.Loaded> イベント ハンドラーが生成されます。  
  
11. 新しく作成された <xref:System.Windows.FrameworkElement.Loaded> イベント ハンドラーで、次のコードをコピーして貼り付けます。  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf2.xaml.cs#customersordersdatabindingwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf2.xaml.vb#customersordersdatabindingwpf)]  
  
12. このコードは、関連する `Orders` オブジェクトと一緒に `Customers` の <xref:System.Collections.Generic.IEnumerable%601> を Northwind データ サービスから返す LINQ クエリの実行に基づいて `Customers` 型の <xref:System.Data.Services.Client.DataServiceCollection%601> のインスタンスを作成し、`customersViewSource` にバインドします。  
  
### Windows フォームでプロジェクト データ ソースを使用するには  
  
1.  **\[データ ソース\]** ウィンドウで **\[NorthwindEntities\]** プロジェクト データ ソースの \[**Customers**\] ノードを展開します。  
  
2.  **\[CustomerID\]** 項目をクリックし、一覧から **\[ComboBox\]** を選択して **\[CustomerID\]** 項目を **\[Customers\]** ノードからデザイナーにドラッグします。  
  
     次のコントロールがフォーム上に作成されます。  
  
    -   `customersBindingSource` という名前の <xref:System.Windows.Forms.BindingSource> のインスタンス。  
  
    -   `customersBindingNavigator` という名前の <xref:System.Windows.Forms.BindingNavigator> のインスタンス。  このコントロールは必要ないので削除できます。  
  
    -   `CustomerID` という名前のデータ バインド <xref:System.Windows.Forms.ComboBox>。  
  
    -   <xref:System.Windows.Forms.Label>  
  
3.  **\[Orders\]** ナビゲーション プロパティをフォームにドラッグします。  
  
4.  これにより、<xref:System.Windows.Forms.BindingSource.DataSource%2A> プロパティが `customersBindingSource` に設定され、<xref:System.Windows.Forms.BindingSource.DataMember%2A> プロパティが `Customers` に設定された `ordersBindingSource` コントロールが作成されます。  また、`ordersDataGridView` データ バインド コントロールも、適切なタイトルのラベル コントロールと共にフォーム上に作成されます。  
  
5.  \(省略可能\) 追加の項目を **\[Customers\]** ノードからデザイナーにドラッグします。  
  
6.  フォームのコード ページを開き、次に示す `using` ステートメント \(Visual Basic の場合は `Imports`\) を追加します。  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersUsing](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorders.cs#customersordersusing)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersUsing](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorders.vb#customersordersusing)]  
  
7.  フォームを定義する部分クラスで、<xref:System.Data.Objects.ObjectContext> インスタンスを作成し、`customerID` の定数を定義する次のコードを追加します。  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorders.cs#customersordersdefinition)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorders.vb#customersordersdefinition)]  
  
8.  フォーム デザイナーで、フォームをダブルクリックします。  
  
     フォームのコード ページが開き、フォームの `Load` イベントを処理するメソッドが作成されます。  
  
9. `Load` イベント ハンドラーで、次のコードをコピーして貼り付けます。  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorders.cs#customersordersdatabinding)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorders.vb#customersordersdatabinding)]  
  
10. このコードは、Northwind データ サービスから `Customers` の <xref:System.Collections.Generic.IEnumerable%601> を返す <xref:System.Data.Services.Client.DataServiceQuery%601> の実行に基づいて `Customers` 型の <xref:System.Data.Services.Client.DataServiceCollection%601> のインスタンスを作成し、`customersBindingSource` にバインドします。  
  
## 参照  
 [WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)   
 [方法: Windows Presentation Foundation 要素にデータをバインドする](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)