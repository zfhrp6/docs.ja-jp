---
title: "方法: XML ツリー (Visual Basic) の構造を変換 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 84b60854-48b2-452c-87f2-77d53e1d653a
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 9c535a06e70ebd299d7f6646576e703d7a0dda84
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---
# <a name="how-to-transform-the-shape-of-an-xml-tree-visual-basic"></a><span data-ttu-id="e059c-102">方法: XML ツリー (Visual Basic) の構造を変換</span><span class="sxs-lookup"><span data-stu-id="e059c-102">How to: Transform the Shape of an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="e059c-103">*図形*ドキュメントの XML 要素名、属性名、およびその階層の特性を表します。</span><span class="sxs-lookup"><span data-stu-id="e059c-103">The *shape* of an XML document refers to its element names, attribute names, and the characteristics of its hierarchy.</span></span>  
  
 <span data-ttu-id="e059c-104">XML ドキュメントの構造を変更しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="e059c-104">Sometimes you will have to change the shape of an XML document.</span></span> <span data-ttu-id="e059c-105">たとえば、既存の XML ドキュメントを、異なる要素名と属性名を必要とする別のシステムに送信するとします。</span><span class="sxs-lookup"><span data-stu-id="e059c-105">For example, you might have to send an existing XML document to another system that requires different element and attribute names.</span></span> <span data-ttu-id="e059c-106">ドキュメント全体を調べ、必要に応じて要素の削除や要素名の変更を行うことも可能ですが、関数型構築を使用する方が、読みやすく保守しやすいコードを生成できます。</span><span class="sxs-lookup"><span data-stu-id="e059c-106">You could go through the document, deleting and renaming elements as required, but using functional construction results in more readable and maintainable code.</span></span> <span data-ttu-id="e059c-107">関数型構築の詳細については、次を参照してください。[関数型構築 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="e059c-107">For more information about functional construction, see [Functional Construction (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="e059c-108">最初の例では、XML ドキュメントの編成を変更します。</span><span class="sxs-lookup"><span data-stu-id="e059c-108">The first example changes the organization of the XML document.</span></span> <span data-ttu-id="e059c-109">ここでは、複合要素をツリー内で移動します。</span><span class="sxs-lookup"><span data-stu-id="e059c-109">It moves complex elements from one location in the tree to another.</span></span>  
  
 <span data-ttu-id="e059c-110">このトピックの&2; 番目の例では、ソース ドキュメントと異なる構造を持つ XML ドキュメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="e059c-110">The second example in this topic creates an XML document with a different shape than the source document.</span></span> <span data-ttu-id="e059c-111">要素名の大文字小文字の区別を変更し、一部の要素名を変更し、ソース ツリーの一部の要素を変換後のツリーに含めないようにします。</span><span class="sxs-lookup"><span data-stu-id="e059c-111">It changes the casing of the element names, renames some elements, and leaves some elements from the source tree out of the transformed tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e059c-112">例</span><span class="sxs-lookup"><span data-stu-id="e059c-112">Example</span></span>  
 <span data-ttu-id="e059c-113">次のコードでは、組み込まれたクエリ式を使用して、XML ファイルの構造を変更します。</span><span class="sxs-lookup"><span data-stu-id="e059c-113">The following code changes the shape of an XML file using embedded query expressions.</span></span>  
  
 <span data-ttu-id="e059c-114">この例のソース XML ドキュメントでは、`Customers` 要素の下にある `Root` 要素に、すべての顧客が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e059c-114">The source XML document in this example contains a `Customers` element under the `Root` element that contains all customers.</span></span> <span data-ttu-id="e059c-115">また、`Orders` 要素の下には `Root` 要素もあり、すべての注文が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e059c-115">It also contains an `Orders` element under the `Root` element that contains all orders.</span></span> <span data-ttu-id="e059c-116">この例では、各顧客の注文が `Orders` 要素内の `Customer` 要素に含まれるような、新しい XML ツリーを作成します。</span><span class="sxs-lookup"><span data-stu-id="e059c-116">This example creates a new XML tree in which the orders for each customer are contained in an `Orders` element within the `Customer` element.</span></span> <span data-ttu-id="e059c-117">元のドキュメントでは、`CustomerID` 要素内に `Order` 要素も含まれています。構造変更後のドキュメントからは、この要素が削除されます。</span><span class="sxs-lookup"><span data-stu-id="e059c-117">The original document also contains a `CustomerID` element in the `Order` element; this element will be removed from the re-shaped document.</span></span>  
  
 <span data-ttu-id="e059c-118">この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: 顧客と注文 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="e059c-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim co As XElement = XElement.Load("CustomersOrders.xml")  
Dim newCustOrd = _  
    <Root>  
        <%= From cust In co.<Customers>.<Customer> _  
            Select _  
            <Customer>  
                <%= cust.Attributes() %>  
                <%= cust.Elements() %>  
                <Orders>  
                    <%= From ord In co.<Orders>.<Order> _  
                        Where ord.<CustomerID>.Value = cust.@CustomerID _  
                        Select _  
                        <Order>  
                            <%= ord.Attributes() %>  
                            <%= ord.<EmployeeID> %>  
                            <%= ord.<OrderDate> %>  
                            <%= ord.<RequiredDate> %>  
                            <%= ord.<ShipInfo> %>  
                        </Order> _  
                    %>  
                </Orders>  
            </Customer> _  
        %>  
    </Root>  
Console.WriteLine(newCustOrd)  
```  
  
 <span data-ttu-id="e059c-119">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="e059c-119">This code produces the following output:</span></span>  
  
```xml  
        <Root>  
<Customer CustomerID="GREAL">  
  <CompanyName>Great Lakes Food Market</CompanyName>  
  <ContactName>Howard Snyder</ContactName>  
  <ContactTitle>Marketing Manager</ContactTitle>  
  <Phone>(503) 555-7555</Phone>  
  <FullAddress>  
    <Address>2732 Baker Blvd.</Address>  
    <City>Eugene</City>  
    <Region>OR</Region>  
    <PostalCode>97403</PostalCode>  
    <Country>USA</Country>  
  </FullAddress>  
  <Orders />  
</Customer>  
<Customer CustomerID="HUNGC">  
  <CompanyName>Hungry Coyote Import Store</CompanyName>  
  <ContactName>Yoshi Latimer</ContactName>  
  <ContactTitle>Sales Representative</ContactTitle>  
  <Phone>(503) 555-6874</Phone>  
  <Fax>(503) 555-2376</Fax>  
  <FullAddress>  
    <Address>City Center Plaza 516 Main St.</Address>  
    <City>Elgin</City>  
    <Region>OR</Region>  
    <PostalCode>97827</PostalCode>  
    <Country>USA</Country>  
  </FullAddress>  
  <Orders />  
</Customer>  
. . .  
```  
  
## <a name="example"></a><span data-ttu-id="e059c-120">例</span><span class="sxs-lookup"><span data-stu-id="e059c-120">Example</span></span>  
 <span data-ttu-id="e059c-121">この例では、一部の要素の名前を変更し、一部の属性を要素に変換します。</span><span class="sxs-lookup"><span data-stu-id="e059c-121">This example renames some elements and converts some attributes to elements.</span></span>  
  
 <span data-ttu-id="e059c-122">コードの呼び出し`ConvertAddress`の一覧が返されます<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="e059c-122">The code calls `ConvertAddress`, which returns a list of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="e059c-123">メソッドの引数は、`Address` 属性の値が `Type` である `"Shipping"` 複合要素を特定するクエリです。</span><span class="sxs-lookup"><span data-stu-id="e059c-123">The argument to the method is a query that determines the `Address` complex element where the `Type` attribute has a value of `"Shipping"`.</span></span>  
  
 <span data-ttu-id="e059c-124">この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: 一般的な購買発注書 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="e059c-124">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
```vb  
Function ConvertAddress(ByVal add As XElement) As IEnumerable(Of XElement)  
    Dim fragment = New List(Of XElement)  
    fragment.Add(<NAME><%= add.<Name>.Value %></NAME>)  
    fragment.Add(<STREET><%= add.<Street>.Value %></STREET>)  
    fragment.Add(<CITY><%= add.<City>.Value %></CITY>)  
    fragment.Add(<ST><%= add.<State>.Value %></ST>)  
    fragment.Add(<POSTALCODE><%= add.<Zip>.Value %></POSTALCODE>)  
    fragment.Add(<COUNTRY><%= add.<Country>.Value %></COUNTRY>)  
    Return fragment  
End Function  
  
Sub Main()  
    Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
    Dim newPo As XElement = _  
        <PO>  
            <ID><%= po.@PurchaseOrderNumber %></ID>  
            <DATE><%= CDate(po.@OrderDate) %></DATE>  
            <%= _  
                ConvertAddress( _  
                (From el In po.<Address> _  
                Where el.@Type = "Shipping" _  
                Select el) _  
                .First() _  
                ) _  
            %>  
        </PO>  
    Console.WriteLine(newPo)  
End Sub  
```  
  
 <span data-ttu-id="e059c-125">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="e059c-125">This code produces the following output:</span></span>  
  
```xml  
<PO>  
  <ID>99503</ID>  
  <DATE>1999-10-20T00:00:00</DATE>  
  <NAME>Ellen Adams</NAME>  
  <STREET>123 Maple Street</STREET>  
  <CITY>Mill Valley</CITY>  
  <ST>CA</ST>  
  <POSTALCODE>10999</POSTALCODE>  
  <COUNTRY>USA</COUNTRY>  
</PO>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e059c-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="e059c-126">See Also</span></span>  
 [<span data-ttu-id="e059c-127">射影と変換 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e059c-127">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)

