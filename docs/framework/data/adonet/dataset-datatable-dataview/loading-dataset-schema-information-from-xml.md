---
title: "XML の DataSet スキーマ情報の読み込み | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# XML の DataSet スキーマ情報の読み込み
<xref:System.Data.DataSet> のスキーマ \(テーブル、列、リレーション、および制約\) は、プログラムを使用して定義され、<xref:System.Data.Common.DataAdapter> の **Fill** メソッドまたは **FillSchema** メソッドによって作成されるか、あるいは XML ドキュメントから読み込まれます。  XML ドキュメントから **DataSet** スキーマ情報を読み込むには、**DataSet** の **ReadXmlSchema** メソッドまたは **InferXmlSchema** メソッドを使用します。  **ReadXmlSchema** を使用すると、XML スキーマ定義言語 \(XSD\) スキーマが含まれているドキュメントまたはインライン XML スキーマが含まれている XML ドキュメントから、**DataSet** スキーマ情報を読み込むかまたは推論できます。  **InferXmlSchema** を使用すると、XML ドキュメントからスキーマを推論できます。このとき、指定した特定の XML 名前空間は無視されます。  
  
> [!NOTE]
>  XSD の構造 \(入れ子になったリレーションなど\) を使用してメモリ内で作成された **DataSet** を、Web サービスまたは XML シリアル化を使って転送した場合、**DataSet** 内のテーブルの順序が維持されない場合があります。  この場合、**DataSet** の受け取り側はテーブルの順序に依存していないことが必要です。  ただし、メモリ内で作成するのではなく、転送する **DataSet** のスキーマを XSD ファイルから読み取った場合は、テーブルの順序が常に維持されます。  
  
## ReadXmlSchema  
 XML ドキュメントから **DataSet** のスキーマだけを読み込み、データを読み込まないようにするには、**DataSet** の **ReadXmlSchema** メソッドを使用します。  **ReadXmlSchema** は、XML スキーマ定義言語 \(XSD\) スキーマを使用して定義されている **DataSet** を作成します。  
  
 **ReadXmlSchema** メソッドは、ファイル名、ストリーム、または読み込む XML ドキュメントが格納されている **XmlReader** のいずれか 1 つを引数として受け取ります。  この XML ドキュメントには、スキーマだけが含まれているか、またはデータのある XML 要素と共にスキーマがインラインで含まれています。  XML スキーマとしてのインライン スキーマを書き込む方法の詳細については、「[XML スキーマ \(XSD\) からの DataSet リレーショナル構造の派生](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)」を参照してください。  
  
 **ReadXmlSchema** に渡された XML ドキュメントに、インライン スキーマ情報が含まれていない場合、**ReadXmlSchema** は XML ドキュメントの要素からスキーマを推論します。  **DataSet** に既にスキーマが含まれている場合、テーブルが存在しなければ新しいテーブルを追加することによって現在のスキーマが拡張されます。  既存のテーブルには新しい列は追加されません。  **DataSet** に既に追加される列が存在していますが、XML で検出された列の型と矛盾する場合には、例外がスローされます。  **ReadXmlSchema** による XML ドキュメントからのスキーマの推論方法の詳細については、「[XML からの DataSet リレーショナル構造の推論](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)」を参照してください。  
  
 **ReadXmlSchema** は **DataSet** スキーマの読み込みまたは推論のいずれかを実行しますが、**DataSet** の **ReadXml** メソッドは、スキーマと XML ドキュメントのデータの両方の読み込みまたは推論を実行します。  詳細については、「[XML からの DataSet の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)」を参照してください。  
  
 XML ドキュメントまたは XML ストリームから **DataSet** スキーマを読み込む方法を次のコード サンプルに示します。  1 番目の例では、XML スキーマ ファイル名が **ReadXmlSchema** メソッドへ渡されます。  2 番目の例では、**System.IO.StreamReader** が示されています。  
  
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
  
## InferXmlSchema  
 **DataSet** に対し、**DataSet** の **InferXmlSchema** メソッドを使用して XML ドキュメントのスキーマを推論するように指示できます。  **InferXmlSchema** は、**XmlReadMode** を **InferSchema** に設定した **ReadXml** \(データの読み込みとスキーマの推論\) と、読み取られるドキュメントにインライン スキーマが含まれていない場合の **ReadXmlSchema** の両方と同様の機能を備えています。  ただし **InferXmlSchema** には、スキーマを推論するときに無視する特定の XML 名前空間を指定できる追加機能を用意しています。  **InferXmlSchema** に必要な 2 つの引数は、XML ドキュメントの位置と、この操作によって無視される XML 名前空間の文字列配列です。XML ドキュメントの位置は、ファイル名、ストリーム、または **XmlReader** によって指定されます。  
  
 たとえば、次のような XML があるとします。  
  
```  
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
  
 前述の XML ドキュメントの要素に対して指定されている属性により、**ReadXmlSchema** メソッドと、**XmlReadMode** が **InferSchema** に設定されている **ReadXml** メソッドは、いずれもドキュメントのすべての要素 \(**Categories**、**CategoryID**、**CategoryName**、**Description**、**Products**、**ProductID**、**ReorderLevel**、および **Discontinued**\) に対してテーブルを作成します。  \(詳細については、「[XML からの DataSet リレーショナル構造の推論](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)」を参照してください\)。ただし、この作成方法よりも適切な方法としては、最初に **Categories** テーブルと **Products** テーブルだけを作成し、次に **Categories** テーブルの **CategoryID**、**CategoryName**、および **Description** 列を作成し、**Products** テーブルの **ProductID**、**ReorderLevel** および **Discontinued** 列を作成する方法があります。  推論されたスキーマが、XML 要素に指定されている属性を無視するようにするには、**InferXmlSchema** メソッドを使用して **officedata** の XML 名前空間を無視するように指定します。この例を次に示します。  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## 参照  
 [DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)   
 [XML スキーマ \(XSD\) からの DataSet リレーショナル構造の派生](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)   
 [XML からの DataSet リレーショナル構造の推論](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)   
 [XML からの DataSet の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)   
 [DataSets、DataTables、および DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)