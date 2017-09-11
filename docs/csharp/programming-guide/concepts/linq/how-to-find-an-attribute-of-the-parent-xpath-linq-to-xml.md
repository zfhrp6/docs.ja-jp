---
title: "方法: 親の属性を検索する (XPath-LINQ to XML) (C#)"
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
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 612baa54e125a5559cc1416bf78d19862ce5d082
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a><span data-ttu-id="7ec06-102">方法: 親の属性を検索する (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="7ec06-102">How to: Find an Attribute of the Parent (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="7ec06-103">このトピックでは、親要素に移動してその属性を検索する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7ec06-103">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>  
  
 <span data-ttu-id="7ec06-104">XPath 式を次に示します。</span><span class="sxs-lookup"><span data-stu-id="7ec06-104">The XPath expression is:</span></span>  
  
 `../@id`  
  
## <a name="example"></a><span data-ttu-id="7ec06-105">例</span><span class="sxs-lookup"><span data-stu-id="7ec06-105">Example</span></span>  
 <span data-ttu-id="7ec06-106">この例では、まず `Author` 要素を検索します。</span><span class="sxs-lookup"><span data-stu-id="7ec06-106">This example first finds an `Author` element.</span></span> <span data-ttu-id="7ec06-107">次に、親要素の `id` 属性を検索します。</span><span class="sxs-lookup"><span data-stu-id="7ec06-107">It then finds the `id` attribute of the parent element.</span></span>  
  
 <span data-ttu-id="7ec06-108">この例では、「[サンプル XML ファイル: 書籍 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="7ec06-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument books = XDocument.Load("Books.xml");  
  
XElement author =   
    books  
    .Root  
    .Element("Book")  
    .Element("Author");  
  
// LINQ to XML query  
XAttribute att1 =  
    author  
    .Parent  
    .Attribute("id");  
  
// XPath expression  
XAttribute att2 = ((IEnumerable)author.XPathEvaluate("../@id")).Cast<XAttribute>().First();  
  
if (att1 == att2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(att1);  
```  
  
 <span data-ttu-id="7ec06-109">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="7ec06-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ec06-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="7ec06-110">See Also</span></span>  
 [<span data-ttu-id="7ec06-111">XPath ユーザー向けの LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="7ec06-111">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)

