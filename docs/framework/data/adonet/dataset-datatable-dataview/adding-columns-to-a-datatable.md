---
title: "DataTable への列の追加 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# DataTable への列の追加
<xref:System.Data.DataTable> には、テーブルの **Columns** プロパティによって参照される <xref:System.Data.DataColumn> オブジェクトのコレクションが格納されます。  この列のコレクションと制約によって、テーブルのスキーマ \(構造\) が定義されます。  
  
 テーブル内で **DataColumn** オブジェクトを作成するには、**DataColumn** コンストラクターを使用するか、または <xref:System.Data.DataColumnCollection> の 1 つである、テーブルの **Columns** プロパティの **Add** メソッドを呼び出します。  **Add** メソッドは、オプションの **ColumnName**、**DataType**、**Expression** の各引数を受け取り、新しい **DataColumn** をコレクションのメンバーとして作成します。  また、このメソッドは既存の **DataColumn** オブジェクトを受け取り、このオブジェクトをコレクションに追加します。必要な場合には、追加された **DataColumn** への参照を返します。  **DataTable** オブジェクトはデータ ソースに依存しないため、**DataColumn** のデータ型を指定するときには、.NET Framework 型が使用されます。  
  
 **DataTable** に 4 つの列を追加する例を次に示します。  
  
```vb  
Dim workTable As DataTable = New DataTable("Customers")  
  
Dim workCol As DataColumn = workTable.Columns.Add( _  
    "CustID", Type.GetType("System.Int32"))  
workCol.AllowDBNull = false  
workCol.Unique = true  
  
workTable.Columns.Add("CustLName", Type.GetType("System.String"))  
workTable.Columns.Add("CustFName", Type.GetType("System.String"))  
workTable.Columns.Add("Purchases", Type.GetType("System.Double"))  
  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
  
DataColumn workCol = workTable.Columns.Add("CustID", typeof(Int32));  
workCol.AllowDBNull = false;  
workCol.Unique = true;  
  
workTable.Columns.Add("CustLName", typeof(String));  
workTable.Columns.Add("CustFName", typeof(String));  
workTable.Columns.Add("Purchases", typeof(Double));  
```  
  
 この例では、**DBNull** 値を許可せずに値を一意の値に制約するように、**CustID** 列のプロパティが設定されています。  ただし、**CustID** 列をテーブルの主キー列として定義した場合、**AllowDBNull** プロパティは自動的に **false** に設定され、**Unique** プロパティは自動的に **true** に設定されます。  詳細については、「[主キーの定義](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)」を参照してください。  
  
> [!CAUTION]
>  列名が指定されていない列を **DataColumnCollection** に追加する場合、この列には "Column1" から始まるインクリメンタル既定名 Column*N* が割り当てられます。  列名を指定するときには、"Column*N*" の命名規則を使用しないことをお勧めします。これは、指定した名前が **DataColumnCollection** に既に存在する既定の列名と競合しないようにするためです。  指定した名前が既に存在する場合は、例外がスローされます。  
  
 <xref:System.Xml.XLinq.XElement> を、<xref:System.Data.DataTable> 内の <xref:System.Data.DataColumn> の <xref:System.Data.DataColumn.DataType%2A> として使用すると、データを読み取るときに XML シリアル化が機能しません。  たとえば、`DataTable.WriteXml` メソッドを使用して <xref:System.Xml.XmlDocument> を書き込むと、XML へのシリアル化で <xref:System.Xml.XLinq.XElement> に親ノードが追加されます。  この問題に対処するには、<xref:System.Xml.XLinq.XElement> の代わりに <xref:System.Data.SqlTypes.SqlXml> 型を使用します。  `ReadXml` および `WriteXml` は、<xref:System.Data.SqlTypes.SqlXml> で適切に機能します。  
  
## 参照  
 <xref:System.Data.DataColumn>   
 <xref:System.Data.DataColumnCollection>   
 <xref:System.Data.DataTable>   
 [DataTable スキーマの定義](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)   
 [DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)