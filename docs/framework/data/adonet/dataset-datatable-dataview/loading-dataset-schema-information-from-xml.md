---
title: "XML の DataSet スキーマ情報の読み込み"
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
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e41eb1168774a5ebfc17147f65901de0e432789f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="loading-dataset-schema-information-from-xml"></a>XML の DataSet スキーマ情報の読み込み
スキーマ、 <xref:System.Data.DataSet> (そのテーブル、列、リレーション、および制約) はプログラムでは、によって作成された、**塗りつぶし**または**FillSchema**のメソッド、<xref:System.Data.Common.DataAdapter>から読み込まれたか、XML ドキュメントです。 読み込む**データセット**スキーマ情報、XML ドキュメントから、いずれかを使用して、 **ReadXmlSchema**または**InferXmlSchema**のメソッド、**データセット**. **ReadXmlSchema**の読み込みまたは推論することができます**データセット**XML スキーマ定義言語 (XSD) スキーマ、またはインライン XML スキーマを持つ XML ドキュメントを含むドキュメントからスキーマ情報。 **InferXmlSchema**指定した特定の XML 名前空間を無視しているときに、XML ドキュメントからスキーマを推論することができます。  
  
> [!NOTE]
>  テーブルの順序で、**データセット**を転送する Web サービスまたは XML シリアル化を使用する場合は保持されませんが、**データセット**インメモリ (入れ子になったリレーション) などの XSD コンス トラクターを使用して作成されました。 そのための受信者、**データセット**テーブルの例ではこの順序に依存しないようにします。 ただし、テーブルの順序は常に保持される場合のスキーマ、**データセット**メモリ内で作成されているのではなく、XSD ファイルから読み取られた転送されています。  
  
## <a name="readxmlschema"></a>ReadXmlSchema  
 スキーマを読み込む、**データセット**すべてのデータを読み込むことがなく、XML ドキュメントからを使用して、 **ReadXmlSchema**のメソッド、**データセット**です。 **ReadXmlSchema**作成**データセット**スキーマの XML スキーマ定義言語 (XSD) スキーマを使用して定義します。  
  
 **ReadXmlSchema**メソッドを 1 つの引数でのファイル名、ストリーム、または**XmlReader**に読み込む XML ドキュメントを含むです。 この XML ドキュメントには、スキーマだけが含まれているか、またはデータのある XML 要素と共にスキーマがインラインで含まれています。 XML スキーマとインライン スキーマの作成方法の詳細については、「[派生した DataSet リレーショナル構造の XML スキーマ (XSD) から](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)です。  
  
 XML ドキュメントを渡す場合**ReadXmlSchema**インライン スキーマ情報を含まない**ReadXmlSchema** XML ドキュメント内の要素からスキーマを推論します。 場合、**データセット**スキーマを既に含む現在のスキーマが既に存在しない場合は、新しいテーブルを追加することによって拡張されます。 既存のテーブルには新しい列は追加されません。 既に追加されている列が存在する場合、**データセット**が列と互換性のない型が見つかりません、xml で、例外がスローされます。 方法の詳細について**ReadXmlSchema**スキーマを生成、XML ドキュメントから、次を参照してください。[推論 DataSet リレーショナル構造の XML から](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)です。  
  
 **ReadXmlSchema**で読み込みまたは推論のスキーマのみ、**データセット**、 **ReadXml**のメソッド、**データセット**読み込まれるかまたは両方を推論スキーマと XML ドキュメントに含まれるデータ。 詳細については、次を参照してください。 [XML からの DataSet の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)です。  
  
 次のコード例を読み込む方法を表示する、**データセット**を XML ドキュメントまたはストリームからのスキーマです。 最初の例に渡される XML スキーマ ファイル名、 **ReadXmlSchema**メソッドです。 2 番目の例、 **System.IO.StreamReader**です。  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema("schema.xsd")  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema("schema.xsd");  
```  
  
```vb  
Dim xmlStream As System.IO.StreamReader = New System.IO.StreamReader ("schema.xsd");  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema(xmlStream)  
xmlStream.Close()  
```  
  
```csharp  
System.IO.StreamReader xmlStream = new System.IO.StreamReader("schema.xsd");  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema(xmlStream);  
xmlStream.Close();  
```  
  
## <a name="inferxmlschema"></a>InferXmlSchema  
 指示することも、**データセット**を使用して XML ドキュメントからスキーマを推論、 **InferXmlSchema**のメソッド、**データセット**です。 **InferXmlSchema**両方と同じ機能**ReadXml**で、 **XmlReadMode**の**InferSchema** (データを読み込むし、スキーマを推論)、および**ReadXmlSchema**読み取られているドキュメントにインライン スキーマが含まれていない場合。 ただし、 **InferXmlSchema**を無視するように、スキーマを推論する際に特定の XML 名前空間を指定できる追加機能を提供します。 **InferXmlSchema**では 2 つの必要な引数: ファイル名、ストリームで指定された、XML ドキュメントの場所または**XmlReader**; と、操作によって無視される XML 名前空間の文字列配列。  
  
 たとえば、次のような XML があるとします。  
  
```xml  
<NewDataSet xmlns:od="urn:schemas-microsoft-com:officedata">  
<Categories>  
  <CategoryID od:adotype="3">1</CategoryID>   
  <CategoryName od:maxLength="15" od:adotype="130">Beverages</CategoryName>   
  <Description od:adotype="203">Soft drinks and teas</Description>   
</Categories>  
<Products>  
  <ProductID od:adotype="20">1</ProductID>   
  <ReorderLevel od:adotype="3">10</ReorderLevel>   
  <Discontinued od:adotype="11">0</Discontinued>   
</Products>  
</NewDataSet>  
```  
  
 上記の XML ドキュメント内の要素に指定された属性のため両方、 **ReadXmlSchema**メソッドおよび**ReadXml**メソッドを**XmlReadMode**の**InferSchema** 、ドキュメント内のすべての要素のテーブルの作成は:**カテゴリ**、 **CategoryID**、 **CategoryName**、**説明**、**製品**、 **ProductID**、 **ReorderLevel**、および**提供が中止されました。**. (詳細については、次を参照してください[推論 DataSet リレーショナル構造の XML から](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)。)。適切な構造体のみを作成すること、ただし、**カテゴリ**と**製品**テーブルを作成し、 **CategoryID**、 **CategoryName**、および**説明**内の列、**カテゴリ**テーブル、および**ProductID**、 **ReorderLevel**、および**生産中止**内の列、**製品**テーブル。 を確保するため、推論されるスキーマが XML 要素で指定された属性を無視することを使用して、 **InferXmlSchema**メソッドの XML 名前空間を指定して**officedata**無視するように、のように、次の例です。  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a>参照  
 [DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [XML スキーマ (XSD) からの DataSet リレーショナル構造の派生](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [XML からの DataSet リレーショナル構造の推論](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [XML からの DataSet の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
