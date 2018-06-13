---
title: XSD としての DataSet スキーマ情報の書き込み
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
ms.openlocfilehash: b2012b32b0751bc093b9b3267cbbfc2e1a408156
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761000"
---
# <a name="writing-dataset-schema-information-as-xsd"></a><span data-ttu-id="d52db-102">XSD としての DataSet スキーマ情報の書き込み</span><span class="sxs-lookup"><span data-stu-id="d52db-102">Writing DataSet Schema Information as XSD</span></span>
<span data-ttu-id="d52db-103"><xref:System.Data.DataSet> のスキーマを XML スキーマ定義言語 (XSD) スキーマとして書き込むと、このスキーマを XML ドキュメントに転送できます。このとき関連データを含む定義、または関連データを含まない定義ができます。</span><span class="sxs-lookup"><span data-stu-id="d52db-103">You can write the schema of a <xref:System.Data.DataSet> as XML Schema definition language (XSD) schema, so that you can transport it, with or without related data, in an XML document.</span></span> <span data-ttu-id="d52db-104">XML スキーマは、ストリーム、ファイルに書き込むことが、 <xref:System.Xml.XmlWriter>、または文字列が厳密に型を生成するために役立ちます**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="d52db-104">XML Schema can be written to a file, a stream, an <xref:System.Xml.XmlWriter>, or a string; it is useful for generating a strongly typed **DataSet**.</span></span> <span data-ttu-id="d52db-105">詳細については厳密に型指定された**データセット**、オブジェクトを参照してください[型指定されたデータセット](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)です。</span><span class="sxs-lookup"><span data-stu-id="d52db-105">For more information about strongly typed **DataSet** objects, see [Typed DataSets](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span></span>  
  
 <span data-ttu-id="d52db-106">XML スキーマでテーブルの列を表現する方法を指定することができますを使用して、 **ColumnMapping**のプロパティ、<xref:System.Data.DataColumn>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d52db-106">You can specify how a column of a table is represented in XML Schema using the **ColumnMapping** property of the <xref:System.Data.DataColumn> object.</span></span> <span data-ttu-id="d52db-107">詳細についてを参照してください「列に XML 要素、属性、およびテキストのマッピングを」[書き込み DataSet の内容を XML データとして](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)です。</span><span class="sxs-lookup"><span data-stu-id="d52db-107">For more information, see "Mapping Columns to XML Elements, Attributes, and Text" in [Writing DataSet Contents as XML Data](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).</span></span>  
  
 <span data-ttu-id="d52db-108">スキーマを記述する、**データセット**をファイルに、XML スキーマとして、ストリームまたは**XmlWriter**を使用して、 **WriteXmlSchema**のメソッド、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="d52db-108">To write the schema of a **DataSet** as XML Schema, to a file, stream, or **XmlWriter**, use the **WriteXmlSchema** method of the **DataSet**.</span></span> <span data-ttu-id="d52db-109">**WriteXmlSchema**結果の XML スキーマのコピー先を指定する 1 つのパラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="d52db-109">**WriteXmlSchema** takes one parameter that specifies the destination of the resulting XML Schema.</span></span> <span data-ttu-id="d52db-110">コード例を以下の XML スキーマを記述する方法、**データセット**ファイル名を含む文字列を渡すことによってファイルへと<xref:System.IO.StreamWriter>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d52db-110">The following code examples demonstrate how to write the XML Schema of a **DataSet** to a file by passing a string containing a file name and a <xref:System.IO.StreamWriter> object.</span></span>  
  
```vb  
dataSet.WriteXmlSchema("Customers.xsd")  
```  
  
```csharp  
dataSet.WriteXmlSchema("Customers.xsd");  
```  
  
```vb  
Dim writer As System.IO.StreamWriter = New System.IO.StreamWriter("Customers.xsd")  
dataSet.WriteXmlSchema(writer)  
writer.Close()  
```  
  
```csharp  
System.IO.StreamWriter writer = new System.IO.StreamWriter("Customers.xsd");  
dataSet.WriteXmlSchema(writer);  
writer.Close();  
```  
  
 <span data-ttu-id="d52db-111">スキーマを取得する、**データセット**、XML スキーマ文字列として書き込むと、使用、 **GetXmlSchema**メソッドを次の例で示すようにします。</span><span class="sxs-lookup"><span data-stu-id="d52db-111">To obtain the schema of a **DataSet** and write it as an XML Schema string, use the **GetXmlSchema** method, as shown in the following example.</span></span>  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a><span data-ttu-id="d52db-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="d52db-112">See Also</span></span>  
 [<span data-ttu-id="d52db-113">DataSet での XML の使用</span><span class="sxs-lookup"><span data-stu-id="d52db-113">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="d52db-114">DataSet 内容の XML データとしての書き込み</span><span class="sxs-lookup"><span data-stu-id="d52db-114">Writing DataSet Contents as XML Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 [<span data-ttu-id="d52db-115">型指定されたデータセット</span><span class="sxs-lookup"><span data-stu-id="d52db-115">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [<span data-ttu-id="d52db-116">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="d52db-116">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="d52db-117">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="d52db-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
