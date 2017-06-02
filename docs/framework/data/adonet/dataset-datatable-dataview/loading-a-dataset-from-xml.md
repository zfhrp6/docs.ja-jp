---
title: "XML からの DataSet の読み込み | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# XML からの DataSet の読み込み
ADO.NET では、XML ストリームまたは XML ドキュメントから <xref:System.Data.DataSet> の内容を作成できます。  また、.NET Framework では、XML から読み込まれる情報と <xref:System.Data.DataSet> のスキーマまたはリレーショナル構造の作成方法を柔軟に変更できます。  
  
 <xref:System.Data.DataSet> に XML のデータを格納するには、<xref:System.Data.DataSet> オブジェクトの **ReadXml** メソッドを使用します。  **ReadXml** メソッドは、ファイル、ストリーム、または **XmlReader** からデータを読み取り、XML のソースを引数として受け取ります。また、**XmlReadMode** 引数を受け取ることもあります。  **XmlReader** に関する詳細については、「[NIB: Reading XML Data with XmlTextReader](http://msdn.microsoft.com/ja-jp/762c069b-b50c-41b8-936e-39eacfb0d540)」を参照してください。**ReadXml** メソッドは、XML ストリームまたは XML ドキュメントの内容を読み取り、<xref:System.Data.DataSet> にデータを読み込みます。  また、指定されている **XmlReadMode** と、リレーショナル スキーマが既に存在しているかどうかに応じて、<xref:System.Data.DataSet> のリレーショナル スキーマも作成します。  
  
 **XmlReadMode** 引数のオプションを次の表に示します。  
  
|オプション|説明|  
|-----------|--------|  
|**Auto**|既定値です。  XML を調べ、次の順序で最適なオプションを選択します。<br /><br /> -   XML が DiffGram の場合は、**DiffGram** が使用されます。<br />-   <xref:System.Data.DataSet> にスキーマが含まれている場合、または XML にインライン スキーマが含まれている場合は、**ReadSchema** が使用されます。<br />-   <xref:System.Data.DataSet> にスキーマが含まれておらず、XML にインライン スキーマが含まれていない場合は、**InferSchema** が使用されます。<br /><br /> 読み取られる XML の形式が判明している場合は、パフォーマンスを最大限に引き出すため、既定値 **Auto** を使用する代わりに、**XmlReadMode** を明示的に設定することをお勧めします。|  
|**ReadSchema**|インライン スキーマを読み取り、データとスキーマを読み込みます。<br /><br /> <xref:System.Data.DataSet> に既にスキーマが含まれている場合には、読み取るインライン スキーマの新しいテーブルが <xref:System.Data.DataSet> の既存のスキーマに追加されます。  インライン スキーマのテーブルが既に <xref:System.Data.DataSet> に存在している場合には、例外がスローされます。  **XmlReadMode.ReadSchema** を使用して既存のテーブルのスキーマを修正できません。<br /><br /> <xref:System.Data.DataSet> にスキーマが含まれておらず、インライン スキーマが存在しない場合には、データは読み取られません。<br /><br /> インライン スキーマを定義するには、XML スキーマ定義言語 \(XSD\) スキーマを使用します。  XML スキーマとしてのインライン スキーマを書き込む方法の詳細については、「[XML スキーマ \(XSD\) からの DataSet リレーショナル構造の派生](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)」を参照してください。|  
|**IgnoreSchema**|インライン スキーマを無視し、データを既存の <xref:System.Data.DataSet> スキーマへ読み込みます。  既存のスキーマに一致しないデータは破棄されます。  <xref:System.Data.DataSet> にスキーマがない場合には、データは読み込まれません。<br /><br /> データが DiffGram の場合、**IgnoreSchema** は **DiffGram** と同様に機能します。|  
|**InferSchema**|インライン スキーマを無視し、XML データ構造ごとにスキーマを推論し、データを読み込みます。<br /><br /> <xref:System.Data.DataSet> に既にスキーマが含まれている場合、既存のテーブルに列を追加することによって現在のスキーマが拡張されます。  既存のテーブルが存在しない場合、余分なテーブルは追加されません。  推論されたテーブルが他の名前空間に既に存在している場合、または推論された列と既存の列が矛盾する場合には、例外がスローされます。<br /><br /> **ReadXmlSchema** による XML ドキュメントからのスキーマの推論方法の詳細については、「[XML からの DataSet リレーショナル構造の推論](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)」を参照してください。|  
|**DiffGram**|DiffGram を読み取り、現在のスキーマへデータを追加します。  **DiffGram** は、既存の行に対し、固有の識別子の値が一致する新しい行を結合します。  このトピックの最後にある「XML のデータの結合」の説明を参照してください。  DiffGrams の詳細については、「[DiffGram](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)」を参照してください。|  
|**Fragment**|ストリームの終わりに達するまで、複数 XML フラグメントの読み取りを続行します。  <xref:System.Data.DataSet> スキーマに一致するフラグメントが適切なテーブルに追加されます。  <xref:System.Data.DataSet> スキーマに一致しないフラグメントは破棄されます。|  
  
> [!NOTE]
>  XML ドキュメントにアクセスするためのオブジェクトである **ReadXml** に **XmlReader** を渡すと、**ReadXml** は次の要素ノードを読み取り、このノードをルート要素として処理し、このノードの終わりに到達するまで読み取ります。  ただし **XmlReadMode.Fragment** を指定する場合にはこれは該当しません。  
  
## DTD エンティティ  
 ドキュメント型定義 \(DTD\) スキーマで定義されているエンティティが、XML に含まれている場合に、ファイル名、ストリーム、または非検証 **XmlReader** を **ReadXml** に渡して <xref:System.Data.DataSet> を読み込むと、例外がスローされます。  この方法の代わりに、**EntityHandling** を **EntityHandling.ExpandEntities** に設定して **XmlValidatingReader** を作成し、**XmlValidatingReader** を **ReadXml** へ渡してください。  **XmlValidatingReader** によってエンティティが展開された後で、<xref:System.Data.DataSet> がこのエンティティを読み取ります。  
  
 XML ストリームから <xref:System.Data.DataSet> を読み込むコード サンプルを次に示します。  1 番目の例では、ファイル名が **ReadXml** メソッドに渡されます。  2 番目の例では、XML が含まれている文字列が <xref:System.IO.StringReader> によって読み込まれます。  
  
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
>  非常に大きなファイルを読み込む際に **ReadXml** を呼び出すと、パフォーマンスが低下することがあります。  大きなファイルを読み込む場合に、**ReadXml** のパフォーマンスを最大にするには、<xref:System.Data.DataSet> のテーブルごとに <xref:System.Data.DataTable.BeginLoadData%2A> メソッドを呼び出し、その後で **ReadXml** を呼び出します。  最後に、次の例に示すように、<xref:System.Data.DataSet> のテーブルごとに <xref:System.Data.DataTable.EndLoadData%2A> を呼び出します。  
  
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
>  <xref:System.Data.DataSet> の XSD スキーマに **targetNamespace** がインクルードされている場合、**ReadXml** を呼び出して、名前空間が修飾されていない要素を含む XML を <xref:System.Data.DataSet> に読み込もうとすると、データが読み取られず、例外が発生することがあります。  この場合に、名前空間が指定されていない要素を読み込むには、XSD スキーマで **elementFormDefault** を "qualified" に設定します。  次に例を示します。  
  
```  
<xsd:schema id="customDataSet"   
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"   
  xmlns="http://www.tempuri.org/customDataSet.xsd"   
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## XML のデータの結合  
 既に、<xref:System.Data.DataSet> にデータが含まれている場合には、<xref:System.Data.DataSet> の既存のデータに XML の新しいデータが追加されます。  **ReadXml** では、XML の中で主キーが一致する行情報を <xref:System.Data.DataSet> に結合しません。  既存の行情報を XML の新しい情報で上書きするには、**ReadXml** を使用して新しい <xref:System.Data.DataSet> を作成してから、新しい <xref:System.Data.DataSet> を既存の <xref:System.Data.DataSet> へ結合 \(<xref:System.Data.DataSet.Merge%2A>\) します。  **XmlReadMode** が **DiffGram** の **ReadXML** を使用して DiffGram を読み込むと、同一の一意の識別子を持つ行が結合されます。  
  
## 参照  
 <xref:System.Data.DataSet.Merge%2A?displayProperty=fullName>   
 [DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)   
 [DiffGram](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)   
 [XML スキーマ \(XSD\) からの DataSet リレーショナル構造の派生](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)   
 [XML からの DataSet リレーショナル構造の推論](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)   
 [XML の DataSet スキーマ情報の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)   
 [DataSets、DataTables、および DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)