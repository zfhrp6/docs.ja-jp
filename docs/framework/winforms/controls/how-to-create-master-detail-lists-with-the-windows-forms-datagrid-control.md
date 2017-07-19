---
title: "方法 : Windows フォーム DataGrid コントロールを使用してマスター/詳細リストを作成する | Microsoft Docs"
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
  - "DataGrid コントロール [Windows フォーム], マスター/詳細リスト"
  - "マスター/詳細リスト"
  - "関連テーブル, 表示 (DataGrid コントロールで)"
ms.assetid: 20388c6a-94f9-4d96-be18-8c200491247f
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : Windows フォーム DataGrid コントロールを使用してマスター/詳細リストを作成する
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 <xref:System.Data.DataSet> に一連の互いに関連するテーブルが含まれている場合は、2 つの <xref:System.Windows.Forms.DataGrid> コントロールを使用してデータをマスター\/詳細形式で表示できます。  一方の <xref:System.Windows.Forms.DataGrid> をマスター グリッドに指定し、もう一方を詳細グリッドに指定します。  マスター リストのエントリを選択すると、関連するすべての子エントリが詳細リストに表示されます。  たとえば、<xref:System.Data.DataSet> に Customers テーブルおよび関連する Orders テーブルが含まれている場合は、Customers テーブルをマスター グリッドに指定し、Orders テーブルを詳細グリッドに指定します。  マスター グリッドから顧客が選択されると、Orders テーブル内でその顧客に関連するすべての注文が、詳細グリッドに表示されます。  
  
### プログラムでマスター\/詳細リレーションシップを設定するには  
  
1.  2 つの <xref:System.Windows.Forms.DataGrid> コントロールを新規作成し、そのプロパティを設定します。  
  
2.  データセットにテーブルを追加します。  
  
3.  作成するリレーションシップを表す <xref:System.Data.DataRelation> 型の変数を宣言します。  
  
4.  リレーションシップの名前と、2 つのテーブルを結び付けるテーブル、列、および項目を指定して、リレーションシップをインスタンス化します。  
  
5.  <xref:System.Data.DataSet> オブジェクトの <xref:System.Data.DataSet.Relations%2A> コレクションにリレーションシップを追加します。  
  
6.  <xref:System.Windows.Forms.DataGrid> の <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> メソッドを使用して、各グリッドを <xref:System.Data.DataSet> にバインドします。  
  
     次の例は、前に生成した <xref:System.Data.DataSet> \(`ds`\) 内の Customers テーブルと Orders テーブルの間にマスター\/詳細リレーションシップを設定する方法を示しています。  
  
    ```vb  
    Dim myDataRelation As DataRelation  
    myDataRelation = New DataRelation _  
       ("CustOrd", ds.Tables("Customers").Columns("CustomerID"), _  
       ds.Tables("Orders").Columns("CustomerID"))  
    ' Add the relation to the DataSet.  
    ds.Relations.Add(myDataRelation)  
    GridOrders.SetDataBinding(ds, "Customers")  
    GridDetails.SetDataBinding(ds, "Customers.CustOrd")  
  
    ```  
  
    ```csharp  
    DataRelation myDataRelation;  
    myDataRelation = new DataRelation("CustOrd", ds.Tables["Customers"].Columns["CustomerID"], ds.Tables["Orders"].Columns["CustomerID"]);  
    // Add the relation to the DataSet.  
    ds.Relations.Add(myDataRelation);  
    GridOrders.SetDataBinding(ds,"Customers");  
    GridDetails.SetDataBinding(ds,"Customers.CustOrd");  
  
    ```  
  
    ```cpp  
    DataRelation^ myDataRelation;  
    myDataRelation = gcnew DataRelation("CustOrd",  
       ds->Tables["Customers"]->Columns["CustomerID"],  
       ds->Tables["Orders"]->Columns["CustomerID"]);  
    // Add the relation to the DataSet.  
    ds->Relations->Add(myDataRelation);  
    GridOrders->SetDataBinding(ds, "Customers");  
    GridDetails->SetDataBinding(ds, "Customers.CustOrd");  
    ```  
  
## 参照  
 [DataGrid コントロール](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)   
 [DataGrid コントロールの概要](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)   
 [方法 : データ ソースに Windows フォーム DataGrid コントロールをバインドする](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)