---
title: "DataSet 内容の XML データとしての書き込み | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# DataSet 内容の XML データとしての書き込み
ADO.NET での XML 表現を記述する、<xref:System.Data.DataSet>、またはスキーマなし。 XML にインラインで含まれているスキーマ情報は、XML スキーマ定義言語 (XSD) を使用して記述されています。 スキーマにはテーブルの定義が含まれています、<xref:System.Data.DataSet>リレーションシップと制約の定義とします。  
  
 ときに、<xref:System.Data.DataSet>内の行、XML データとして書き込まれる、<xref:System.Data.DataSet>が現在のバージョンで書き込まれます。 ただし、<xref:System.Data.DataSet>書き込むこともできますが DiffGram としてそう、現在と行の元の値の両方が含まれています。  
  
 XML 表現、<xref:System.Data.DataSet>ファイル、ストリームに書き込むことが、 **XmlWriter**、または文字列です。 これらの選択肢では、優れた柔軟性を提供の XML 表現の転送方法を<xref:System.Data.DataSet>します。 XML 表現を取得する、<xref:System.Data.DataSet>を文字列として使用して、 **GetXml**メソッドを次の例で示すようにします。  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 **GetXml**の XML 表現を返す、<xref:System.Data.DataSet>スキーマ情報がない場合。 スキーマ情報を書き込むため、<xref:System.Data.DataSet>(XML スキーマ) として使用して、文字列に**GetXmlSchema**します。  
  
 書き込む、<xref:System.Data.DataSet>、ファイル、ストリーム、または**XmlWriter**を使用して、 **WriteXml**メソッドです。 最初のパラメーターに渡す**WriteXml** XML の出力先であります。 たとえば、ファイル名を含む文字列を渡して、 **System.IO.TextWriter**オブジェクト、およびなどです。 省略可能な&2; 番目のパラメーターを渡すことができます、**から成る**XML 出力が書き込まれる方法を指定します。  
  
 次の表に、オプションの**から成る**します。  
  
|XmlWriteMode のオプション|説明|  
|-------------------------|-----------------|  
|**IgnoreSchema**|現在の内容を書き込み、<xref:System.Data.DataSet>せず、XML スキーマの XML データとして。 既定値です。|  
|**書き込むには**|現在の内容を書き込み、<xref:System.Data.DataSet>インライン XML スキーマとして、リレーショナル構造の XML データとして。|  
|**DiffGram**|全体を書き込みます<xref:System.Data.DataSet>を DiffGram として元と現在の値を含みます。 詳細については、次を参照してください。 [Diffgram](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)します。|  
  
 XML 表現を記述するとき、<xref:System.Data.DataSet>を含む**DataRelation**オブジェクトの場合、結果の XML を持つ、関連する親要素内で入れ子になった各リレーションシップの子の行にする可能性があります。 これを実現する次のように設定します。、**入れ子になった**のプロパティ、 **DataRelation**に**true**を追加すると、 **DataRelation**に、<xref:System.Data.DataSet>します。 詳細については、次を参照してください。 [Datarelation の入れ子](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)します。  
  
 XML 表現を記述する方法の&2; つの例を次に、<xref:System.Data.DataSet>ファイルにします。 最初の例では、xml ファイルの名前を渡しますに文字列として**WriteXml**します。 2 番目の例では、 **System.IO.StreamWriter**オブジェクトです。  
  
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
 テーブルの列を XML で表現する方法を指定することができますを使用して、 **ColumnMapping**のプロパティ、 **DataColumn**オブジェクトです。 次の表に示します**MappingType**の値、 **ColumnMapping**テーブルの列と、結果の XML のプロパティです。  
  
|MappingType の値|説明|  
|-----------------------|-----------------|  
|**要素**|既定値です。 列が XML 要素として書き込まれます。このとき、ColumnName は要素名になり、列の内容は要素のテキストとして書き込まれます。 例:<br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|**属性**|列が、現在の行の XML 要素の XML 属性として書き込まれます。このとき、ColumnName は属性名になり、列の内容は属性の値として書き込まれます。 例:<br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|**SimpleContent**|列の内容が、現在の行の XML 要素のテキストとして書き込まれます。 例:<br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> なお**SimpleContent**を持つテーブルの列を設定できません**要素**列または入れ子になったリレーションです。|  
|**非表示**|列は XML 出力に書き込まれません。|  
  
## <a name="see-also"></a>関連項目  
 [データセットの XML を使用します。](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)   
 [Diffgram](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)   
 [Datarelation の入れ子化](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)   
 [XSD としての DataSet スキーマ情報の書き込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-schema-information-as-xsd.md)   
 [Dataset、Datatable、および Dataview](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET マネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)