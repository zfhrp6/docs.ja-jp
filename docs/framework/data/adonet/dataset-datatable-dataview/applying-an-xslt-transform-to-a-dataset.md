---
title: "DataSet への XSLT 変換の適用"
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
ms.assetid: 09f2e4ee-1d08-4ba8-8936-83394fee319d
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 35251c5e2a713463510b3ff8b65e9096385c6bcf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="applying-an-xslt-transform-to-a-dataset"></a><span data-ttu-id="cbe30-102">DataSet への XSLT 変換の適用</span><span class="sxs-lookup"><span data-stu-id="cbe30-102">Applying an XSLT Transform to a DataSet</span></span>
<span data-ttu-id="cbe30-103">**WriteXml**のメソッド、<xref:System.Data.DataSet>の内容を記述することができます、**データセット**XML データとして。</span><span class="sxs-lookup"><span data-stu-id="cbe30-103">The **WriteXml** method of the <xref:System.Data.DataSet> enables you to write the contents of a **DataSet** as XML data.</span></span> <span data-ttu-id="cbe30-104">一般的なタスクは、XSLT (XSL Transformation) を使用してこの XML を別の形式へ変換する操作です。</span><span class="sxs-lookup"><span data-stu-id="cbe30-104">A common task is to then transform that XML to another format using XSL transformations (XSLT).</span></span> <span data-ttu-id="cbe30-105">ただし、同期、**データセット**で、<xref:System.Xml.XmlDataDocument>の内容に XSLT スタイル シートを適用することができます、**データセット**を最初の内容を記述しなくても、 **データセット**を使用して XML データとして**WriteXml**です。</span><span class="sxs-lookup"><span data-stu-id="cbe30-105">However, synchronizing a **DataSet** with an <xref:System.Xml.XmlDataDocument> enables you to apply an XSLT stylesheet to the contents of a **DataSet** without having to first write the contents of the **DataSet** as XML data using **WriteXml**.</span></span>  
  
 <span data-ttu-id="cbe30-106">次の例では、設定、**データセット**によるテーブルおよびリレーションシップでは、同期、**データセット**で、 **XmlDataDocument**、し、の一部を書き込みます**データセット**HTML ファイルとして、XSLT スタイル シートを使用します。</span><span class="sxs-lookup"><span data-stu-id="cbe30-106">The following example populates a **DataSet** with tables and relationships, synchronizes the **DataSet** with an **XmlDataDocument**, and writes a portion of the **DataSet** as an HTML file using an XSLT stylesheet.</span></span> <span data-ttu-id="cbe30-107">次のコードは、XSLT スタイルシートの内容です。</span><span class="sxs-lookup"><span data-stu-id="cbe30-107">Following are the contents of the XSLT stylesheet.</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">  
  
<xsl:template match="CustomerOrders">  
  <HTML>  
  <STYLE>  
  BODY {font-family:verdana;font-size:9pt}  
  TD   {font-size:8pt}  
  </STYLE>  
    <BODY>  
    <TABLE BORDER="1">  
      <xsl:apply-templates select="Customers"/>  
    </TABLE>  
    </BODY>  
  </HTML>  
</xsl:template>  
  
<xsl:template match="Customers">  
    <TR><TD>  
      <xsl:value-of select="ContactName"/>, <xsl:value-of select="Phone"/><BR/>  
    </TD></TR>  
      <xsl:apply-templates select="Orders"/>  
</xsl:template>  
  
<xsl:template match="Orders">  
  <TABLE BORDER="1">  
    <TR><TD valign="top"><B>Order:</B></TD><TD valign="top"><xsl:value-of select="OrderID"/></TD></TR>  
    <TR><TD valign="top"><B>Date:</B></TD><TD valign="top"><xsl:value-of select="OrderDate"/></TD></TR>  
    <TR><TD valign="top"><B>Ship To:</B></TD>  
        <TD valign="top"><xsl:value-of select="ShipName"/><BR/>  
        <xsl:value-of select="ShipAddress"/><BR/>  
        <xsl:value-of select="ShipCity"/>, <xsl:value-of select="ShipRegion"/>  <xsl:value-of select="ShipPostalCode"/><BR/>  
        <xsl:value-of select="ShipCountry"/></TD></TR>  
  </TABLE>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
 <span data-ttu-id="cbe30-108">次のコードがいっぱいになった、**データセット**し、XSLT スタイル シートを適用します。</span><span class="sxs-lookup"><span data-stu-id="cbe30-108">The following code fills the **DataSet** and applies the XSLT style sheet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cbe30-109">XSLT スタイル シートを適用する場合、**データセット**関係が含まれる、設定した場合に最適なパフォーマンスを実現する、**入れ子になった**のプロパティ、<xref:System.Data.DataRelation>に**true**列ごとの関係を入れ子にします。</span><span class="sxs-lookup"><span data-stu-id="cbe30-109">If you are applying an XSLT style sheet to a **DataSet** that contains relations, you achieve best performance if you set the **Nested** property of the <xref:System.Data.DataRelation> to **true** for each nested relation.</span></span> <span data-ttu-id="cbe30-110">これにより、階層を自然な順番で上から下へと進みながらデータを変換する XSLT スタイル シートを利用できるようになります。パフォーマンスに大きく影響する XPath ロケーション軸 (たとえば、スタイル シートのノード テスト式での preceding-sibling や following-sibling) を使用して階層をたどる必要はなくなります。</span><span class="sxs-lookup"><span data-stu-id="cbe30-110">This allows you to use XSLT style sheets that implement natural top-down processing to navigate the hierarchy and transform the data, as opposed to using performance-intensive XPath location axes (for example, preceding-sibling and following-sibling in style sheet node test expressions) to navigate it.</span></span> <span data-ttu-id="cbe30-111">入れ子になったリレーションシップの詳細については、次を参照してください。 [Datarelation の入れ子](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)です。</span><span class="sxs-lookup"><span data-stu-id="cbe30-111">For more information on nested relations, see [Nesting DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Customers", connection)  
customerAdapter.Fill(dataSet, "Customers")  
  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Orders", connection)  
orderAdapter.Fill(dataSet, "Orders")  
  
connection.Close()  
  
dataSet.Relations.Add("CustOrders", _  
dataSet.Tables("Customers").Columns("CustomerID"), _  
dataSet.Tables("Orders").Columns("CustomerID")).Nested = true  
  
Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)   
  
Dim xslTran As XslTransform = New XslTransform  
xslTran.Load("transform.xsl")  
  
Dim writer As XmlTextWriter = New XmlTextWriter( _  
  "xslt_output.html", System.Text.Encoding.UTF8)  
  
xslTran.Transform(xmlDoc, Nothing, writer)  
writer.Close()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
connection.Open();  
  
DataSet custDS = new DataSet("CustomerDataSet");  
  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT * FROM Customers", connection);  
customerAdapter.Fill(custDS, "Customers");  
  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT * FROM Orders", connection);  
orderAdapter.Fill(custDS, "Orders");  
  
connection.Close();  
  
custDS.Relations.Add("CustOrders",  
  custDS.Tables["Customers"].Columns["CustomerID"],  
                     custDS.Tables["Orders"].Columns["CustomerID"]).Nested = true;  
  
XmlDataDocument xmlDoc = new XmlDataDocument(custDS);   
  
XslTransform xslTran = new XslTransform();  
xslTran.Load("transform.xsl");  
  
XmlTextWriter writer = new XmlTextWriter("xslt_output.html",   
  System.Text.Encoding.UTF8);  
  
xslTran.Transform(xmlDoc, null, writer);  
writer.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="cbe30-112">参照</span><span class="sxs-lookup"><span data-stu-id="cbe30-112">See Also</span></span>  
 [<span data-ttu-id="cbe30-113">DataSet と XmlDataDocument の同期</span><span class="sxs-lookup"><span data-stu-id="cbe30-113">DataSet and XmlDataDocument Synchronization</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)  
 [<span data-ttu-id="cbe30-114">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="cbe30-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
