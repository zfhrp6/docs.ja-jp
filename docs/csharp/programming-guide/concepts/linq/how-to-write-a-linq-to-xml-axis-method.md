---
title: "方法: LINQ to XML 軸メソッドを記述する (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 50aef06b-1d22-4718-a18a-21237e26d7c1
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2f931bf850b094cf35db7c88aaf7aba9910f8c94
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-write-a-linq-to-xml-axis-method-c"></a><span data-ttu-id="8fcdc-102">方法: LINQ to XML 軸メソッドを記述する (C#)</span><span class="sxs-lookup"><span data-stu-id="8fcdc-102">How to: Write a LINQ to XML Axis Method (C#)</span></span>
<span data-ttu-id="8fcdc-103">XML ツリーからコレクションを取得する独自の軸メソッドを記述できます。</span><span class="sxs-lookup"><span data-stu-id="8fcdc-103">You can write your own axis methods to retrieve collections from an XML tree.</span></span> <span data-ttu-id="8fcdc-104">これを行うための最適な方法の 1 つは、要素または属性のコレクションを返す拡張メソッドを記述することです。</span><span class="sxs-lookup"><span data-stu-id="8fcdc-104">One of the best ways to do this is to write an extension method that returns a collection of elements or attributes.</span></span> <span data-ttu-id="8fcdc-105">アプリケーションの要件に基づいて、要素または属性の特定のサブセットを返す拡張メソッドを記述できます。</span><span class="sxs-lookup"><span data-stu-id="8fcdc-105">You can write your extension method to return specific subsets of elements or attributes, based on the requirements of your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fcdc-106">例</span><span class="sxs-lookup"><span data-stu-id="8fcdc-106">Example</span></span>  
 <span data-ttu-id="8fcdc-107">次の例では、2 つの拡張メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="8fcdc-107">The following example uses two extension methods.</span></span> <span data-ttu-id="8fcdc-108">最初の拡張メソッドである `GetXPath` は、<xref:System.Xml.Linq.XObject> を処理して、評価時にノードまたは属性を返す XPath 式を返します。</span><span class="sxs-lookup"><span data-stu-id="8fcdc-108">The first extension method, `GetXPath`, operates on <xref:System.Xml.Linq.XObject>, and returns an XPath expression that when evaluated will return the node or attribute.</span></span> <span data-ttu-id="8fcdc-109">2 番目の拡張メソッドである `Find` は、<xref:System.Xml.Linq.XElement> を処理して、</span><span class="sxs-lookup"><span data-stu-id="8fcdc-109">The second extension method, `Find`, operates on <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="8fcdc-110">指定されたテキストを含む <xref:System.Xml.Linq.XAttribute> オブジェクトと <xref:System.Xml.Linq.XElement> オブジェクトのコレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="8fcdc-110">It returns a collection of <xref:System.Xml.Linq.XAttribute> objects and <xref:System.Xml.Linq.XElement> objects that contain some specified text.</span></span>  
  
 <span data-ttu-id="8fcdc-111">この例では、「[サンプル XML ファイル: 複数の購買発注書 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="8fcdc-111">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```csharp  
public static class MyExtensions  
{  
    private static string GetQName(XElement xe)  
    {  
        string prefix = xe.GetPrefixOfNamespace(xe.Name.Namespace);  
        if (xe.Name.Namespace == XNamespace.None || prefix == null)  
            return xe.Name.LocalName.ToString();  
        else  
            return prefix + ":" + xe.Name.LocalName.ToString();  
    }  
  
    private static string GetQName(XAttribute xa)  
    {  
        string prefix =  
            xa.Parent.GetPrefixOfNamespace(xa.Name.Namespace);  
        if (xa.Name.Namespace == XNamespace.None || prefix == null)  
            return xa.Name.ToString();  
        else  
            return prefix + ":" + xa.Name.LocalName;  
    }  
  
    private static string NameWithPredicate(XElement el)  
    {  
        if (el.Parent != null && el.Parent.Elements(el.Name).Count() != 1)  
            return GetQName(el) + "[" +   
                (el.ElementsBeforeSelf(el.Name).Count() + 1) + "]";  
        else  
            return GetQName(el);  
    }  
  
    public static string StrCat<T>(this IEnumerable<T> source,  
        string separator)  
    {  
        return source.Aggregate(new StringBuilder(),  
                   (sb, i) => sb  
                       .Append(i.ToString())  
                       .Append(separator),  
                   s => s.ToString());  
    }  
  
    public static string GetXPath(this XObject xobj)  
    {  
        if (xobj.Parent == null)  
        {  
            XDocument doc = xobj as XDocument;  
            if (doc != null)  
                return ".";  
            XElement el = xobj as XElement;  
            if (el != null)  
                return "/" + NameWithPredicate(el);  
            // the XPath data model does not include white space text nodes  
            // that are children of a document, so this method returns null.  
            XText xt = xobj as XText;  
            if (xt != null)  
                return null;  
            XComment com = xobj as XComment;  
            if (com != null)  
                return  
                    "/" +  
                    (  
                        com  
                        .Document  
                        .Nodes()  
                        .OfType<XComment>()  
                        .Count() != 1 ?  
                        "comment()[" +  
                        (com  
                        .NodesBeforeSelf()  
                        .OfType<XComment>()  
                        .Count() + 1) +  
                        "]" :  
                        "comment()"  
                    );  
            XProcessingInstruction pi = xobj as XProcessingInstruction;  
            if (pi != null)  
                return  
                    "/" +  
                    (  
                        pi.Document.Nodes()  
                        .OfType<XProcessingInstruction>()  
                        .Count() != 1 ?  
                        "processing-instruction()[" +  
                        (pi  
                        .NodesBeforeSelf()  
                        .OfType<XProcessingInstruction>()  
                        .Count() + 1) +  
                        "]" :  
                        "processing-instruction()"  
                    );  
            return null;  
        }  
        else  
        {  
            XElement el = xobj as XElement;  
            if (el != null)  
            {  
                return  
                    "/" +  
                    el  
                    .Ancestors()  
                    .InDocumentOrder()  
                    .Select(e => NameWithPredicate(e))  
                    .StrCat("/") +  
                    NameWithPredicate(el);  
            }  
            XAttribute at = xobj as XAttribute;  
            if (at != null)  
                return  
                    "/" +  
                    at  
                    .Parent  
                    .AncestorsAndSelf()  
                    .InDocumentOrder()  
                    .Select(e => NameWithPredicate(e))  
                    .StrCat("/") +  
                    "@" + GetQName(at);  
            XComment com = xobj as XComment;  
            if (com != null)  
                return  
                    "/" +  
                    com  
                    .Parent  
                    .AncestorsAndSelf()  
                    .InDocumentOrder()  
                    .Select(e => NameWithPredicate(e))  
                    .StrCat("/") +  
                    (  
                        com  
                        .Parent  
                        .Nodes()  
                        .OfType<XComment>()  
                        .Count() != 1 ?  
                        "comment()[" +  
                        (com  
                        .NodesBeforeSelf()  
                        .OfType<XComment>()  
                        .Count() + 1) + "]" :  
                        "comment()"  
                    );  
            XCData cd = xobj as XCData;  
            if (cd != null)  
                return  
                    "/" +  
                    cd  
                    .Parent  
                    .AncestorsAndSelf()  
                    .InDocumentOrder()  
                    .Select(e => NameWithPredicate(e))  
                    .StrCat("/") +  
                    (  
                        cd  
                        .Parent  
                        .Nodes()  
                        .OfType<XText>()  
                        .Count() != 1 ?  
                        "text()[" +  
                        (cd  
                        .NodesBeforeSelf()  
                        .OfType<XText>()  
                        .Count() + 1) + "]" :  
                        "text()"  
                    );  
            XText tx = xobj as XText;  
            if (tx != null)  
                return  
                    "/" +  
                    tx  
                    .Parent  
                    .AncestorsAndSelf()  
                    .InDocumentOrder()  
                    .Select(e => NameWithPredicate(e))  
                    .StrCat("/") +  
                    (  
                        tx  
                        .Parent  
                        .Nodes()  
                        .OfType<XText>()  
                        .Count() != 1 ?  
                        "text()[" +  
                        (tx  
                        .NodesBeforeSelf()  
                        .OfType<XText>()  
                        .Count() + 1) + "]" :  
                        "text()"  
                    );  
            XProcessingInstruction pi = xobj as XProcessingInstruction;  
            if (pi != null)  
                return  
                    "/" +  
                    pi  
                    .Parent  
                    .AncestorsAndSelf()  
                    .InDocumentOrder()  
                    .Select(e => NameWithPredicate(e))  
                    .StrCat("/") +  
                    (  
                        pi  
                        .Parent  
                        .Nodes()  
                        .OfType<XProcessingInstruction>()  
                        .Count() != 1 ?  
                        "processing-instruction()[" +  
                        (pi  
                        .NodesBeforeSelf()  
                        .OfType<XProcessingInstruction>()  
                        .Count() + 1) + "]" :  
                        "processing-instruction()"  
                    );  
            return null;  
        }  
    }  
  
    public static IEnumerable<XObject> Find(this XElement source, string value)  
    {  
        if (source.Attributes().Any())  
        {  
            foreach (XAttribute att in source.Attributes())  
            {  
                string contents = (string)att;  
                if (contents.Contains(value))  
                    yield return att;  
            }  
        }  
        if (source.Elements().Any())  
        {  
            foreach (XElement child in source.Elements())  
                foreach (XObject s in child.Find(value))  
                    yield return s;  
        }  
        else  
        {  
            string contents = (string)source;  
            if (contents.Contains(value))  
                yield return source;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        XElement purchaseOrders = XElement.Load("PurchaseOrders.xml");  
  
        IEnumerable<XObject> subset =  
            from xobj in purchaseOrders.Find("1999")  
            select xobj;  
  
        foreach (XObject obj in subset)  
        {  
            Console.WriteLine(obj.GetXPath());  
            if (obj.GetType() == typeof(XElement))  
                Console.WriteLine(((XElement)obj).Value);  
            else if (obj.GetType() == typeof(XAttribute))  
                Console.WriteLine(((XAttribute)obj).Value);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="8fcdc-112">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="8fcdc-112">This code produces the following output:</span></span>  
  
```  
/PurchaseOrders/PurchaseOrder[1]/@OrderDate  
1999-10-20  
/PurchaseOrders/PurchaseOrder[1]/Items/Item[2]/ShipDate  
1999-05-21  
/PurchaseOrders/PurchaseOrder[2]/@OrderDate  
1999-10-22  
/PurchaseOrders/PurchaseOrder[3]/@OrderDate  
1999-10-22  
```  
  
## <a name="see-also"></a><span data-ttu-id="8fcdc-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="8fcdc-113">See Also</span></span>  
 [<span data-ttu-id="8fcdc-114">高度なクエリ手法 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8fcdc-114">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)

