---
title: "厳密に型指定された DataSet の生成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 54333cbf-bb43-4314-a7d4-6dc1dd1c44b3
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# 厳密に型指定された DataSet の生成
XML スキーマ定義言語 \(XSD\) 標準に準拠する XML スキーマがあれば、[!INCLUDE[winsdklong](../../../../../includes/winsdklong-md.md)] に付属の XSD.exe ツールを使用して、厳密に型指定された <xref:System.Data.DataSet> を生成できます。  
  
 \(データベース テーブルから xsd を作成するには、「<xref:System.Data.DataSet.WriteXmlSchema%2A>」または「[Visual Studio でのデータセットの操作](http://msdn.microsoft.com/library/8bw9ksd6.aspx)」 を参照してください。\)  
  
 XSD.exe ツールを使用して **DataSet** を生成する構文を次のコードで示します。  
  
```  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 この構文では、`/d` ディレクティブが **DataSet** を生成することを知らせます。また、`/l:` は使用する言語 \(C\#、Visual Basic .NET など\) をツールに知らせます。  オプションの `/eld` ディレクティブを指定すると、生成された **DataSet** に対し、[!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)] を使用してクエリを実行できます。このオプションは、`/d` オプションと組み合わせて指定します。  詳細については、「[Querying Typed DataSets](../../../../../docs/framework/data/adonet/querying-typed-datasets.md)」を参照してください。  オプションの `/n:` ディレクティブは、**XSDSchema.Namespace** と呼ばれる **DataSet** の名前空間も生成することをツールに知らせます。  コマンドの出力は XSDSchemaFileName.cs で、ADO.NET アプリケーションでコンパイルおよび使用できます。  生成されたコードをライブラリまたはモジュールとしてコンパイルできます。  
  
 C\# コンパイラ \(csc.exe\) を使用して、生成されたコードをライブラリとしてコンパイルする構文を次のコードで示します。  
  
```  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 `/t:` ディレクティブはライブラリとしてコンパイルすることをツールに知らせ、`/r:` ディレクティブはコンパイルに必要な依存ライブラリを指定します。  コマンドの出力は XSDSchemaFileName.dll で、`/r:` ディレクティブによる ADO.NET アプリケーションのコンパイル時にコンパイラに渡すことができます。  
  
 ADO.NET アプリケーションの XSD.exe に渡された名前空間にアクセスする構文を次のコードで示します。  
  
```vb  
Imports XSDSchema.Namespace  
  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 **CustomerDataSet** という名前の型指定された **DataSet** を使用して、**Northwind** データベースから顧客リストを読み込むコード サンプルを次に示します。  **Fill** メソッドを使用してデータが読み込まれると、例では、型指定された **CustomersRow** \(**DataRow**\) オブジェクトを使用して、**Customers** テーブルの各顧客をループします。  これにより、**DataColumnCollection** を経由せずに **CustomerID** 列に直接アクセスできます。  
  
```vb  
Dim customers As CustomerDataSet= New CustomerDataSet()  
Dim adapter As SqlDataAdapter New SqlDataAdapter( _  
  "SELECT * FROM dbo.Customers;", _  
  "Data Source=(local);Integrated " & _  
  "Security=SSPI;Initial Catalog=Northwind")  
  
adapter.Fill(customers, "Customers")  
  
Dim customerRow As CustomerDataSet.CustomersRow  
For Each customerRow In customers.Customers  
  Console.WriteLine(customerRow.CustomerID)  
Next  
  
```  
  
```csharp  
CustomerDataSet customers = new CustomerDataSet();  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT * FROM dbo.Customers;",  
  "Data Source=(local);Integrated " +  
  "Security=SSPI;Initial Catalog=Northwind");  
  
adapter.Fill(customers, "Customers");  
  
foreach(CustomerDataSet.CustomersRow customerRow in customers.Customers)  
  Console.WriteLine(customerRow.CustomerID);  
```  
  
 例に使用された XML スキーマを次に示します。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet" xmlns="" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
## 参照  
 <xref:System.Data.DataColumnCollection>   
 <xref:System.Data.DataSet>   
 [型指定された DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)   
 [DataSets、DataTables、および DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)