---
title: "列の推論"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ba06bce55db53de1da1c07d2a6451d5664fa23bf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="inferring-columns"></a>列の推論
ADO.NET は、<xref:System.Data.DataSet> のテーブルとして推論する要素を、XML ドキュメントから決定した後、それらのテーブルの列を推論します。 ADO.NET 2.0 導入ごとに厳密に型指定されたデータ型を推測する新しいスキーマ推論エンジン**simpleType**要素。 以前のバージョンで、データ型、推論された**simpleType**要素が常に**xsd:string**です。  
  
## <a name="migration-and-backward-compatibility"></a>移行および下位互換性  
 **ReadXml**メソッドが型の引数を受け取る**InferSchema**です。 この引数を使用することにより、以前のバージョンと互換性のある推論方法を指定することができます。 使用可能な値、 **InferSchema**列挙体は、次の表に表示されます。  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 単純型を <xref:System.String> として常に推論することで下位互換性を提供します。  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 厳密に型指定されたデータ型を推論します。 <xref:System.Data.DataTable> で使用した場合、例外をスローします。  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 インライン スキーマを無視し、データを既存の <xref:System.Data.DataSet> スキーマに読み取ります。  
  
## <a name="attributes"></a>属性  
 定義されている[テーブルの推論](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md)属性を持つ要素はテーブルとして推論されます。 その要素の属性は、そのテーブルの列として推論されます。 **ColumnMapping**列のプロパティ設定されます**MappingType.Attribute**スキーマが XML に書き戻さか、列名が属性として書き込まれますことを確認するためです。 属性の値は、テーブルの行に格納されます。 たとえば、次のような XML があるとします。  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 推論プロセスという名前のテーブルが生成されます**Element1** 、2 つの列を持つ**attr1**と**attr2**です。 **ColumnMapping**両方の列のプロパティ設定されます**MappingType.Attribute**です。  
  
 **データセット:** DocumentElement  
  
 **Table:** Element1  
  
|attr1|attr2|  
|-----------|-----------|  
|value1|value2|  
  
## <a name="elements-without-attributes-or-child-elements"></a>属性または子の要素を持たない要素  
 要素に子の要素または属性がない場合、その要素は列として推論されます。 **ColumnMapping**列のプロパティ設定されます**MappingType.Element**です。 子の要素のテキストは、テーブルの行に格納されます。 たとえば、次のような XML があるとします。  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 推論プロセスという名前のテーブルが生成されます**Element1** 、2 つの列を持つ**ChildElement1**と**ChildElement2**です。 **ColumnMapping**両方の列のプロパティ設定されます**MappingType.Element**です。  
  
 **データセット:** DocumentElement  
  
 **Table:** Element1  
  
|ChildElement1|ChildElement2|  
|-------------------|-------------------|  
|Text1|Text2|  
  
## <a name="see-also"></a>関連項目  
 [XML からの DataSet リレーショナル構造の推論](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [XML からの DataSet の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [XML からの DataSet スキーマ情報の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
