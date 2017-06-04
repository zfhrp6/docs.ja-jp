---
title: "方法 : データ ソースに Windows フォーム DataGrid コントロールをバインドする | Microsoft Docs"
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
  - "バインド コントロール"
  - "バインド コントロール, DataGrid コントロール"
  - "データ バインド, DataGrid コントロール"
  - "データ バインド コントロール, DataGrid"
  - "DataGrid コントロール [Windows フォーム], データ バインド"
  - "データセット [Windows フォーム], バインド (DataGrid コントロールに)"
  - "Windows フォーム コントロール, データ バインド"
ms.assetid: 128cdb07-dfd3-4d60-9d6a-902847667c36
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 方法 : データ ソースに Windows フォーム DataGrid コントロールをバインドする
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 Windows フォームの <xref:System.Windows.Forms.DataGrid> コントロールは、データ ソースの情報を表示するようにデザインされています。  実行時には <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> メソッドを呼び出してコントロールをバインドします。  各種データ ソースのデータを表示できますが、最も一般的なソースはデータセットとデータ ビューです。  
  
### プログラムによって DataGrid コントロールをデータ連結するには  
  
1.  データセットにデータを読み込むコードを記述します。  
  
     データ ソースが、データセット テーブルに基づくデータセットまたはデー タビューの場合は、そのデータセットにデータを読み込むためのコードをフォームに追加します。  
  
     実際に使用するコードは、データセットがデータをどこで取得するかに依存します。  データセットにデータベースのデータを直接読み込む場合は、通常はデータ アダプターの `Fill`  メソッドを呼び出します。次の例では、`DsCategories1` というデータセットにデータを読み込んでいます。  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     XML Web サービスのデータをデータセットに読み込む場合は、通常、サービスのインスタンスを作成するコードを記述し、データセットを返すメソッドのいずれかを呼び出します。  その後、XML Web サービスからのデータセットをローカルのデータセットにマージします。  次の例は、`CategoriesService` という XML Web サービスのインスタンスを作成し、その `GetCategories` メソッドを呼び出し、結果のデータセットを `DsCategories1` というローカル データセットにマージする方法を示します。  
  
    ```vb  
    Dim ws As New MyProject.localhost.CategoriesService()  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials  
    DsCategories1.Merge(ws.GetCategories())  
  
    ```  
  
    ```csharp  
    MyProject.localhost.CategoriesService ws = new MyProject.localhost.CategoriesService();  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials;  
    DsCategories1.Merge(ws.GetCategories());  
  
    ```  
  
    ```cpp  
    MyProject::localhost::CategoriesService^ ws =   
       new MyProject::localhost::CategoriesService();  
    ws->Credentials = System::Net::CredentialCache::DefaultCredentials;  
    dsCategories1->Merge(ws->GetCategories());  
    ```  
  
2.  データ ソースとデータ メンバーを引数として、<xref:System.Windows.Forms.DataGrid> コントロールの <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> メソッドを呼び出します。  データ メンバーを明示的に渡す必要がない場合は、空の文字列を渡します。  
  
    > [!NOTE]
    >  グリッドのバインドを初めて実行する場合は、このコントロールの <xref:System.Windows.Forms.DataGrid.DataSource%2A> プロパティおよび <xref:System.Windows.Forms.DataGrid.DataMember%2A> プロパティを設定できます。  ただし、これらのプロパティは、一度設定するとリセットできません。  したがって、常に <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> メソッドを使用することをお勧めします。  
  
     次の例は、プログラムで `DsCustomers1` というデータセットの Customers テーブルにバインドする方法を示しています。  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     データセットに Customers テーブル以外のテーブルが存在しない場合は、代わりに次の方法でグリッドを連結できます。  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3.  \(必要に応じて\) 適切なテーブル スタイルと列スタイルをグリッドに追加します。  テーブル スタイルがなくてもテーブルを表示できますが、その場合は最低限の書式だけが適用され、すべての列が表示されます。  
  
## 参照  
 [DataGrid コントロールの概要](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)   
 [方法 : Windows フォーム DataGrid コントロールにテーブルと列を追加する](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)   
 [DataGrid コントロール](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)   
 [Windows フォームでのデータ バインド](../../../../docs/framework/winforms/windows-forms-data-binding.md)