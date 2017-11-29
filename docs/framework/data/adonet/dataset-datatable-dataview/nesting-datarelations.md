---
title: "DataRelation の入れ子化"
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
ms.assetid: 9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: db7df753bf6066d3a89c46a82b66e47281076f95
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="nesting-datarelations"></a><span data-ttu-id="1d1f0-102">DataRelation の入れ子化</span><span class="sxs-lookup"><span data-stu-id="1d1f0-102">Nesting DataRelations</span></span>
<span data-ttu-id="1d1f0-103">データのリレーショナル表現では、各テーブルに含まれている行が、列または列セットを使用して相互に関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="1d1f0-103">In a relational representation of data, individual tables contain rows that are related to one another using a column or set of columns.</span></span> <span data-ttu-id="1d1f0-104">ADO.NET の <xref:System.Data.DataSet> では、テーブル間のリレーションシップは <xref:System.Data.DataRelation> を使用して実装されます。</span><span class="sxs-lookup"><span data-stu-id="1d1f0-104">In the ADO.NET <xref:System.Data.DataSet>, the relationship between tables is implemented using a <xref:System.Data.DataRelation>.</span></span> <span data-ttu-id="1d1f0-105">作成するときに、 **DataRelation**列の親子リレーションシップは、このリレーションだけをとおして管理されます。</span><span class="sxs-lookup"><span data-stu-id="1d1f0-105">When you create a **DataRelation**, the parent-child relationships of the columns are managed only through the relation.</span></span> <span data-ttu-id="1d1f0-106">テーブルと列はそれぞれ別個のエンティティです。</span><span class="sxs-lookup"><span data-stu-id="1d1f0-106">The tables and columns are separate entities.</span></span> <span data-ttu-id="1d1f0-107">XML のデータ階層表現では、子要素が入れ子の状態で含まれている親要素によって親子のリレーションシップが表現されます。</span><span class="sxs-lookup"><span data-stu-id="1d1f0-107">In the hierarchical representation of data that XML provides, the parent-child relationships are represented by parent elements that contain nested child elements.</span></span>  
  
 <span data-ttu-id="1d1f0-108">子オブジェクトの入れ子を容易にするときに、**データセット**と同期されて、<xref:System.Xml.XmlDataDocument>またはを使用して XML データとして書き込まれた**WriteXml**、 **DataRelation**公開、**入れ子になった**プロパティです。</span><span class="sxs-lookup"><span data-stu-id="1d1f0-108">To facilitate the nesting of child objects when a **DataSet** is synchronized with an <xref:System.Xml.XmlDataDocument> or written as XML data using **WriteXml**, the **DataRelation** exposes a **Nested** property.</span></span> <span data-ttu-id="1d1f0-109">設定、**入れ子になった**のプロパティ、 **DataRelation**に**true**子を XML データとして書き込まれるときに、親の列は入れ子にするリレーションシップの行と、または同期されている、 **XmlDataDocument**です。</span><span class="sxs-lookup"><span data-stu-id="1d1f0-109">Setting the **Nested** property of a **DataRelation** to **true** causes the child rows of the relation to be nested within the parent column when written as XML data or synchronized with an **XmlDataDocument**.</span></span> <span data-ttu-id="1d1f0-110">**入れ子になった**のプロパティ、 **DataRelation**は**false**既定でします。</span><span class="sxs-lookup"><span data-stu-id="1d1f0-110">The **Nested** property of the **DataRelation** is **false**, by default.</span></span>  
  
 <span data-ttu-id="1d1f0-111">たとえば、次**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="1d1f0-111">For example, consider the following **DataSet**.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT OrderID, CustomerID, OrderDate FROM Orders", connection)  
  
connection.Open()  
  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
customerAdapter.Fill(dataSet, "Customers")  
orderAdapter.Fill(dataSet, "Orders")  
  
connection.Close()  
  
Dim customerOrders As DataRelation = dataSet.Relations.Add( _  
  "CustOrders", dataSet.Tables("Customers").Columns("CustomerID"), _  
  dataSet.Tables("Orders").Columns("CustomerID"))  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT OrderID, CustomerID, OrderDate FROM Orders", connection);  
  
connection.Open();  
  
DataSet dataSet = new DataSet("CustomerOrders");  
customerAdapter.Fill(dataSet, "Customers");  
orderAdapter.Fill(dataSet, "Orders");  
  
connection.Close();  
  
DataRelation customerOrders = dataSet.Relations.Add(  
  "CustOrders", dataSet.Tables["Customers"].Columns["CustomerID"],  
  dataSet.Tables["Orders"].Columns["CustomerID"]);  
```  
  
 <span data-ttu-id="1d1f0-112">**入れ子になった**のプロパティ、 **DataRelation**オブジェクトに設定されていない**true**この**データセット**、子オブジェクトが入れ子になっていません。親要素内でときにこの**データセット**は XML データとして表されます。</span><span class="sxs-lookup"><span data-stu-id="1d1f0-112">Because the **Nested** property of the **DataRelation** object is not set to **true** for this **DataSet**, the child objects are not nested within the parent elements when this **DataSet** is represented as XML data.</span></span> <span data-ttu-id="1d1f0-113">XML 表現を変換する、**データセット**を格納している関連**データセット**入れ子でないデータの関係を使用できるパフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="1d1f0-113">Transforming the XML representation of a **DataSet** that contains related **DataSet**s with non-nested data relations can cause slow performance.</span></span> <span data-ttu-id="1d1f0-114">データ リレーションシップは入れ子にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1d1f0-114">We recommend that you nest the data relations.</span></span> <span data-ttu-id="1d1f0-115">これを行うには、設定、**入れ子になった**プロパティを**true**です。</span><span class="sxs-lookup"><span data-stu-id="1d1f0-115">To do this, set the **Nested** property to **true**.</span></span> <span data-ttu-id="1d1f0-116">次に、トップダウン階層形式の XPath クエリ式を使用してデータを検索、変換するコードを XSLT スタイル シートに記述します。</span><span class="sxs-lookup"><span data-stu-id="1d1f0-116">Then write code in the XSLT style sheet that uses top-down hierarchical XPath query expressions to locate and transform the data.</span></span>  
  
 <span data-ttu-id="1d1f0-117">次のコード例は、呼び出しの結果を示しています。 **WriteXml**上、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="1d1f0-117">The following code example shows the result from calling **WriteXml** on the **DataSet**.</span></span>  
  
```xml  
<CustomerOrders>  
  <Customers>  
    <CustomerID>ALFKI</CustomerID>  
    <CompanyName>Alfreds Futterkiste</CompanyName>  
  </Customers>  
  <Customers>  
    <CustomerID>ANATR</CustomerID>  
    <CompanyName>Ana Trujillo Emparedados y helados</CompanyName>  
  </Customers>  
  <Orders>  
    <OrderID>10643</OrderID>  
    <CustomerID>ALFKI</CustomerID>  
    <OrderDate>1997-08-25T00:00:00</OrderDate>  
  </Orders>  
  <Orders>  
    <OrderID>10692</OrderID>  
    <CustomerID>ALFKI</CustomerID>  
    <OrderDate>1997-10-03T00:00:00</OrderDate>  
  </Orders>  
  <Orders>  
    <OrderID>10308</OrderID>  
    <CustomerID>ANATR</CustomerID>  
    <OrderDate>1996-09-18T00:00:00</OrderDate>  
  </Orders>  
</CustomerOrders>  
```  
  
 <span data-ttu-id="1d1f0-118">注意してください、**顧客**要素および**Orders**要素が兄弟要素として表示されます。</span><span class="sxs-lookup"><span data-stu-id="1d1f0-118">Note that the **Customers** element and the **Orders** elements are shown as sibling elements.</span></span> <span data-ttu-id="1d1f0-119">必要な場合、 **Orders** 、それぞれの親要素の子として表示する要素、**入れ子になった**のプロパティ、 **DataRelation** に設定する必要があります**true**しするには、次を追加します。</span><span class="sxs-lookup"><span data-stu-id="1d1f0-119">If you wanted the **Orders** elements to show up as children of their respective parent elements, the **Nested** property of the **DataRelation** would need to be set to **true** and you would add the following:</span></span>  
  
```vb  
customerOrders.Nested = True  
```  
  
```csharp  
customerOrders.Nested = true;  
```  
  
 <span data-ttu-id="1d1f0-120">次のコードは、結果の出力は、のようになりますで、 **Orders**要素は、該当する親要素内で入れ子になっています。</span><span class="sxs-lookup"><span data-stu-id="1d1f0-120">The following code shows what the resulting output would look like, with the **Orders** elements nested within their respective parent elements.</span></span>  
  
```xml  
<CustomerOrders>  
  <Customers>  
    <CustomerID>ALFKI</CustomerID>  
    <Orders>  
      <OrderID>10643</OrderID>  
      <CustomerID>ALFKI</CustomerID>  
      <OrderDate>1997-08-25T00:00:00</OrderDate>  
    </Orders>  
    <Orders>  
      <OrderID>10692</OrderID>  
      <CustomerID>ALFKI</CustomerID>  
      <OrderDate>1997-10-03T00:00:00</OrderDate>  
    </Orders>  
    <CompanyName>Alfreds Futterkiste</CompanyName>  
  </Customers>  
  <Customers>  
    <CustomerID>ANATR</CustomerID>  
    <Orders>  
      <OrderID>10308</OrderID>  
      <CustomerID>ANATR</CustomerID>  
      <OrderDate>1996-09-18T00:00:00</OrderDate>  
    </Orders>  
    <CompanyName>Ana Trujillo Emparedados y helados</CompanyName>  
  </Customers>  
</CustomerOrders>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1d1f0-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="1d1f0-121">See Also</span></span>  
 [<span data-ttu-id="1d1f0-122">DataSet での XML の使用</span><span class="sxs-lookup"><span data-stu-id="1d1f0-122">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="1d1f0-123">DataRelation の追加</span><span class="sxs-lookup"><span data-stu-id="1d1f0-123">Adding DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)  
 [<span data-ttu-id="1d1f0-124">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="1d1f0-124">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="1d1f0-125">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="1d1f0-125">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
