---
title: "DataSet 内容の XML データとしての書き込み"
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
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9b1250d616ad5835fccd1a3acbf0b8a759c34181
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="writing-dataset-contents-as-xml-data"></a>DataSet 内容の XML データとしての書き込み
ADO.NET では、<xref:System.Data.DataSet> の XML 表現を記述することができます。このとき、 にスキーマが含まれていても、含まれていなくてもかまいません。 XML にインラインで含まれているスキーマ情報は、XML スキーマ定義言語 (XSD) を使用して記述されています。 スキーマには、リレーション定義および制約定義と、<xref:System.Data.DataSet> のテーブル定義が含まれています。  
  
 <xref:System.Data.DataSet> が XML データとして書き込まれると、<xref:System.Data.DataSet> の行は現在のバージョンで書き込まれます。 ただし、行の現在の値と元の値の両方を含めるには、<xref:System.Data.DataSet> を DiffGram として書き込みます。  
  
 XML 表現、<xref:System.Data.DataSet>ファイル、ストリームに書き込むことができます、 **XmlWriter**、または string です。 複数の書き込み先があることから、<xref:System.Data.DataSet> の XML 表現の転送方法を柔軟に変更できます。 XML 表現を取得する、<xref:System.Data.DataSet>を文字列として使用して、 **GetXml**メソッドの次の例に示すようにします。  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 **GetXml**の XML 表現を返します、<xref:System.Data.DataSet>スキーマ情報がない場合。 スキーマ情報を書き込む、 <xref:System.Data.DataSet> (XML スキーマ) として使用して、文字列に**GetXmlSchema**です。  
  
 書き込む、<xref:System.Data.DataSet>ファイル、ストリーム、または**XmlWriter**を使用して、 **WriteXml**メソッドです。 最初のパラメーターに渡す**WriteXml** XML 出力の先であります。 たとえば、ファイル名を含む文字列を渡す、 **System.IO.TextWriter**オブジェクト、およびなどです。 省略可能な 2 番目のパラメーターを渡すことができます、 **XmlWriteMode**に XML 出力を書き込む方法を指定します。  
  
 次の表は、オプションの**XmlWriteMode**です。  
  
|XmlWriteMode のオプション|説明|  
|-------------------------|-----------------|  
|**IgnoreSchema**|<xref:System.Data.DataSet> の現在の内容を XML スキーマを含まない XML データとして書き込みます。 既定値です。|  
|**WriteSchema**|<xref:System.Data.DataSet> の現在の内容を XML データとして書き込みます。このとき、リレーショナル構造がインライン XML スキーマとして書き込まれます。|  
|**DiffGram**|元の値と現在の値を含め、<xref:System.Data.DataSet> 全体を DiffGram として書き込みます。 詳細については、次を参照してください。 [Diffgram](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)です。|  
  
 XML 表現を記述する場合、<xref:System.Data.DataSet>を格納している**DataRelation**オブジェクト、結果の XML 要素が関連する親要素内で入れ子になった各リレーションシップの子行があるにする可能性があります。 これを実現するには、設定、**入れ子になった**のプロパティ、 **DataRelation**に**true**を追加すると、 **DataRelation** に<xref:System.Data.DataSet>. 詳細については、次を参照してください。 [Datarelation の入れ子](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)です。  
  
 <xref:System.Data.DataSet> の XML 表現をファイルに書き込む 2 つの例を次に示します。 最初の例は、文字列として、結果の XML ファイルの名前を渡します**WriteXml**です。 2 番目の例では、 **System.IO.StreamWriter**オブジェクト。  
  
```vb  
custDS.WriteXml("Customers.xml", XmlWriteMode.WriteSchema)  
```  
  
```csharp  
custDS.WriteXml("Customers.xml", XmlWriteMode.WriteSchema);  
```  
  
```vb  
Dim xmlSW As System.IO.StreamWriter = New System.IO.StreamWriter("Customers.xml")  
custDS.WriteXml(xmlSW, XmlWriteMode.WriteSchema)  
xmlSW.Close()  
```  
  
```csharp  
System.IO.StreamWriter xmlSW = new System.IO.StreamWriter("Customers.xml");  
custDS.WriteXml(xmlSW, XmlWriteMode.WriteSchema);  
xmlSW.Close();  
```  
  
## <a name="mapping-columns-to-xml-elements-attributes-and-text"></a>XML 要素、属性、およびテキストへの列の割り当て  
 テーブルの列を XML で表現する方法を指定することができますを使用して、 **ColumnMapping**のプロパティ、 **DataColumn**オブジェクト。 次の表は、さまざまな**MappingType**の値を**ColumnMapping**テーブルの列、および結果の XML のプロパティです。  
  
|MappingType の値|説明|  
|-----------------------|-----------------|  
|**要素**|既定値です。 列が XML 要素として書き込まれます。このとき、ColumnName は要素名になり、列の内容は要素のテキストとして書き込まれます。 例:<br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|**属性**|列が、現在の行の XML 要素の XML 属性として書き込まれます。このとき、ColumnName は属性名になり、列の内容は属性の値として書き込まれます。 例:<br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|**SimpleContent**|列の内容が、現在の行の XML 要素のテキストとして書き込まれます。 例:<br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> なお**SimpleContent**を持つテーブルの列を設定できません**要素**列または入れ子にされたリレーションシップです。|  
|**Hidden**|列は XML 出力に書き込まれません。|  
  
## <a name="see-also"></a>参照  
 [DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)  
 [DataRelation の入れ子化](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 [XSD としての DataSet スキーマ情報の書き込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-schema-information-as-xsd.md)  
 [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
