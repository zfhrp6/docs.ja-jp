---
title: "方法: 親 (XPATH-LINQ to XML) の属性を検索 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d2572fd-27d4-426c-b079-16854cb9ec7d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4da7888ab838dacbdda097f24580745692d407fd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="8e5e2-102">方法: 親 (XPATH-LINQ to XML) の属性を検索 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e5e2-102">How to: Find an Attribute of the Parent (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="8e5e2-103">このトピックでは、親要素に移動してその属性を検索する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8e5e2-103">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>  
  
 <span data-ttu-id="8e5e2-104">XPath 式を次に示します。</span><span class="sxs-lookup"><span data-stu-id="8e5e2-104">The XPath expression is:</span></span>  
  
 `../@id`  
  
## <a name="example"></a><span data-ttu-id="8e5e2-105">例</span><span class="sxs-lookup"><span data-stu-id="8e5e2-105">Example</span></span>  
 <span data-ttu-id="8e5e2-106">この例では、まず `Author` 要素を検索します。</span><span class="sxs-lookup"><span data-stu-id="8e5e2-106">This example first finds an `Author` element.</span></span> <span data-ttu-id="8e5e2-107">次に、親要素の `id` 属性を検索します。</span><span class="sxs-lookup"><span data-stu-id="8e5e2-107">It then finds the `id` attribute of the parent element.</span></span>  
  
 <span data-ttu-id="8e5e2-108">この例では、「[サンプル XML ファイル: 書籍 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="8e5e2-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```vb  
Dim books As XDocument = XDocument.Load("Books.xml")  
Dim author As XElement = books.Root.<Book>.<Author>.FirstOrDefault()  
  
' LINQ to XML query  
Dim att1 As XAttribute = author.Parent.Attribute("id")  
  
' XPath expression  
Dim att2 As XAttribute = DirectCast(author.XPathEvaluate("../@id"),  _  
    IEnumerable).Cast(Of XAttribute)().First()  
  
If att1 Is att2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(att1)  
```  
  
 <span data-ttu-id="8e5e2-109">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="8e5e2-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
```  
  
## <a name="see-also"></a><span data-ttu-id="8e5e2-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="8e5e2-110">See Also</span></span>  
 [<span data-ttu-id="8e5e2-111">LINQ to XML を XPath ユーザー (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e5e2-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
