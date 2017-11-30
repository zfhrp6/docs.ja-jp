---
title: "XSD としての DataSet スキーマ情報の書き込み"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: dde8a16ee0fbd86dacf6125c9a02209a794a5b74
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="writing-dataset-schema-information-as-xsd"></a>XSD としての DataSet スキーマ情報の書き込み
<xref:System.Data.DataSet> のスキーマを XML スキーマ定義言語 (XSD) スキーマとして書き込むと、このスキーマを XML ドキュメントに転送できます。このとき関連データを含む定義、または関連データを含まない定義ができます。 XML スキーマは、ストリーム、ファイルに書き込むことが、 <xref:System.Xml.XmlWriter>、または文字列が厳密に型を生成するために役立ちます**データセット**です。 詳細については厳密に型指定された**データセット**、オブジェクトを参照してください[型指定されたデータセット](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)です。  
  
 XML スキーマでテーブルの列を表現する方法を指定することができますを使用して、 **ColumnMapping**のプロパティ、<xref:System.Data.DataColumn>オブジェクト。 詳細についてを参照してください「列に XML 要素、属性、およびテキストのマッピングを」[書き込み DataSet の内容を XML データとして](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)です。  
  
 スキーマを記述する、**データセット**をファイルに、XML スキーマとして、ストリームまたは**XmlWriter**を使用して、 **WriteXmlSchema**のメソッド、**データセット**です。 **WriteXmlSchema**結果の XML スキーマのコピー先を指定する 1 つのパラメーターを受け取ります。 コード例を以下の XML スキーマを記述する方法、**データセット**ファイル名を含む文字列を渡すことによってファイルへと<xref:System.IO.StreamWriter>オブジェクト。  
  
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
  
 スキーマを取得する、**データセット**、XML スキーマ文字列として書き込むと、使用、 **GetXmlSchema**メソッドを次の例で示すようにします。  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a>関連項目  
 [DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [XML データとしてデータセットのコンテンツの書き込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 [型指定されたデータセット](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
