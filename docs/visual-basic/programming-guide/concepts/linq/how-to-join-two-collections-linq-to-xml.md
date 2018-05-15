---
title: '方法: 2 つのコレクション (LINQ to XML) を結合 (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5a5758d4-906b-4285-908d-5b930db192e6
ms.openlocfilehash: 3ceb9cf7dfdd1d18a07e93d15624fd8fac045d07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-join-two-collections-linq-to-xml-visual-basic"></a><span data-ttu-id="431b7-102">方法: 2 つのコレクション (LINQ to XML) を結合 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="431b7-102">How to: Join Two Collections (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="431b7-103">XML ドキュメント内の要素または属性は、別の要素または属性を参照することがあります。</span><span class="sxs-lookup"><span data-stu-id="431b7-103">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="431b7-104">たとえば、「[サンプル XML ファイル: 顧客と注文 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md)」の XML ドキュメントには、顧客の一覧と注文の一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="431b7-104">For example, the [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md) XML document contains a list of customers and a list of orders.</span></span> <span data-ttu-id="431b7-105">各 `Customer` 要素には、`CustomerID` 属性が含まれています。</span><span class="sxs-lookup"><span data-stu-id="431b7-105">Each `Customer` element contains a `CustomerID` attribute.</span></span> <span data-ttu-id="431b7-106">各 `Order` 要素には、`CustomerID` 要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="431b7-106">Each `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="431b7-107">各注文の `CustomerID` 要素は、顧客の `CustomerID` 属性を参照します。</span><span class="sxs-lookup"><span data-stu-id="431b7-107">The `CustomerID` element in each order refers to the `CustomerID` attribute in a customer.</span></span>  
  
 <span data-ttu-id="431b7-108">「[サンプル XSD ファイル: 顧客と注文](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md)」のトピックには、このドキュメントの検証に使用できる XSD が含まれています。</span><span class="sxs-lookup"><span data-stu-id="431b7-108">The topic [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md) contains an XSD that can be used to validate this document.</span></span> <span data-ttu-id="431b7-109">この XSD は、XSD の `xs:key` 機能と `xs:keyref` 機能を使用して、`CustomerID` 要素の `Customer` 属性がキーであることを確立し、各 `CustomerID` 要素の `Order` 要素と各 `CustomerID` 要素の `Customer` 属性の間にリレーションシップを確立します。</span><span class="sxs-lookup"><span data-stu-id="431b7-109">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>  
  
 <span data-ttu-id="431b7-110">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] では、`Join` 句を使用することで、このリレーションシップを利用できます。</span><span class="sxs-lookup"><span data-stu-id="431b7-110">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can take advantage of this relationship by using the `Join` clause.</span></span>  
  
 <span data-ttu-id="431b7-111">使用できるインデックスがないため、このような結合では実行時のパフォーマンスが低下することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="431b7-111">Note that because there is no index available, such joining will have poor runtime performance.</span></span>  
  
 <span data-ttu-id="431b7-112">詳細については`Join`を参照してください[参加操作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md)です。</span><span class="sxs-lookup"><span data-stu-id="431b7-112">For more detailed information about `Join`, see [Join Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="431b7-113">例</span><span class="sxs-lookup"><span data-stu-id="431b7-113">Example</span></span>  
 <span data-ttu-id="431b7-114">次の例では、`Customer` 要素を `Order` 要素に結合し、注文に `CompanyName` 要素が含まれている新しい XML ドキュメントを生成します。</span><span class="sxs-lookup"><span data-stu-id="431b7-114">The following example joins the `Customer` elements to the `Order` elements, and generates a new XML document that includes the `CompanyName` element in the orders.</span></span>  
  
 <span data-ttu-id="431b7-115">クエリを実行する前に、この例では、ドキュメントが「[サンプル XSD ファイル: 顧客と注文](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md)」のスキーマに準拠しているかどうかを検証します。</span><span class="sxs-lookup"><span data-stu-id="431b7-115">Before executing the query, the example validates that the document complies with the schema in [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span></span> <span data-ttu-id="431b7-116">これにより、結合句が常に機能するようになります。</span><span class="sxs-lookup"><span data-stu-id="431b7-116">This ensures that the join clause will always work.</span></span>  
  
 <span data-ttu-id="431b7-117">このクエリでは、まずすべての `Customer` 要素を取得し、次にそれらを `Order` 要素に結合します。</span><span class="sxs-lookup"><span data-stu-id="431b7-117">This query first retrieves all `Customer` elements, and then joins them to the `Order` elements.</span></span> <span data-ttu-id="431b7-118">クエリでは、"K" より大きい `CustomerID` を持つ顧客の注文のみを選択します。</span><span class="sxs-lookup"><span data-stu-id="431b7-118">It selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="431b7-119">次に、各注文内に顧客情報を含む新しい `Order` 要素を射影します。</span><span class="sxs-lookup"><span data-stu-id="431b7-119">It then projects a new `Order` element that contains the customer information within each order.</span></span>  
  
 <span data-ttu-id="431b7-120">この例では、「[サンプル XML ファイル: 顧客と注文 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="431b7-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="431b7-121">この例では、「[サンプル XSD ファイル: 顧客と注文](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md)」の XSD スキーマを使用します。</span><span class="sxs-lookup"><span data-stu-id="431b7-121">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span></span>  
  
 <span data-ttu-id="431b7-122">この方式の結合ではパフォーマンスが低下することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="431b7-122">Note that joining in this fashion will not perform very well.</span></span> <span data-ttu-id="431b7-123">結合は線形探索によって実行されます。</span><span class="sxs-lookup"><span data-stu-id="431b7-123">Joins are performed via a linear search.</span></span> <span data-ttu-id="431b7-124">パフォーマンスを向上させるハッシュ テーブルまたはインデックスはありません。</span><span class="sxs-lookup"><span data-stu-id="431b7-124">There are no hash tables or indexes to help with performance.</span></span>  
  
```vb  
Public Class Program  
    Public Shared errors As Boolean = False  
  
    Public Shared Function LamValidEvent(ByVal o As Object, _  
                 ByVal e As ValidationEventArgs) As Boolean  
        Console.WriteLine("{0}", e.Message)  
        errors = True  
    End Function  
  
    Shared Sub Main()  
        Dim schemas As New XmlSchemaSet()  
        schemas.Add("", "CustomersOrders.xsd")  
  
        Console.Write("Attempting to validate, ")  
        Dim custOrdDoc As XDocument = XDocument.Load("CustomersOrders.xml")  
  
        custOrdDoc.Validate(schemas, Function(o, e) LamValidEvent(0, e))  
        If errors Then  
            Console.WriteLine("custOrdDoc did not validate")  
        Else  
            Console.WriteLine("custOrdDoc validated")  
        End If  
  
        If Not errors Then  
            'Join customers and orders, and create a new XML document with  
            ' a different shape.  
            'The new document contains orders only for customers with a  
            ' CustomerID > 'K'.  
            Dim custOrd As XElement = custOrdDoc.<Root>.FirstOrDefault  
            Dim newCustOrd As XElement = _  
                <Root>  
                    <%= From c In custOrd.<Customers>.<Customer> _  
                        Join o In custOrd.<Orders>.<Order> _  
                        On c.@CustomerID Equals o.<CustomerID>.Value _  
                        Where c.@CustomerID.CompareTo("K") > 0 _  
                        Select _  
                        <Order>  
                            <CustomerID><%= c.@CustomerID %></CustomerID>  
                            <%= c.<CompanyName> %>  
                            <%= c.<ContactName> %>  
                            <%= o.<EmployeeID> %>  
                            <%= o.<OrderDate> %>  
                        </Order> _  
                    %>  
                </Root>  
            Console.WriteLine(newCustOrd)  
        End If  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="431b7-125">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="431b7-125">This code produces the following output:</span></span>  
  
```  
Attempting to validate, custOrdDoc validated  
<Root>  
  <Order>  
    <CustomerID>LAZYK</CustomerID>  
    <CompanyName>Lazy K Kountry Store</CompanyName>  
    <ContactName>John Steel</ContactName>  
    <EmployeeID>1</EmployeeID>  
    <OrderDate>1997-03-21T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LAZYK</CustomerID>  
    <CompanyName>Lazy K Kountry Store</CompanyName>  
    <ContactName>John Steel</ContactName>  
    <EmployeeID>8</EmployeeID>  
    <OrderDate>1997-05-22T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>1</EmployeeID>  
    <OrderDate>1997-06-25T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>8</EmployeeID>  
    <OrderDate>1997-10-27T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>6</EmployeeID>  
    <OrderDate>1997-11-10T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>4</EmployeeID>  
    <OrderDate>1998-02-12T00:00:00</OrderDate>  
  </Order>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="431b7-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="431b7-126">See Also</span></span>  
 [<span data-ttu-id="431b7-127">詳細クエリ手法 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="431b7-127">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
