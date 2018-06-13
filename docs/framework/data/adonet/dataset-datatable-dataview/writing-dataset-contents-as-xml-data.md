---
title: DataSet 内容の XML データとしての書き込み
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd15f8a5-3b4c-46d0-a561-4559ab2a4705
ms.openlocfilehash: 44afa79d715ef62bcbd1c242a533876d911345c8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761910"
---
# <a name="writing-dataset-contents-as-xml-data"></a><span data-ttu-id="5ee56-102">DataSet 内容の XML データとしての書き込み</span><span class="sxs-lookup"><span data-stu-id="5ee56-102">Writing DataSet Contents as XML Data</span></span>
<span data-ttu-id="5ee56-103">ADO.NET では、<xref:System.Data.DataSet> の XML 表現を記述することができます。このとき、 にスキーマが含まれていても、含まれていなくてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="5ee56-103">In ADO.NET you can write an XML representation of a <xref:System.Data.DataSet>, with or without its schema.</span></span> <span data-ttu-id="5ee56-104">XML にインラインで含まれているスキーマ情報は、XML スキーマ定義言語 (XSD) を使用して記述されています。</span><span class="sxs-lookup"><span data-stu-id="5ee56-104">If schema information is included inline with the XML, it is written using the XML Schema definition language (XSD).</span></span> <span data-ttu-id="5ee56-105">スキーマには、リレーション定義および制約定義と、<xref:System.Data.DataSet> のテーブル定義が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5ee56-105">The schema contains the table definitions of the <xref:System.Data.DataSet> as well as the relation and constraint definitions.</span></span>  
  
 <span data-ttu-id="5ee56-106"><xref:System.Data.DataSet> が XML データとして書き込まれると、<xref:System.Data.DataSet> の行は現在のバージョンで書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="5ee56-106">When a <xref:System.Data.DataSet> is written as XML data, the rows in the <xref:System.Data.DataSet> are written in their current versions.</span></span> <span data-ttu-id="5ee56-107">ただし、行の現在の値と元の値の両方を含めるには、<xref:System.Data.DataSet> を DiffGram として書き込みます。</span><span class="sxs-lookup"><span data-stu-id="5ee56-107">However, the <xref:System.Data.DataSet> can also be written as a DiffGram so that both the current and the original values of the rows will be included.</span></span>  
  
 <span data-ttu-id="5ee56-108">XML 表現、<xref:System.Data.DataSet>ファイル、ストリームに書き込むことができます、 **XmlWriter**、または string です。</span><span class="sxs-lookup"><span data-stu-id="5ee56-108">The XML representation of the <xref:System.Data.DataSet> can be written to a file, a stream, an **XmlWriter**, or a string.</span></span> <span data-ttu-id="5ee56-109">複数の書き込み先があることから、<xref:System.Data.DataSet> の XML 表現の転送方法を柔軟に変更できます。</span><span class="sxs-lookup"><span data-stu-id="5ee56-109">These choices provide great flexibility for how you transport the XML representation of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="5ee56-110">XML 表現を取得する、<xref:System.Data.DataSet>を文字列として使用して、 **GetXml**メソッドの次の例に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="5ee56-110">To obtain the XML representation of the <xref:System.Data.DataSet> as a string, use the **GetXml** method as shown in the following example.</span></span>  
  
```vb  
Dim xmlDS As String = custDS.GetXml()  
```  
  
```csharp  
string xmlDS = custDS.GetXml();  
```  
  
 <span data-ttu-id="5ee56-111">**GetXml**の XML 表現を返します、<xref:System.Data.DataSet>スキーマ情報がない場合。</span><span class="sxs-lookup"><span data-stu-id="5ee56-111">**GetXml** returns the XML representation of the <xref:System.Data.DataSet> without schema information.</span></span> <span data-ttu-id="5ee56-112">スキーマ情報を書き込む、 <xref:System.Data.DataSet> (XML スキーマ) として使用して、文字列に**GetXmlSchema**です。</span><span class="sxs-lookup"><span data-stu-id="5ee56-112">To write the schema information from the <xref:System.Data.DataSet> (as XML Schema) to a string, use **GetXmlSchema**.</span></span>  
  
 <span data-ttu-id="5ee56-113">書き込む、<xref:System.Data.DataSet>ファイル、ストリーム、または**XmlWriter**を使用して、 **WriteXml**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="5ee56-113">To write a <xref:System.Data.DataSet> to a file, stream, or **XmlWriter**, use the **WriteXml** method.</span></span> <span data-ttu-id="5ee56-114">最初のパラメーターに渡す**WriteXml** XML 出力の先であります。</span><span class="sxs-lookup"><span data-stu-id="5ee56-114">The first parameter you pass to **WriteXml** is the destination of the XML output.</span></span> <span data-ttu-id="5ee56-115">たとえば、ファイル名を含む文字列を渡す、 **System.IO.TextWriter**オブジェクト、およびなどです。</span><span class="sxs-lookup"><span data-stu-id="5ee56-115">For example, pass a string containing a file name, a **System.IO.TextWriter** object, and so on.</span></span> <span data-ttu-id="5ee56-116">省略可能な 2 番目のパラメーターを渡すことができます、 **XmlWriteMode**に XML 出力を書き込む方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="5ee56-116">You can pass an optional second parameter of an **XmlWriteMode** to specify how the XML output is to be written.</span></span>  
  
 <span data-ttu-id="5ee56-117">次の表は、オプションの**XmlWriteMode**です。</span><span class="sxs-lookup"><span data-stu-id="5ee56-117">The following table shows the options for **XmlWriteMode**.</span></span>  
  
|<span data-ttu-id="5ee56-118">XmlWriteMode のオプション</span><span class="sxs-lookup"><span data-stu-id="5ee56-118">XmlWriteMode option</span></span>|<span data-ttu-id="5ee56-119">説明</span><span class="sxs-lookup"><span data-stu-id="5ee56-119">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="5ee56-120">**IgnoreSchema**</span><span class="sxs-lookup"><span data-stu-id="5ee56-120">**IgnoreSchema**</span></span>|<span data-ttu-id="5ee56-121"><xref:System.Data.DataSet> の現在の内容を XML スキーマを含まない XML データとして書き込みます。</span><span class="sxs-lookup"><span data-stu-id="5ee56-121">Writes the current contents of the <xref:System.Data.DataSet> as XML data, without an XML Schema.</span></span> <span data-ttu-id="5ee56-122">既定値です。</span><span class="sxs-lookup"><span data-stu-id="5ee56-122">This is the default.</span></span>|  
|<span data-ttu-id="5ee56-123">**WriteSchema**</span><span class="sxs-lookup"><span data-stu-id="5ee56-123">**WriteSchema**</span></span>|<span data-ttu-id="5ee56-124"><xref:System.Data.DataSet> の現在の内容を XML データとして書き込みます。このとき、リレーショナル構造がインライン XML スキーマとして書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="5ee56-124">Writes the current contents of the <xref:System.Data.DataSet> as XML data with the relational structure as inline XML Schema.</span></span>|  
|<span data-ttu-id="5ee56-125">**DiffGram**</span><span class="sxs-lookup"><span data-stu-id="5ee56-125">**DiffGram**</span></span>|<span data-ttu-id="5ee56-126">元の値と現在の値を含め、<xref:System.Data.DataSet> 全体を DiffGram として書き込みます。</span><span class="sxs-lookup"><span data-stu-id="5ee56-126">Writes the entire <xref:System.Data.DataSet> as a DiffGram, including original and current values.</span></span> <span data-ttu-id="5ee56-127">詳細については、次を参照してください。 [Diffgram](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)です。</span><span class="sxs-lookup"><span data-stu-id="5ee56-127">For more information, see [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md).</span></span>|  
  
 <span data-ttu-id="5ee56-128">XML 表現を記述する場合、<xref:System.Data.DataSet>を格納している**DataRelation**オブジェクト、結果の XML 要素が関連する親要素内で入れ子になった各リレーションシップの子行があるにする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5ee56-128">When writing an XML representation of a <xref:System.Data.DataSet> that contains **DataRelation** objects, you will most likely want the resulting XML to have the child rows of each relation nested within their related parent elements.</span></span> <span data-ttu-id="5ee56-129">これを実現するには、設定、**入れ子になった**のプロパティ、 **DataRelation**に**true**を追加すると、 **DataRelation** に<xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="5ee56-129">To accomplish this, set the **Nested** property of the **DataRelation** to **true** when you add the **DataRelation** to the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="5ee56-130">詳細については、次を参照してください。 [Datarelation の入れ子](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)です。</span><span class="sxs-lookup"><span data-stu-id="5ee56-130">For more information, see [Nesting DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span></span>  
  
 <span data-ttu-id="5ee56-131"><xref:System.Data.DataSet> の XML 表現をファイルに書き込む 2 つの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5ee56-131">Following are two examples of how to write the XML representation of a <xref:System.Data.DataSet> to a file.</span></span> <span data-ttu-id="5ee56-132">最初の例は、文字列として、結果の XML ファイルの名前を渡します**WriteXml**です。</span><span class="sxs-lookup"><span data-stu-id="5ee56-132">The first example passes the file name for the resulting XML as a string to **WriteXml**.</span></span> <span data-ttu-id="5ee56-133">2 番目の例では、 **System.IO.StreamWriter**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="5ee56-133">The second example passes a **System.IO.StreamWriter** object.</span></span>  
  
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
  
## <a name="mapping-columns-to-xml-elements-attributes-and-text"></a><span data-ttu-id="5ee56-134">XML 要素、属性、およびテキストへの列の割り当て</span><span class="sxs-lookup"><span data-stu-id="5ee56-134">Mapping Columns to XML Elements, Attributes, and Text</span></span>  
 <span data-ttu-id="5ee56-135">テーブルの列を XML で表現する方法を指定することができますを使用して、 **ColumnMapping**のプロパティ、 **DataColumn**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="5ee56-135">You can specify how a column of a table is represented in XML using the **ColumnMapping** property of the **DataColumn** object.</span></span> <span data-ttu-id="5ee56-136">次の表は、さまざまな**MappingType**の値を**ColumnMapping**テーブルの列、および結果の XML のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="5ee56-136">The following table shows the different **MappingType** values for the **ColumnMapping** property of a table column, and the resulting XML.</span></span>  
  
|<span data-ttu-id="5ee56-137">MappingType の値</span><span class="sxs-lookup"><span data-stu-id="5ee56-137">MappingType value</span></span>|<span data-ttu-id="5ee56-138">説明</span><span class="sxs-lookup"><span data-stu-id="5ee56-138">Description</span></span>|  
|-----------------------|-----------------|  
|<span data-ttu-id="5ee56-139">**要素**</span><span class="sxs-lookup"><span data-stu-id="5ee56-139">**Element**</span></span>|<span data-ttu-id="5ee56-140">既定値です。</span><span class="sxs-lookup"><span data-stu-id="5ee56-140">This is the default.</span></span> <span data-ttu-id="5ee56-141">列が XML 要素として書き込まれます。このとき、ColumnName は要素名になり、列の内容は要素のテキストとして書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="5ee56-141">The column is written as an XML element where the ColumnName is the name of the element and the contents of the column are written as the text of the element.</span></span> <span data-ttu-id="5ee56-142">例えば:</span><span class="sxs-lookup"><span data-stu-id="5ee56-142">For example:</span></span><br /><br /> `<ColumnName>Column Contents</ColumnName>`|  
|<span data-ttu-id="5ee56-143">**属性**</span><span class="sxs-lookup"><span data-stu-id="5ee56-143">**Attribute**</span></span>|<span data-ttu-id="5ee56-144">列が、現在の行の XML 要素の XML 属性として書き込まれます。このとき、ColumnName は属性名になり、列の内容は属性の値として書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="5ee56-144">The column is written as an XML attribute of the XML element for the current row where the ColumnName is the name of the attribute and the contents of the column are written as the value of the attribute.</span></span> <span data-ttu-id="5ee56-145">例えば:</span><span class="sxs-lookup"><span data-stu-id="5ee56-145">For example:</span></span><br /><br /> `<RowElement ColumnName="Column Contents" />`|  
|<span data-ttu-id="5ee56-146">**SimpleContent**</span><span class="sxs-lookup"><span data-stu-id="5ee56-146">**SimpleContent**</span></span>|<span data-ttu-id="5ee56-147">列の内容が、現在の行の XML 要素のテキストとして書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="5ee56-147">The contents of the column are written as text in the XML element for the current row.</span></span> <span data-ttu-id="5ee56-148">例えば:</span><span class="sxs-lookup"><span data-stu-id="5ee56-148">For example:</span></span><br /><br /> `<RowElement>Column Contents</RowElement>`<br /><br /> <span data-ttu-id="5ee56-149">なお**SimpleContent**を持つテーブルの列を設定できません**要素**列または入れ子にされたリレーションシップです。</span><span class="sxs-lookup"><span data-stu-id="5ee56-149">Note that **SimpleContent** cannot be set for a column of a table that has **Element** columns or nested relations.</span></span>|  
|<span data-ttu-id="5ee56-150">**非表示**</span><span class="sxs-lookup"><span data-stu-id="5ee56-150">**Hidden**</span></span>|<span data-ttu-id="5ee56-151">列は XML 出力に書き込まれません。</span><span class="sxs-lookup"><span data-stu-id="5ee56-151">The column is not written in the XML output.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5ee56-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ee56-152">See Also</span></span>  
 [<span data-ttu-id="5ee56-153">DataSet での XML の使用</span><span class="sxs-lookup"><span data-stu-id="5ee56-153">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="5ee56-154">DiffGrams</span><span class="sxs-lookup"><span data-stu-id="5ee56-154">DiffGrams</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)  
 [<span data-ttu-id="5ee56-155">DataRelation の入れ子化</span><span class="sxs-lookup"><span data-stu-id="5ee56-155">Nesting DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 [<span data-ttu-id="5ee56-156">XSD としての DataSet スキーマ情報の書き込み</span><span class="sxs-lookup"><span data-stu-id="5ee56-156">Writing DataSet Schema Information as XSD</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-schema-information-as-xsd.md)  
 [<span data-ttu-id="5ee56-157">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="5ee56-157">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="5ee56-158">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="5ee56-158">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
