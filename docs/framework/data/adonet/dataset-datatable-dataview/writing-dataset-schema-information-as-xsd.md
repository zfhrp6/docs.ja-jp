---
title: "XSD としての DataSet スキーマ情報の書き込み | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# XSD としての DataSet スキーマ情報の書き込み
<xref:System.Data.DataSet> のスキーマを XML スキーマ定義言語 \(XSD\) スキーマとして書き込むと、このスキーマを XML ドキュメントに転送できます。このとき関連データを含む定義、または関連データを含まない定義ができます。  XML スキーマはファイル、ストリーム、<xref:System.Xml.XmlWriter>、または文字列に書き込むことができるため、厳密に型指定された **DataSet** を生成するときに役立ちます。  厳密に型指定された **DataSet** オブジェクトの詳細については、「[型指定された DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)」を参照してください。  
  
 テーブルの列を XML スキーマで表す方法を指定するには、<xref:System.Data.DataColumn> オブジェクトの **ColumnMapping** プロパティを使用します。  詳細については、「[DataSet 内容の XML データとしての書き込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)」の「XML 要素、属性、およびテキストへの列の割り当て」を参照してください。  
  
 **DataSet** スキーマを XML スキーマとしてファイル、ストリーム、または **XmlWriter** に書き込むには、**DataSet** の **WriteXmlSchema** メソッドを使用します。  **WriteXmlSchema** は、XML スキーマの書き込み先を指定するパラメーターを 1 つ受け取ります。  ファイル名を含んだ文字列と <xref:System.IO.StreamWriter> オブジェクトを渡して **DataSet** の XML スキーマをファイルに書き込む方法を示すコード サンプルを次に示します。  
  
```vb  
dataSet.WriteXmlSchema("Customers.xsd")  
```  
  
```csharp  
dataSet.WriteXmlSchema("Customers.xsd");  
```  
  
```vb  
Dim writer As System.IO.StreamWriter = New System.IO.StreamWriter("Customers.xsd")  
dataSet.WriteXmlSchema(writer)  
writer.Close()  
```  
  
```csharp  
System.IO.StreamWriter writer = new System.IO.StreamWriter("Customers.xsd");  
dataSet.WriteXmlSchema(writer);  
writer.Close();  
```  
  
 **DataSet** のスキーマを取得し、XML スキーマ文字列として書き込むには、次の例に示すように **GetXmlSchema** メソッドを使用します。  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## 参照  
 [DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)   
 [DataSet 内容の XML データとしての書き込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)   
 [型指定された DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)   
 [DataSets、DataTables、および DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)