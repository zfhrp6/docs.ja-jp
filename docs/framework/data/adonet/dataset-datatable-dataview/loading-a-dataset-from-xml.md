---
title: "XML からの DataSet の読み込み"
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
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ebbe1addf47bc76903e362cfb353ade359a1c8ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="loading-a-dataset-from-xml"></a><span data-ttu-id="d449e-102">XML からの DataSet の読み込み</span><span class="sxs-lookup"><span data-stu-id="d449e-102">Loading a DataSet from XML</span></span>
<span data-ttu-id="d449e-103">ADO.NET では、XML ストリームまたは XML ドキュメントから <xref:System.Data.DataSet> の内容を作成できます。</span><span class="sxs-lookup"><span data-stu-id="d449e-103">The contents of an ADO.NET <xref:System.Data.DataSet> can be created from an XML stream or document.</span></span> <span data-ttu-id="d449e-104">また、.NET Framework では、XML から読み込まれる情報と <xref:System.Data.DataSet> のスキーマまたはリレーショナル構造の作成方法を柔軟に変更できます。</span><span class="sxs-lookup"><span data-stu-id="d449e-104">In addition, with the .NET Framework you have great flexibility over what information is loaded from XML, and how the schema or relational structure of the <xref:System.Data.DataSet> is created.</span></span>  
  
 <span data-ttu-id="d449e-105">入力する、 <xref:System.Data.DataSet> XML からデータを使用して、 **ReadXml**のメソッド、<xref:System.Data.DataSet>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d449e-105">To fill a <xref:System.Data.DataSet> with data from XML, use the **ReadXml** method of the <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="d449e-106">**ReadXml**メソッドは、ストリーム、ファイルから読み取りますまたは**XmlReader**、XML と省略可能なソースを引数として受け取り、 **XmlReadMode**引数。</span><span class="sxs-lookup"><span data-stu-id="d449e-106">The **ReadXml** method reads from a file, a stream, or an **XmlReader**, and takes as arguments the source of the XML plus an optional **XmlReadMode** argument.</span></span> <span data-ttu-id="d449e-107">(詳細については、 **XmlReader**を参照してください[NIB: XmlTextReader による XML データの読み取り](http://msdn.microsoft.com/en-us/762c069b-b50c-41b8-936e-39eacfb0d540))。**ReadXml**メソッドは、XML ストリームまたはドキュメントと読み込みの内容を読み取り、<xref:System.Data.DataSet>データを使用します。</span><span class="sxs-lookup"><span data-stu-id="d449e-107">(For more information about the **XmlReader**, see [NIB: Reading XML Data with XmlTextReader](http://msdn.microsoft.com/en-us/762c069b-b50c-41b8-936e-39eacfb0d540).) The **ReadXml** method reads the contents of the XML stream or document and loads the <xref:System.Data.DataSet> with data.</span></span> <span data-ttu-id="d449e-108">リレーショナル スキーマも作成されます、<xref:System.Data.DataSet>に応じて、 **XmlReadMode**指定し、リレーショナル スキーマが既に存在するかどうか。</span><span class="sxs-lookup"><span data-stu-id="d449e-108">It will also create the relational schema of the <xref:System.Data.DataSet> depending on the **XmlReadMode** specified and whether or not a relational schema already exists.</span></span>  
  
 <span data-ttu-id="d449e-109">次の表に、オプション、 **XmlReadMode**引数。</span><span class="sxs-lookup"><span data-stu-id="d449e-109">The following table describes the options for the **XmlReadMode** argument.</span></span>  
  
|<span data-ttu-id="d449e-110">オプション</span><span class="sxs-lookup"><span data-stu-id="d449e-110">Option</span></span>|<span data-ttu-id="d449e-111">説明</span><span class="sxs-lookup"><span data-stu-id="d449e-111">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="d449e-112">**Auto**</span><span class="sxs-lookup"><span data-stu-id="d449e-112">**Auto**</span></span>|<span data-ttu-id="d449e-113">既定値です。</span><span class="sxs-lookup"><span data-stu-id="d449e-113">This is the default.</span></span> <span data-ttu-id="d449e-114">XML を調べ、次の順序で最適なオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="d449e-114">Examines the XML and chooses the most appropriate option in the following order:</span></span><br /><br /> <span data-ttu-id="d449e-115">場合、XML が DiffGram **DiffGram**を使用します。</span><span class="sxs-lookup"><span data-stu-id="d449e-115">-   If the XML is a DiffGram, **DiffGram** is used.</span></span><br /><span data-ttu-id="d449e-116">If、<xref:System.Data.DataSet>スキーマを含むまたは XML にインライン スキーマが含まれている**ReadSchema**を使用します。</span><span class="sxs-lookup"><span data-stu-id="d449e-116">-   If the <xref:System.Data.DataSet> contains a schema or the XML contains an inline schema, **ReadSchema** is used.</span></span><br /><span data-ttu-id="d449e-117">場合、<xref:System.Data.DataSet>スキーマが含まれていない XML にインライン スキーマが含まれていないと**InferSchema**を使用します。</span><span class="sxs-lookup"><span data-stu-id="d449e-117">-   If the <xref:System.Data.DataSet> does not contain a schema and the XML does not contain an inline schema, **InferSchema** is used.</span></span><br /><br /> <span data-ttu-id="d449e-118">読み取られる XML の形式がわかっている場合最適なパフォーマンスをことをお勧め明示的に設定すること**XmlReadMode**ではなく、そのまま使用よりも、**自動**既定値です。</span><span class="sxs-lookup"><span data-stu-id="d449e-118">If you know the format of the XML being read, for best performance it is recommended that you set an explicit **XmlReadMode**, rather than accept the **Auto** default.</span></span>|  
|<span data-ttu-id="d449e-119">**ReadSchema**</span><span class="sxs-lookup"><span data-stu-id="d449e-119">**ReadSchema**</span></span>|<span data-ttu-id="d449e-120">インライン スキーマを読み取り、データとスキーマを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="d449e-120">Reads any inline schema and loads the data and schema.</span></span><br /><br /> <span data-ttu-id="d449e-121"><xref:System.Data.DataSet> に既にスキーマが含まれている場合には、読み取るインライン スキーマの新しいテーブルが <xref:System.Data.DataSet> の既存のスキーマに追加されます。</span><span class="sxs-lookup"><span data-stu-id="d449e-121">If the <xref:System.Data.DataSet> already contains a schema, new tables are added from the inline schema to the existing schema in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="d449e-122">インライン スキーマのテーブルが既に <xref:System.Data.DataSet> に存在している場合には、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="d449e-122">If any tables in the inline schema already exist in the <xref:System.Data.DataSet>, an exception is thrown.</span></span> <span data-ttu-id="d449e-123">既存のテーブルを使用して、スキーマを変更することはできません**XmlReadMode.ReadSchema**です。</span><span class="sxs-lookup"><span data-stu-id="d449e-123">You will not be able to modify the schema of an existing table using **XmlReadMode.ReadSchema**.</span></span><br /><br /> <span data-ttu-id="d449e-124"><xref:System.Data.DataSet> にスキーマが含まれておらず、インライン スキーマが存在しない場合には、データは読み取られません。</span><span class="sxs-lookup"><span data-stu-id="d449e-124">If the <xref:System.Data.DataSet> does not contain a schema, and there is no inline schema, no data is read.</span></span><br /><br /> <span data-ttu-id="d449e-125">インライン スキーマを定義するには、XML スキーマ定義言語 (XSD) スキーマを使用します。</span><span class="sxs-lookup"><span data-stu-id="d449e-125">Inline schema can be defined using XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="d449e-126">XML スキーマとインライン スキーマの作成方法の詳細については、「[派生した DataSet リレーショナル構造の XML スキーマ (XSD) から](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)です。</span><span class="sxs-lookup"><span data-stu-id="d449e-126">For details about writing inline schema as XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>|  
|<span data-ttu-id="d449e-127">**IgnoreSchema**</span><span class="sxs-lookup"><span data-stu-id="d449e-127">**IgnoreSchema**</span></span>|<span data-ttu-id="d449e-128">インライン スキーマを無視し、データを既存の <xref:System.Data.DataSet> スキーマへ読み込みます。</span><span class="sxs-lookup"><span data-stu-id="d449e-128">Ignores any inline schema and loads the data into the existing <xref:System.Data.DataSet> schema.</span></span> <span data-ttu-id="d449e-129">既存のスキーマに一致しないデータは破棄されます。</span><span class="sxs-lookup"><span data-stu-id="d449e-129">Any data that does not match the existing schema is discarded.</span></span> <span data-ttu-id="d449e-130"><xref:System.Data.DataSet> にスキーマがない場合には、データは読み込まれません。</span><span class="sxs-lookup"><span data-stu-id="d449e-130">If no schema exists in the <xref:System.Data.DataSet>, no data is loaded.</span></span><br /><br /> <span data-ttu-id="d449e-131">場合は、データは、DiffGram **IgnoreSchema**と同じ機能を持つ**DiffGram** *です。*</span><span class="sxs-lookup"><span data-stu-id="d449e-131">If the data is a DiffGram, **IgnoreSchema** has the same functionality as **DiffGram** *.*</span></span>|  
|<span data-ttu-id="d449e-132">**InferSchema**</span><span class="sxs-lookup"><span data-stu-id="d449e-132">**InferSchema**</span></span>|<span data-ttu-id="d449e-133">インライン スキーマを無視し、XML データ構造ごとにスキーマを推論し、データを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="d449e-133">Ignores any inline schema and infers the schema per the structure of the XML data, then loads the data.</span></span><br /><br /> <span data-ttu-id="d449e-134"><xref:System.Data.DataSet> に既にスキーマが含まれている場合、既存のテーブルに列を追加することによって現在のスキーマが拡張されます。</span><span class="sxs-lookup"><span data-stu-id="d449e-134">If the <xref:System.Data.DataSet> already contains a schema, the current schema is extended by adding columns to existing tables.</span></span> <span data-ttu-id="d449e-135">既存のテーブルが存在しない場合、余分なテーブルは追加されません。</span><span class="sxs-lookup"><span data-stu-id="d449e-135">Extra tables will not be added if there are not existing tables.</span></span> <span data-ttu-id="d449e-136">推論されたテーブルが他の名前空間に既に存在している場合、または推論された列と既存の列が矛盾する場合には、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="d449e-136">An exception is thrown if an inferred table already exists with a different namespace, or if any inferred columns conflict with existing columns.</span></span><br /><br /> <span data-ttu-id="d449e-137">方法の詳細について**ReadXmlSchema**スキーマを生成、XML ドキュメントから、次を参照してください。[推論 DataSet リレーショナル構造の XML から](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)です。</span><span class="sxs-lookup"><span data-stu-id="d449e-137">For details about how **ReadXmlSchema** infers a schema from an XML document, see [Inferring DataSet Relational Structure from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md).</span></span>|  
|<span data-ttu-id="d449e-138">**DiffGram**</span><span class="sxs-lookup"><span data-stu-id="d449e-138">**DiffGram**</span></span>|<span data-ttu-id="d449e-139">DiffGram を読み取り、現在のスキーマへデータを追加します。</span><span class="sxs-lookup"><span data-stu-id="d449e-139">Reads a DiffGram and adds the data to the current schema.</span></span> <span data-ttu-id="d449e-140">**DiffGram**既存の行に対し、一意の識別子の値が一致する新しい行をマージします。</span><span class="sxs-lookup"><span data-stu-id="d449e-140">**DiffGram** merges new rows with existing rows where the unique identifier values match.</span></span> <span data-ttu-id="d449e-141">このトピックの最後にある「XML のデータの結合」の説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d449e-141">See "Merging Data from XML" at the end of this topic.</span></span> <span data-ttu-id="d449e-142">Diffgram についての詳細については、次を参照してください。 [Diffgram](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)です。</span><span class="sxs-lookup"><span data-stu-id="d449e-142">For more information about DiffGrams, see [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).</span></span>|  
|<span data-ttu-id="d449e-143">**フラグメント**</span><span class="sxs-lookup"><span data-stu-id="d449e-143">**Fragment**</span></span>|<span data-ttu-id="d449e-144">ストリームの終わりに達するまで、複数 XML フラグメントの読み取りを続行します。</span><span class="sxs-lookup"><span data-stu-id="d449e-144">Continues reading multiple XML fragments until the end of the stream is reached.</span></span> <span data-ttu-id="d449e-145"><xref:System.Data.DataSet> スキーマに一致するフラグメントが適切なテーブルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="d449e-145">Fragments that match the <xref:System.Data.DataSet> schema are appended to the appropriate tables.</span></span> <span data-ttu-id="d449e-146"><xref:System.Data.DataSet> スキーマに一致しないフラグメントは破棄されます。</span><span class="sxs-lookup"><span data-stu-id="d449e-146">Fragments that do not match the <xref:System.Data.DataSet> schema are discarded.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="d449e-147">渡す場合、 **XmlReader**に**ReadXml** 、XML ドキュメントにアクセスするための位置指定一部である**ReadXml**と、次の要素ノードへの読み取りはルートとして処理されます読み取りのみ、要素ノードが終了するまでの要素。</span><span class="sxs-lookup"><span data-stu-id="d449e-147">If you pass an **XmlReader** to **ReadXml** that is positioned part of the way into an XML document, **ReadXml** will read to the next element node and will treat that as the root element, reading until the end of the element node only.</span></span> <span data-ttu-id="d449e-148">これは適用されませんを指定する場合**XmlReadMode.Fragment**です。</span><span class="sxs-lookup"><span data-stu-id="d449e-148">This does not apply if you specify **XmlReadMode.Fragment**.</span></span>  
  
## <a name="dtd-entities"></a><span data-ttu-id="d449e-149">DTD エンティティ</span><span class="sxs-lookup"><span data-stu-id="d449e-149">DTD Entities</span></span>  
 <span data-ttu-id="d449e-150">読み込もうとした場合、XML ドキュメント型定義 (DTD) スキーマで定義されたエンティティが含まれている場合、例外がスローされます、<xref:System.Data.DataSet>ファイルを渡すことによって名、ストリーム、または非検証**XmlReader**に**ReadXml**です。</span><span class="sxs-lookup"><span data-stu-id="d449e-150">If your XML contains entities defined in a document type definition (DTD) schema, an exception will be thrown if you attempt to load a <xref:System.Data.DataSet> by passing a file name, stream, or non-validating **XmlReader** to **ReadXml**.</span></span> <span data-ttu-id="d449e-151">代わりに、作成する必要があります、 **XmlValidatingReader**で**EntityHandling** 'éý' **entityhandling.expandentities が使用**、渡すと、 **XmlValidatingReader**に**ReadXml**です。</span><span class="sxs-lookup"><span data-stu-id="d449e-151">Instead, you must create an **XmlValidatingReader**, with **EntityHandling** set to **EntityHandling.ExpandEntities**, and pass your **XmlValidatingReader** to **ReadXml**.</span></span> <span data-ttu-id="d449e-152">**XmlValidatingReader**によって読み取られる前にエンティティの展開は、<xref:System.Data.DataSet>です。</span><span class="sxs-lookup"><span data-stu-id="d449e-152">The **XmlValidatingReader** will expand the entities prior to being read by the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="d449e-153">XML ストリームから <xref:System.Data.DataSet> を読み込むコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="d449e-153">The following code examples show how to load a <xref:System.Data.DataSet> from an XML stream.</span></span> <span data-ttu-id="d449e-154">最初の例に渡されるファイル名、 **ReadXml**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="d449e-154">The first example shows a file name being passed to the **ReadXml** method.</span></span> <span data-ttu-id="d449e-155">2 番目の例では、XML が含まれている文字列が <xref:System.IO.StringReader> によって読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="d449e-155">The second example shows a string that contains XML being loaded using a <xref:System.IO.StringReader>.</span></span>  
  
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
>  <span data-ttu-id="d449e-156">呼び出す場合**ReadXml**非常に大きなファイルを読み込むには、パフォーマンスの低下が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d449e-156">If you call **ReadXml** to load a very large file, you may encounter slow performance.</span></span> <span data-ttu-id="d449e-157">最適なパフォーマンスを得るため**ReadXml**、サイズの大きなファイルを呼び出して、<xref:System.Data.DataTable.BeginLoadData%2A>メソッド内の各テーブルを<xref:System.Data.DataSet>、およびを呼び出す**ReadXml**です。</span><span class="sxs-lookup"><span data-stu-id="d449e-157">To ensure best performance for **ReadXml**, on a large file, call the <xref:System.Data.DataTable.BeginLoadData%2A> method for each table in the <xref:System.Data.DataSet>, and then call **ReadXml**.</span></span> <span data-ttu-id="d449e-158">最後に、次の例に示すように、<xref:System.Data.DataTable.EndLoadData%2A> のテーブルごとに <xref:System.Data.DataSet> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d449e-158">Finally, call <xref:System.Data.DataTable.EndLoadData%2A> for each table in the <xref:System.Data.DataSet>, as shown in the following example.</span></span>  
  
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
>  <span data-ttu-id="d449e-159">場合の XSD スキーマ、<xref:System.Data.DataSet>が含まれています、 **targetNamespace**、データを読み取ることができませんが、およびを呼び出すときに、例外が発生する可能性があります**ReadXml**を読み込む、<xref:System.Data.DataSet>を含む xml該当する名前空間のない要素です。</span><span class="sxs-lookup"><span data-stu-id="d449e-159">If the XSD schema for your <xref:System.Data.DataSet> includes a **targetNamespace**, data may not be read, and you may encounter exceptions, when calling **ReadXml** to load the <xref:System.Data.DataSet> with XML that contains elements with no qualifying namespace.</span></span> <span data-ttu-id="d449e-160">ここでは修飾されていない要素を読み取り、次のように設定します。 **elementFormDefault** 、XSD スキーマで"qualified"に等しい。</span><span class="sxs-lookup"><span data-stu-id="d449e-160">To read unqualified elements in this case, set **elementFormDefault** equal to "qualified" in your XSD schema.</span></span> <span data-ttu-id="d449e-161">例:</span><span class="sxs-lookup"><span data-stu-id="d449e-161">For example:</span></span>  
  
```xml  
<xsd:schema id="customDataSet"   
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"   
  xmlns="http://www.tempuri.org/customDataSet.xsd"   
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a><span data-ttu-id="d449e-162">XML のデータの結合</span><span class="sxs-lookup"><span data-stu-id="d449e-162">Merging Data from XML</span></span>  
 <span data-ttu-id="d449e-163">既に、<xref:System.Data.DataSet> にデータが含まれている場合には、<xref:System.Data.DataSet> の既存のデータに XML の新しいデータが追加されます。</span><span class="sxs-lookup"><span data-stu-id="d449e-163">If the <xref:System.Data.DataSet> already contains data, the new data from the XML is added to the data already present in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="d449e-164">**ReadXml**に XML からマージしません、<xref:System.Data.DataSet>が主キーに一致する行情報。</span><span class="sxs-lookup"><span data-stu-id="d449e-164">**ReadXml** does not merge from the XML into the <xref:System.Data.DataSet> any row information with matching primary keys.</span></span> <span data-ttu-id="d449e-165">XML から新しい情報で既存の行情報を上書きするには使用**ReadXml**を新規作成する<xref:System.Data.DataSet>、し<xref:System.Data.DataSet.Merge%2A>新しい<xref:System.Data.DataSet>既存に<xref:System.Data.DataSet>です。</span><span class="sxs-lookup"><span data-stu-id="d449e-165">To overwrite existing row information with new information from XML, use **ReadXml** to create a new <xref:System.Data.DataSet>, and then <xref:System.Data.DataSet.Merge%2A> the new <xref:System.Data.DataSet> into the existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="d449e-166">使用して DiffGram を読み込む**ReadXML**で、 **XmlReadMode**の**DiffGram**を同じ一意の識別子を持つ行をマージします。</span><span class="sxs-lookup"><span data-stu-id="d449e-166">Note that loading a DiffGram using **ReadXML** with an **XmlReadMode** of **DiffGram** will merge rows that have the same unique identifier.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d449e-167">参照</span><span class="sxs-lookup"><span data-stu-id="d449e-167">See Also</span></span>  
 <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="d449e-168">DataSet での XML の使用</span><span class="sxs-lookup"><span data-stu-id="d449e-168">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="d449e-169">DiffGrams</span><span class="sxs-lookup"><span data-stu-id="d449e-169">DiffGrams</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)  
 [<span data-ttu-id="d449e-170">XML スキーマ (XSD) からの DataSet リレーショナル構造の派生</span><span class="sxs-lookup"><span data-stu-id="d449e-170">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [<span data-ttu-id="d449e-171">XML からの DataSet リレーショナル構造の推論</span><span class="sxs-lookup"><span data-stu-id="d449e-171">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="d449e-172">XML の DataSet スキーマ情報の読み込み</span><span class="sxs-lookup"><span data-stu-id="d449e-172">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="d449e-173">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="d449e-173">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="d449e-174">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="d449e-174">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
