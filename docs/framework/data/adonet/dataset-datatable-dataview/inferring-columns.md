---
title: "列の推論 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 列の推論
ADO.NET は、<xref:System.Data.DataSet> のテーブルとして推論する要素を、XML ドキュメントから決定した後、それらのテーブルの列を推論します。  ADO.NET 2.0 では、各 **simpleType** 要素の厳密に型指定されたデータ型を推論する新しいスキーマ推論エンジンが導入されました。  以前のバージョンでは、推論される **simpleType** 要素のデータ型は、常に **xsd:string** でした。  
  
## 移行および下位互換性  
 **ReadXml** メソッドは、**InferSchema** 型の引数を取ります。  この引数を使用することにより、以前のバージョンと互換性のある推論方法を指定することができます。  **InferSchema** 列挙体で使用できる値を、次の表に示します。  
  
 <xref:System.Data.XmlReadMode>  
 単純型を <xref:System.String> として常に推論することで下位互換性を提供します。  
  
 <xref:System.Data.XmlReadMode>  
 厳密に型指定されたデータ型を推論します。  <xref:System.Data.DataTable> で使用した場合、例外をスローします。  
  
 <xref:System.Data.XmlReadMode>  
 インライン スキーマを無視し、データを既存の <xref:System.Data.DataSet> スキーマに読み取ります。  
  
## 属性  
 「[テーブルの推論](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md)」で説明したとおり、属性を持つ要素は、テーブルとして推論されます。  その要素の属性は、そのテーブルの列として推論されます。  スキーマが XML に書き戻される場合に、列の名前が確実に属性として書き込まれるように、推論された列の **ColumnMapping** プロパティは **MappingType.Attribute** に設定されます。  属性の値は、テーブルの行に格納されます。  たとえば、次のような XML があるとします。  
  
```  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 推論プロセスにより、**attr1** および **attr2** という 2 つの列を持つ **Element1** という名前のテーブルが生成されます。  2 つの列の **ColumnMapping** プロパティは、**MappingType.Attribute** に設定されます。  
  
 **DataSet:** DocumentElement  
  
 **Table:** Element1  
  
|attr1|attr2|  
|-----------|-----------|  
|value1|value2|  
  
## 属性または子の要素を持たない要素  
 要素に子の要素または属性がない場合、その要素は列として推論されます。  列の **ColumnMapping** プロパティは、**MappingType.Element** に設定されます。  子の要素のテキストは、テーブルの行に格納されます。  たとえば、次のような XML があるとします。  
  
```  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 推論プロセスにより、**ChildElement1** および **ChildElement2** という 2 つの列を持つ **Element1** という名前のテーブルが生成されます。  2 つの列の **ColumnMapping** プロパティは、**MappingType.Element** に設定されます。  
  
 **DataSet:** DocumentElement  
  
 **Table:** Element1  
  
|ChildElement1|ChildElement2|  
|-------------------|-------------------|  
|Text1|Text2|  
  
## 参照  
 [XML からの DataSet リレーショナル構造の推論](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)   
 [XML からの DataSet の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)   
 [XML の DataSet スキーマ情報の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)   
 [DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)   
 [DataSets、DataTables、および DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)