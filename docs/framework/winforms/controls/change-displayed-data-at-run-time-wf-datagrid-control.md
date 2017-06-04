---
title: "方法 : Windows フォーム DataGrid コントロールに表示されるデータを実行時に変更する | Microsoft Docs"
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
  - "セル, 変更 (DataGrid セル値を)"
  - "DataGrid コントロール [Windows フォーム], データ バインド"
  - "DataGrid コントロール [Windows フォーム], 動的に変更 (実行時に)"
ms.assetid: 0c7a6d00-30de-416e-8223-0a81ddb4c1f8
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : Windows フォーム DataGrid コントロールに表示されるデータを実行時に変更する
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 デザイン時の機能を使用して Windows フォーム <xref:System.Windows.Forms.DataGrid> を作成した後で、グリッドの <xref:System.Data.DataSet> オブジェクトの要素を実行時に動的に変更できます。  これには、テーブルの個別の値を変更する場合と、<xref:System.Windows.Forms.DataGrid> コントロールに連結するデータ ソースを変更する場合があります。  個別の値の変更は、<xref:System.Windows.Forms.DataGrid> コントロールではなく、<xref:System.Data.DataSet> オブジェクトによって行います。  
  
### プログラムでデータを変更するには  
  
1.  データを変更する <xref:System.Data.DataSet> オブジェクトのテーブル、および変更する行とフィールドを指定し、セルを新しい値に設定します。  
  
    > [!NOTE]
    >  <xref:System.Data.DataSet> の最初のテーブルまたはテーブルの最初の行を指定するには、0 を使用します。  
  
     次の例に `Button1` をクリックしてデータセットの最初のテーブルの最初の行の 2 番目のエントリを変更する方法を示します。  <xref:System.Data.DataSet> \(`ds`\) とテーブル \(`0` and`1`\) は既に作成済みです。  
  
    ```vb  
    Protected Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       ds.tables(0).rows(0)(1) = "NewEntry"  
    End Sub  
  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       ds.Tables[0].Rows[0][1]="NewEntry";  
    }  
  
    ```  
  
    ```cpp  
    private:   
       void button1_Click(System::Object^ sender, System::EventArgs^ e)  
       {  
          dataSet1->Tables[0]->Rows[0][1] = "NewEntry";  
       }  
    ```  
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]、[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) フォームのコンストラクターに次のコードを挿入してイベント ハンドラーを登録します。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     実行時に、<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> メソッドを使用して、<xref:System.Windows.Forms.DataGrid> コントロールを異なるデータ ソースに連結できます。  たとえば、複数の [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] データ コントロールをそれぞれ異なるデータベースに接続できます。  
  
### プログラムでデータ ソースを変更するには  
  
1.  <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> メソッドに、連結するデータ ソースおよびテーブルの名前を設定します。  
  
     <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> メソッドを使用して、データ ソースを Pubs データベースの Authors テーブルに接続されている [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] データ コントロール \(adoPubsAuthors\) に変更する例を次に示します。  
  
    ```vb  
    Private Sub ResetSource()  
       DataGrid1.SetDataBinding(adoPubsAuthors, "Authors")  
    End Sub  
  
    ```  
  
    ```csharp  
    private void ResetSource()  
    {  
       DataGrid1.SetDataBinding(adoPubsAuthors, "Authors");  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void ResetSource()  
       {  
          dataGrid1->SetDataBinding(adoPubsAuthors, "Authors");  
       }  
    ```  
  
## 参照  
 [ADO.NET の DataSet](../../../../docs/framework/data/adonet/ado-net-datasets.md)   
 [方法 : Windows フォーム DataGrid コントロールの列を削除するまたは非表示にする](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)   
 [方法 : Windows フォーム DataGrid コントロールにテーブルと列を追加する](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)   
 [方法 : データ ソースに Windows フォーム DataGrid コントロールをバインドする](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)