---
title: "方法: XSD を使用して検証する (LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 6a7f83a9-2d74-4c2b-8417-0a8595879516
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8ec86ee033d44c7d9da1b3a734cb6746dbff31eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-validate-using-xsd-linq-to-xml-c"></a><span data-ttu-id="12ffd-102">方法: XSD を使用して検証する (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="12ffd-102">How to: Validate Using XSD (LINQ to XML) (C#)</span></span>
<span data-ttu-id="12ffd-103"><xref:System.Xml.Schema> 名前空間には、XML スキーマ定義言語 (XSD) ファイルに対して XML ツリーを簡単に検証できる拡張メソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="12ffd-103">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XML Schema Definition Language (XSD) file.</span></span> <span data-ttu-id="12ffd-104">詳細については、<xref:System.Xml.Schema.Extensions.Validate%2A> メソッドのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="12ffd-104">For more information, see the <xref:System.Xml.Schema.Extensions.Validate%2A> method documentation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12ffd-105">例</span><span class="sxs-lookup"><span data-stu-id="12ffd-105">Example</span></span>  
 <span data-ttu-id="12ffd-106">次の例では、<xref:System.Xml.Schema.XmlSchemaSet> を作成し、このスキーマ セットに対して 2 つの <xref:System.Xml.Linq.XDocument> オブジェクトを検証します。</span><span class="sxs-lookup"><span data-stu-id="12ffd-106">The following example creates an <xref:System.Xml.Schema.XmlSchemaSet>, then validates two <xref:System.Xml.Linq.XDocument> objects against the schema set.</span></span> <span data-ttu-id="12ffd-107">ドキュメントの 1 つは有効ですが、その他のドキュメントは無効です。</span><span class="sxs-lookup"><span data-stu-id="12ffd-107">One of the documents is valid, the other is not.</span></span>  
  
```csharp  
string xsdMarkup =  
    @"<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'>  
       <xsd:element name='Root'>  
        <xsd:complexType>  
         <xsd:sequence>  
          <xsd:element name='Child1' minOccurs='1' maxOccurs='1'/>  
          <xsd:element name='Child2' minOccurs='1' maxOccurs='1'/>  
         </xsd:sequence>  
        </xsd:complexType>  
       </xsd:element>  
      </xsd:schema>";  
XmlSchemaSet schemas = new XmlSchemaSet();  
schemas.Add("", XmlReader.Create(new StringReader(xsdMarkup)));  
  
XDocument doc1 = new XDocument(  
    new XElement("Root",  
        new XElement("Child1", "content1"),  
        new XElement("Child2", "content1")  
    )  
);  
  
XDocument doc2 = new XDocument(  
    new XElement("Root",  
        new XElement("Child1", "content1"),  
        new XElement("Child3", "content1")  
    )  
);  
  
Console.WriteLine("Validating doc1");  
bool errors = false;  
doc1.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("doc1 {0}", errors ? "did not validate" : "validated");  
  
Console.WriteLine();  
Console.WriteLine("Validating doc2");  
errors = false;  
doc2.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("doc2 {0}", errors ? "did not validate" : "validated");  
```  
  
 <span data-ttu-id="12ffd-108">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="12ffd-108">This example produces the following output:</span></span>  
  
```  
Validating doc1  
doc1 validated  
  
Validating doc2  
The element 'Root' has invalid child element 'Child3'. List of possible elements expected: 'Child2'.  
doc2 did not validate  
```  
  
## <a name="example"></a><span data-ttu-id="12ffd-109">例</span><span class="sxs-lookup"><span data-stu-id="12ffd-109">Example</span></span>  
 <span data-ttu-id="12ffd-110">次の例では、「[サンプル XML ファイル: 顧客と注文 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md)」の XML ドキュメントが「[サンプル XSD ファイル : 顧客と注文](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md)」のスキーマに従った有効なものであるかどうかを検証します。</span><span class="sxs-lookup"><span data-stu-id="12ffd-110">The following example validates that the XML document from [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md) is valid per the schema from [Sample XSD File: Customers and Orders](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span></span> <span data-ttu-id="12ffd-111">次に、ソース XML ドキュメントを変更します。</span><span class="sxs-lookup"><span data-stu-id="12ffd-111">It then modifies the source XML document.</span></span> <span data-ttu-id="12ffd-112">変更するのは最初の顧客の `CustomerID` 属性です。</span><span class="sxs-lookup"><span data-stu-id="12ffd-112">It changes the `CustomerID` attribute on the first customer.</span></span> <span data-ttu-id="12ffd-113">変更が完了すると、存在しない顧客を注文が参照するようになります。したがって、この XML ドキュメントは有効ではなくなります。</span><span class="sxs-lookup"><span data-stu-id="12ffd-113">After the change, orders will then refer to a customer that does not exist, so the XML document will no longer validate.</span></span>  
  
 <span data-ttu-id="12ffd-114">この例では、「[サンプル XML ファイル: 顧客と注文 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="12ffd-114">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
 <span data-ttu-id="12ffd-115">この例では、「[サンプル XSD ファイル: 顧客と注文](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md)」の XSD スキーマを使用します。</span><span class="sxs-lookup"><span data-stu-id="12ffd-115">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](../../../../csharp/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders1.md).</span></span>  
  
```csharp  
XmlSchemaSet schemas = new XmlSchemaSet();  
schemas.Add("", "CustomersOrders.xsd");  
  
Console.WriteLine("Attempting to validate");  
XDocument custOrdDoc = XDocument.Load("CustomersOrders.xml");  
bool errors = false;  
custOrdDoc.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");  
  
Console.WriteLine();  
// Modify the source document so that it will not validate.  
custOrdDoc.Root.Element("Orders").Element("Order").Element("CustomerID").Value = "AAAAA";  
Console.WriteLine("Attempting to validate after modification");  
errors = false;  
custOrdDoc.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");  
```  
  
 <span data-ttu-id="12ffd-116">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="12ffd-116">This example produces the following output:</span></span>  
  
```  
Attempting to validate  
custOrdDoc validated  
  
Attempting to validate after modification  
The key sequence 'AAAAA' in Keyref fails to refer to some key.  
custOrdDoc did not validate  
```  
  
## <a name="see-also"></a><span data-ttu-id="12ffd-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="12ffd-117">See Also</span></span>  
 <xref:System.Xml.Schema.Extensions.Validate%2A>  
 [<span data-ttu-id="12ffd-118">XML ツリーの作成 (C#)</span><span class="sxs-lookup"><span data-stu-id="12ffd-118">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
