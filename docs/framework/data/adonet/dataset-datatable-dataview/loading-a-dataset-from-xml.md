---
title: XML からの DataSet の読み込み
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: 0b74480209c8d06f38ea39e7a89741fc5a89512b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759765"
---
# <a name="loading-a-dataset-from-xml"></a>XML からの DataSet の読み込み
ADO.NET では、XML ストリームまたは XML ドキュメントから <xref:System.Data.DataSet> の内容を作成できます。 また、.NET Framework では、XML から読み込まれる情報と <xref:System.Data.DataSet> のスキーマまたはリレーショナル構造の作成方法を柔軟に変更できます。  
  
 入力する、 <xref:System.Data.DataSet> XML からデータを使用して、 **ReadXml**のメソッド、<xref:System.Data.DataSet>オブジェクト。 **ReadXml**メソッドは、ストリーム、ファイルから読み取りますまたは**XmlReader**、XML と省略可能なソースを引数として受け取り、 **XmlReadMode**引数。 (詳細については、 **XmlReader**を参照してください[NIB: XmlTextReader による XML データの読み取り](http://msdn.microsoft.com/library/762c069b-b50c-41b8-936e-39eacfb0d540))。**ReadXml**メソッドは、XML ストリームまたはドキュメントと読み込みの内容を読み取り、<xref:System.Data.DataSet>データを使用します。 リレーショナル スキーマも作成されます、<xref:System.Data.DataSet>に応じて、 **XmlReadMode**指定し、リレーショナル スキーマが既に存在するかどうか。  
  
 次の表に、オプション、 **XmlReadMode**引数。  
  
|オプション|説明|  
|------------|-----------------|  
|**Auto**|既定値です。 XML を調べ、次の順序で最適なオプションを選択します。<br /><br /> 場合、XML が DiffGram **DiffGram**を使用します。<br />If、<xref:System.Data.DataSet>スキーマを含むまたは XML にインライン スキーマが含まれている**ReadSchema**を使用します。<br />場合、<xref:System.Data.DataSet>スキーマが含まれていない XML にインライン スキーマが含まれていないと**InferSchema**を使用します。<br /><br /> 読み取られる XML の形式がわかっている場合最適なパフォーマンスをことをお勧め明示的に設定すること**XmlReadMode**ではなく、そのまま使用よりも、**自動**既定値です。|  
|**ReadSchema**|インライン スキーマを読み取り、データとスキーマを読み込みます。<br /><br /> <xref:System.Data.DataSet> に既にスキーマが含まれている場合には、読み取るインライン スキーマの新しいテーブルが <xref:System.Data.DataSet> の既存のスキーマに追加されます。 インライン スキーマのテーブルが既に <xref:System.Data.DataSet> に存在している場合には、例外がスローされます。 既存のテーブルを使用して、スキーマを変更することはできません**XmlReadMode.ReadSchema**です。<br /><br /> <xref:System.Data.DataSet> にスキーマが含まれておらず、インライン スキーマが存在しない場合には、データは読み取られません。<br /><br /> インライン スキーマを定義するには、XML スキーマ定義言語 (XSD) スキーマを使用します。 XML スキーマとインライン スキーマの作成方法の詳細については、「[派生した DataSet リレーショナル構造の XML スキーマ (XSD) から](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)です。|  
|**IgnoreSchema**|インライン スキーマを無視し、データを既存の <xref:System.Data.DataSet> スキーマへ読み込みます。 既存のスキーマに一致しないデータは破棄されます。 <xref:System.Data.DataSet> にスキーマがない場合には、データは読み込まれません。<br /><br /> 場合は、データは、DiffGram **IgnoreSchema**と同じ機能を持つ**DiffGram** *です。*|  
|**InferSchema**|インライン スキーマを無視し、XML データ構造ごとにスキーマを推論し、データを読み込みます。<br /><br /> <xref:System.Data.DataSet> に既にスキーマが含まれている場合、既存のテーブルに列を追加することによって現在のスキーマが拡張されます。 既存のテーブルが存在しない場合、余分なテーブルは追加されません。 推論されたテーブルが他の名前空間に既に存在している場合、または推論された列と既存の列が矛盾する場合には、例外がスローされます。<br /><br /> 方法の詳細について**ReadXmlSchema**スキーマを生成、XML ドキュメントから、次を参照してください。[推論 DataSet リレーショナル構造の XML から](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)です。|  
|**DiffGram**|DiffGram を読み取り、現在のスキーマへデータを追加します。 **DiffGram**既存の行に対し、一意の識別子の値が一致する新しい行をマージします。 このトピックの最後にある「XML のデータの結合」の説明を参照してください。 Diffgram についての詳細については、次を参照してください。 [Diffgram](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)です。|  
|**フラグメント**|ストリームの終わりに達するまで、複数 XML フラグメントの読み取りを続行します。 <xref:System.Data.DataSet> スキーマに一致するフラグメントが適切なテーブルに追加されます。 <xref:System.Data.DataSet> スキーマに一致しないフラグメントは破棄されます。|  
  
> [!NOTE]
>  渡す場合、 **XmlReader**に**ReadXml** 、XML ドキュメントにアクセスするための位置指定一部である**ReadXml**と、次の要素ノードへの読み取りはルートとして処理されます読み取りのみ、要素ノードが終了するまでの要素。 これは適用されませんを指定する場合**XmlReadMode.Fragment**です。  
  
## <a name="dtd-entities"></a>DTD エンティティ  
 読み込もうとした場合、XML ドキュメント型定義 (DTD) スキーマで定義されたエンティティが含まれている場合、例外がスローされます、<xref:System.Data.DataSet>ファイルを渡すことによって名、ストリーム、または非検証**XmlReader**に**ReadXml**です。 代わりに、作成する必要があります、 **XmlValidatingReader**で**EntityHandling** 'éý' **entityhandling.expandentities が使用**、渡すと、 **XmlValidatingReader**に**ReadXml**です。 **XmlValidatingReader**によって読み取られる前にエンティティの展開は、<xref:System.Data.DataSet>です。  
  
 XML ストリームから <xref:System.Data.DataSet> を読み込むコード サンプルを次に示します。 最初の例に渡されるファイル名、 **ReadXml**メソッドです。 2 番目の例では、XML が含まれている文字列が <xref:System.IO.StringReader> によって読み込まれます。  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema);  
```  
  
```vb  
Dim dataSet As DataSet = New DataSet  
Dim dataTable As DataTable = New DataTable("table1")  
dataTable.Columns.Add("col1", Type.GetType("System.String"))  
dataSet.Tables.Add(dataTable)  
  
Dim xmlData As String = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>"  
  
Dim xmlSR As System.IO.StringReader = New System.IO.StringReader(xmlData)  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
DataTable dataTable = new DataTable("table1");  
dataTable.Columns.Add("col1", typeof(string));  
dataSet.Tables.Add(dataTable);  
  
string xmlData = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>";  
  
System.IO.StringReader xmlSR = new System.IO.StringReader(xmlData);  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema);  
```  
  
> [!NOTE]
>  呼び出す場合**ReadXml**非常に大きなファイルを読み込むには、パフォーマンスの低下が発生する可能性があります。 最適なパフォーマンスを得るため**ReadXml**、サイズの大きなファイルを呼び出して、<xref:System.Data.DataTable.BeginLoadData%2A>メソッド内の各テーブルを<xref:System.Data.DataSet>、およびを呼び出す**ReadXml**です。 最後に、次の例に示すように、<xref:System.Data.DataTable.EndLoadData%2A> のテーブルごとに <xref:System.Data.DataSet> を呼び出します。  
  
```vb  
Dim dataTable As DataTable  
  
For Each dataTable In dataSet.Tables  
   dataTable.BeginLoadData()  
Next  
  
dataSet.ReadXml("file.xml")  
  
For Each dataTable in dataSet.Tables  
   dataTable.EndLoadData()  
Next  
```  
  
```csharp  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.BeginLoadData();  
  
dataSet.ReadXml("file.xml");   
  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.EndLoadData();  
```  
  
> [!NOTE]
>  場合の XSD スキーマ、<xref:System.Data.DataSet>が含まれています、 **targetNamespace**、データを読み取ることができませんが、およびを呼び出すときに、例外が発生する可能性があります**ReadXml**を読み込む、<xref:System.Data.DataSet>を含む xml該当する名前空間のない要素です。 ここでは修飾されていない要素を読み取り、次のように設定します。 **elementFormDefault** 、XSD スキーマで"qualified"に等しい。 例えば:  
  
```xml  
<xsd:schema id="customDataSet"   
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"   
  xmlns="http://www.tempuri.org/customDataSet.xsd"   
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a>XML のデータの結合  
 既に、<xref:System.Data.DataSet> にデータが含まれている場合には、<xref:System.Data.DataSet> の既存のデータに XML の新しいデータが追加されます。 **ReadXml**に XML からマージしません、<xref:System.Data.DataSet>が主キーに一致する行情報。 XML から新しい情報で既存の行情報を上書きするには使用**ReadXml**を新規作成する<xref:System.Data.DataSet>、し<xref:System.Data.DataSet.Merge%2A>新しい<xref:System.Data.DataSet>既存に<xref:System.Data.DataSet>です。 使用して DiffGram を読み込む**ReadXML**で、 **XmlReadMode**の**DiffGram**を同じ一意の識別子を持つ行をマージします。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>  
 [DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)  
 [XML スキーマ (XSD) からの DataSet リレーショナル構造の派生](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [XML からの DataSet リレーショナル構造の推論](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [XML の DataSet スキーマ情報の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
