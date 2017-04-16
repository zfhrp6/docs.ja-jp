---
title: "データの並べ替えとフィルター処理 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# データの並べ替えとフィルター処理
<xref:System.Data.DataView> には、<xref:System.Data.DataTable> のデータの並べ替えとフィルター処理を行うさまざまな方法が用意されています。  
  
-   <xref:System.Data.DataView.Sort%2A> プロパティを使用すれば、1 列または複数列の並べ替え順序を指定し、ASC \(昇順\) パラメーターと DESC \(降順\) パラメーターを含めることができます。  
  
-   <xref:System.Data.DataView.ApplyDefaultSort%2A> プロパティを使用すると、テーブルの主キー列 \(1 列または複数列\) に基づいて、昇順の並べ替え順序を自動的に作成できます。  **Sort** プロパティが null 参照または空の文字列の場合、およびテーブルに主キーが定義されている場合は、<xref:System.Data.DataView.ApplyDefaultSort%2A> だけが適用されます。  
  
-   <xref:System.Data.DataView.RowFilter%2A> プロパティを使用すると、列の値に基づいて行のサブセットを指定できます。  **RowFilter** プロパティの有効な式の詳細については、<xref:System.Data.DataColumn> クラスの <xref:System.Data.DataColumn.Expression%2A> プロパティの情報を参照してください。  
  
     データ サブセットの動的ビューの作成とは対照的に、データに対して特定のクエリの実行結果を返す場合、パフォーマンスを最大限に引き出すには、**RowFilter** プロパティを設定する代わりに **DataView** の <xref:System.Data.DataView.Find%2A> メソッドまたは <xref:System.Data.DataView.FindRows%2A> メソッドを使用します。  **RowFilter** プロパティを設定すると、データのインデックスが再作成され、アプリケーションのオーバーヘッドが増加してパフォーマンスの低下を招きます。  **RowFilter** プロパティは、データ連結アプリケーションでの使用に適しています。このアプリケーションでは、連結されたコントロールによってフィルター処理結果が表示されます。  **Find** メソッドと **FindRows** メソッドでは、現在のインデックスが使用されます。このため、インデックスを再作成する必要はありません。  **Find** メソッドと **FindRows** メソッドの詳細については、「[行の検索](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md)」を参照してください。  
  
-   <xref:System.Data.DataView.RowStateFilter%2A> プロパティを使用して、表示する行バージョンを指定できます。  **DataView** は、基になる行の **RowState** に従って、暗黙的に行バージョンを公開します。  たとえば、**RowStateFilter** が **DataViewRowState.Deleted** に設定されている場合、**DataView** は行バージョンが **Original** の **Deleted** 行をすべて公開します。これは、**Current** 行バージョンが存在しないためです。  **DataRowView** の **RowVersion** プロパティを使用すると、公開される行のバージョンを確認できます。  
  
     **DataViewRowState** のオプションを次の表に示します。  
  
    |DataViewRowState のオプション|説明|  
    |-----------------------------|--------|  
    |**CurrentRows**|**Current** 行バージョンのすべての **Unchanged** 行、**Added** 行、および **Modified** 行です。  既定値です。|  
    |**Added**|**Current** 行バージョンのすべての **Added** 行です。|  
    |**Deleted**|**Original** 行バージョンのすべての **Deleted** 行です。|  
    |**ModifiedCurrent**|**Current** 行バージョンのすべての **Modified** 行です。|  
    |**ModifiedOriginal**|**Original**  行バージョンのすべての **Modified** 行です。|  
    |**なし**|行がありません。|  
    |**OriginalRows**|**Original** 行バージョンのすべての **Unchanged** 行、**Modified** 行、および **Deleted** 行です。|  
    |**Unchanged**|**Current** 行バージョンのすべての **Unchanged** 行です。|  
  
 行状態と行バージョンの詳細については、「[行の状態とバージョン](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)」を参照してください。  
  
 在庫数が標準在庫数以下である製品を、仕入先 ID \(supplier ID\) で並べ替え、さらに製品名 \(product name\) で並べ替えたビューを作成するコード サンプルを次に示します。  
  
```vb  
Dim prodView As DataView = New DataView(prodDS.Tables("Products"), _  
   "UnitsInStock <= ReorderLevel", _  
   "SupplierID, ProductName", _  
   DataViewRowState.CurrentRows)  
  
```  
  
```csharp  
DataView prodView = new DataView(prodDS.Tables["Products"],  
   "UnitsInStock <= ReorderLevel",  
   "SupplierID, ProductName",  
   DataViewRowState.CurrentRows);  
```  
  
## 参照  
 <xref:System.Data.DataViewRowState>   
 <xref:System.Data.DataColumn.Expression%2A?displayProperty=fullName>   
 <xref:System.Data.DataTable>   
 <xref:System.Data.DataView>   
 [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)