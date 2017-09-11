---
title: "方法: 特定の名前を持つ兄弟の属性を検索する (XPath-LINQ to XML) (C#)"
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
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a11b36ebe7dd56dc94984f636644256045ec16d1
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-c"></a><span data-ttu-id="97912-102">方法: 特定の名前を持つ兄弟の属性を検索する (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="97912-102">How to: Find Attributes of Siblings with a Specific Name (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="97912-103">このトピックでは、コンテキスト ノードの兄弟が持つすべての属性を検索する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="97912-103">This topic shows how to find all attributes of the siblings of the context node.</span></span> <span data-ttu-id="97912-104">コレクション内にある特定の名前の属性のみが返されます。</span><span class="sxs-lookup"><span data-stu-id="97912-104">Only attributes with a specific name are returned in the collection.</span></span>  
  
 <span data-ttu-id="97912-105">XPath 式を次に示します。</span><span class="sxs-lookup"><span data-stu-id="97912-105">The XPath expression is:</span></span>  
  
 `../Book/@id`  
  
## <a name="example"></a><span data-ttu-id="97912-106">例</span><span class="sxs-lookup"><span data-stu-id="97912-106">Example</span></span>  
 <span data-ttu-id="97912-107">この例では、最初に `Book` 要素を検索し、次に `Book` という名前の兄弟要素をすべて検索します。その後、`id` という名前の属性をすべて検索します。</span><span class="sxs-lookup"><span data-stu-id="97912-107">This example first finds a `Book` element, and then finds all sibling elements named `Book`, and then finds all attributes named `id`.</span></span> <span data-ttu-id="97912-108">結果は属性のコレクションです。</span><span class="sxs-lookup"><span data-stu-id="97912-108">The result is a collection of attributes.</span></span>  
  
 <span data-ttu-id="97912-109">この例では、「[サンプル XML ファイル: 書籍 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="97912-109">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument books = XDocument.Load("Books.xml");  
  
XElement book =   
    books  
    .Root  
    .Element("Book");  
  
// LINQ to XML query  
IEnumerable<XAttribute> list1 =  
    from el in book.Parent.Elements("Book")  
    select el.Attribute("id");  
  
// XPath expression  
IEnumerable<XAttribute> list2 =  
  ((IEnumerable)book.XPathEvaluate("../Book/@id")).Cast<XAttribute>();  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XAttribute el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="97912-110">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="97912-110">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
id="bk102"  
```  
  
## <a name="see-also"></a><span data-ttu-id="97912-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="97912-111">See Also</span></span>  
 [<span data-ttu-id="97912-112">XPath ユーザー向けの LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="97912-112">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)

