---
title: XML の DataSet スキーマ情報の読み込み
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: 4b212a7233e6eec93cdce3e521b58e08745e35e0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760246"
---
# <a name="loading-dataset-schema-information-from-xml"></a><span data-ttu-id="7fccd-102">XML の DataSet スキーマ情報の読み込み</span><span class="sxs-lookup"><span data-stu-id="7fccd-102">Loading DataSet Schema Information from XML</span></span>
<span data-ttu-id="7fccd-103">スキーマ、 <xref:System.Data.DataSet> (そのテーブル、列、リレーション、および制約) はプログラムでは、によって作成された、**塗りつぶし**または**FillSchema**のメソッド、<xref:System.Data.Common.DataAdapter>から読み込まれたか、XML ドキュメントです。</span><span class="sxs-lookup"><span data-stu-id="7fccd-103">The schema of a <xref:System.Data.DataSet> (its tables, columns, relations, and constraints) can be defined programmatically, created by the **Fill** or **FillSchema** methods of a <xref:System.Data.Common.DataAdapter>, or loaded from an XML document.</span></span> <span data-ttu-id="7fccd-104">読み込む**データセット**スキーマ情報、XML ドキュメントから、いずれかを使用して、 **ReadXmlSchema**または**InferXmlSchema**のメソッド、**データセット**.</span><span class="sxs-lookup"><span data-stu-id="7fccd-104">To load **DataSet** schema information from an XML document, you can use either the **ReadXmlSchema** or the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="7fccd-105">**ReadXmlSchema**の読み込みまたは推論することができます**データセット**XML スキーマ定義言語 (XSD) スキーマ、またはインライン XML スキーマを持つ XML ドキュメントを含むドキュメントからスキーマ情報。</span><span class="sxs-lookup"><span data-stu-id="7fccd-105">**ReadXmlSchema** allows you to load or infer **DataSet** schema information from the document containing XML Schema definition language (XSD) schema, or an XML document with inline XML Schema.</span></span> <span data-ttu-id="7fccd-106">**InferXmlSchema**指定した特定の XML 名前空間を無視しているときに、XML ドキュメントからスキーマを推論することができます。</span><span class="sxs-lookup"><span data-stu-id="7fccd-106">**InferXmlSchema** allows you to infer the schema from the XML document while ignoring certain XML namespaces that you specify.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7fccd-107">テーブルの順序で、**データセット**を転送する Web サービスまたは XML シリアル化を使用する場合は保持されませんが、**データセット**インメモリ (入れ子になったリレーション) などの XSD コンス トラクターを使用して作成されました。</span><span class="sxs-lookup"><span data-stu-id="7fccd-107">Table ordering in a **DataSet** might not be preserved when you use Web services or XML serialization to transfer a **DataSet** that was created in-memory by using XSD constructs (such as nested relations).</span></span> <span data-ttu-id="7fccd-108">そのための受信者、**データセット**テーブルの例ではこの順序に依存しないようにします。</span><span class="sxs-lookup"><span data-stu-id="7fccd-108">Therefore, the recipient of the **DataSet** should not depend on table ordering in this case.</span></span> <span data-ttu-id="7fccd-109">ただし、テーブルの順序は常に保持される場合のスキーマ、**データセット**メモリ内で作成されているのではなく、XSD ファイルから読み取られた転送されています。</span><span class="sxs-lookup"><span data-stu-id="7fccd-109">However, table ordering is always preserved if the schema of the **DataSet** being transferred was read from XSD files, instead of being created in-memory.</span></span>  
  
## <a name="readxmlschema"></a><span data-ttu-id="7fccd-110">ReadXmlSchema</span><span class="sxs-lookup"><span data-stu-id="7fccd-110">ReadXmlSchema</span></span>  
 <span data-ttu-id="7fccd-111">スキーマを読み込む、**データセット**すべてのデータを読み込むことがなく、XML ドキュメントからを使用して、 **ReadXmlSchema**のメソッド、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="7fccd-111">To load the schema of a **DataSet** from an XML document without loading any data, you can use the **ReadXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="7fccd-112">**ReadXmlSchema**作成**データセット**スキーマの XML スキーマ定義言語 (XSD) スキーマを使用して定義します。</span><span class="sxs-lookup"><span data-stu-id="7fccd-112">**ReadXmlSchema** creates **DataSet** schema defined using XML Schema definition language (XSD) schema.</span></span>  
  
 <span data-ttu-id="7fccd-113">**ReadXmlSchema**メソッドを 1 つの引数でのファイル名、ストリーム、または**XmlReader**に読み込む XML ドキュメントを含むです。</span><span class="sxs-lookup"><span data-stu-id="7fccd-113">The **ReadXmlSchema** method takes a single argument of a file name, a stream, or an **XmlReader** containing the XML document to be loaded.</span></span> <span data-ttu-id="7fccd-114">この XML ドキュメントには、スキーマだけが含まれているか、またはデータのある XML 要素と共にスキーマがインラインで含まれています。</span><span class="sxs-lookup"><span data-stu-id="7fccd-114">The XML document can contain only schema, or can contain schema inline with XML elements containing data.</span></span> <span data-ttu-id="7fccd-115">XML スキーマとインライン スキーマの作成方法の詳細については、「[派生した DataSet リレーショナル構造の XML スキーマ (XSD) から](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)です。</span><span class="sxs-lookup"><span data-stu-id="7fccd-115">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
 <span data-ttu-id="7fccd-116">XML ドキュメントを渡す場合**ReadXmlSchema**インライン スキーマ情報を含まない**ReadXmlSchema** XML ドキュメント内の要素からスキーマを推論します。</span><span class="sxs-lookup"><span data-stu-id="7fccd-116">If the XML document passed to **ReadXmlSchema** contains no inline schema information, **ReadXmlSchema** will infer the schema from the elements in the XML document.</span></span> <span data-ttu-id="7fccd-117">場合、**データセット**スキーマを既に含む現在のスキーマが既に存在しない場合は、新しいテーブルを追加することによって拡張されます。</span><span class="sxs-lookup"><span data-stu-id="7fccd-117">If the **DataSet** already contains a schema, the current schema will be extended by adding new tables if they do not already exist.</span></span> <span data-ttu-id="7fccd-118">既存のテーブルには新しい列は追加されません。</span><span class="sxs-lookup"><span data-stu-id="7fccd-118">New columns will not be added to added to existing tables.</span></span> <span data-ttu-id="7fccd-119">既に追加されている列が存在する場合、**データセット**が列と互換性のない型が見つかりません、xml で、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="7fccd-119">If a column being added already exists in the **DataSet** but has an incompatible type with the column found in the XML, an exception is thrown.</span></span> <span data-ttu-id="7fccd-120">方法の詳細について**ReadXmlSchema**スキーマを生成、XML ドキュメントから、次を参照してください。[推論 DataSet リレーショナル構造の XML から](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)です。</span><span class="sxs-lookup"><span data-stu-id="7fccd-120">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).</span></span>  
  
 <span data-ttu-id="7fccd-121">**ReadXmlSchema**で読み込みまたは推論のスキーマのみ、**データセット**、 **ReadXml**のメソッド、**データセット**読み込まれるかまたは両方を推論スキーマと XML ドキュメントに含まれるデータ。</span><span class="sxs-lookup"><span data-stu-id="7fccd-121">Although **ReadXmlSchema** loads or infers only the schema of a **DataSet**, the **ReadXml** method of the **DataSet** loads or infers both the schema and the data contained in the XML document.</span></span> <span data-ttu-id="7fccd-122">詳細については、次を参照してください。 [XML からの DataSet の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)です。</span><span class="sxs-lookup"><span data-stu-id="7fccd-122">For more information, see [Loading a DataSet from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md).</span></span>  
  
 <span data-ttu-id="7fccd-123">次のコード例を読み込む方法を表示する、**データセット**を XML ドキュメントまたはストリームからのスキーマです。</span><span class="sxs-lookup"><span data-stu-id="7fccd-123">The following code examples show how to load a **DataSet** schema from an XML document or stream.</span></span> <span data-ttu-id="7fccd-124">最初の例に渡される XML スキーマ ファイル名、 **ReadXmlSchema**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="7fccd-124">The first example shows an XML Schema file name being passed to the **ReadXmlSchema** method.</span></span> <span data-ttu-id="7fccd-125">2 番目の例、 **System.IO.StreamReader**です。</span><span class="sxs-lookup"><span data-stu-id="7fccd-125">The second example shows a **System.IO.StreamReader**.</span></span>  
  
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
  
## <a name="inferxmlschema"></a><span data-ttu-id="7fccd-126">InferXmlSchema</span><span class="sxs-lookup"><span data-stu-id="7fccd-126">InferXmlSchema</span></span>  
 <span data-ttu-id="7fccd-127">指示することも、**データセット**を使用して XML ドキュメントからスキーマを推論、 **InferXmlSchema**のメソッド、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="7fccd-127">You can also instruct the **DataSet** to infer its schema from an XML document using the **InferXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="7fccd-128">**InferXmlSchema**両方と同じ機能**ReadXml**で、 **XmlReadMode**の**InferSchema** (データを読み込むし、スキーマを推論)、および**ReadXmlSchema**読み取られているドキュメントにインライン スキーマが含まれていない場合。</span><span class="sxs-lookup"><span data-stu-id="7fccd-128">**InferXmlSchema** functions the same as do both **ReadXml** with an **XmlReadMode** of **InferSchema** (loads data as well as infers schema), and **ReadXmlSchema** if the document being read contains no inline schema.</span></span> <span data-ttu-id="7fccd-129">ただし、 **InferXmlSchema**を無視するように、スキーマを推論する際に特定の XML 名前空間を指定できる追加機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="7fccd-129">However, **InferXmlSchema** provides the additional capability of allowing you to specify particular XML namespaces to be ignored when the schema is inferred.</span></span> <span data-ttu-id="7fccd-130">**InferXmlSchema**では 2 つの必要な引数: ファイル名、ストリームで指定された、XML ドキュメントの場所または**XmlReader**; と、操作によって無視される XML 名前空間の文字列配列。</span><span class="sxs-lookup"><span data-stu-id="7fccd-130">**InferXmlSchema** takes two required arguments: the location of the XML document, specified by a file name, a stream, or an **XmlReader**; and a string array of XML namespaces to be ignored by the operation.</span></span>  
  
 <span data-ttu-id="7fccd-131">たとえば、次のような XML があるとします。</span><span class="sxs-lookup"><span data-stu-id="7fccd-131">For example, consider the following XML:</span></span>  
  
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
  
 <span data-ttu-id="7fccd-132">上記の XML ドキュメント内の要素に指定された属性のため両方、 **ReadXmlSchema**メソッドおよび**ReadXml**メソッドを**XmlReadMode**の**InferSchema** 、ドキュメント内のすべての要素のテーブルの作成は:**カテゴリ**、 **CategoryID**、 **CategoryName**、**説明**、**製品**、 **ProductID**、 **ReorderLevel**、および**提供が中止されました。**.</span><span class="sxs-lookup"><span data-stu-id="7fccd-132">Because of the attributes specified for the elements in the preceding XML document, both the **ReadXmlSchema** method and the **ReadXml** method with an **XmlReadMode** of **InferSchema** would create tables for every element in the document: **Categories**, **CategoryID**, **CategoryName**, **Description**, **Products**, **ProductID**, **ReorderLevel**, and **Discontinued**.</span></span> <span data-ttu-id="7fccd-133">(詳細については、次を参照してください[推論 DataSet リレーショナル構造の XML から](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)。)適切な構造体のみを作成すること、ただし、**カテゴリ**と**製品**テーブルを作成し、 **CategoryID**、 **CategoryName**、および**説明**内の列、**カテゴリ**テーブル、および**ProductID**、 **ReorderLevel**、および**生産中止**内の列、**製品**テーブル。</span><span class="sxs-lookup"><span data-stu-id="7fccd-133">(For more information, see [Inferring DataSet Relational Structure from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).) However, a more appropriate structure would be to create only the **Categories** and **Products** tables, and then to create **CategoryID**, **CategoryName**, and **Description** columns in the **Categories** table, and **ProductID**, **ReorderLevel**, and **Discontinued** columns in the **Products** table.</span></span> <span data-ttu-id="7fccd-134">を確保するため、推論されるスキーマが XML 要素で指定された属性を無視することを使用して、 **InferXmlSchema**メソッドの XML 名前空間を指定して**officedata**無視するように、のように、次の例です。</span><span class="sxs-lookup"><span data-stu-id="7fccd-134">To ensure that the inferred schema ignores the attributes specified in the XML elements, use the **InferXmlSchema** method and specify the XML namespace for **officedata** to be ignored, as shown in the following example.</span></span>  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a><span data-ttu-id="7fccd-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="7fccd-135">See Also</span></span>  
 [<span data-ttu-id="7fccd-136">DataSet での XML の使用</span><span class="sxs-lookup"><span data-stu-id="7fccd-136">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="7fccd-137">XML スキーマ (XSD) からの DataSet リレーショナル構造の派生</span><span class="sxs-lookup"><span data-stu-id="7fccd-137">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [<span data-ttu-id="7fccd-138">XML からの DataSet リレーショナル構造の推論</span><span class="sxs-lookup"><span data-stu-id="7fccd-138">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="7fccd-139">XML からの DataSet の読み込み</span><span class="sxs-lookup"><span data-stu-id="7fccd-139">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="7fccd-140">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="7fccd-140">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="7fccd-141">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="7fccd-141">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
