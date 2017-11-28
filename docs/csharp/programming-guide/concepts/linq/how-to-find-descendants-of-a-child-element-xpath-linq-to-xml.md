---
title: "方法: 子要素の子孫を検索する (XPath-LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 505b7512-bb8b-4f85-abbf-491f039c961e
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 873cfe6a725a932ac4616e7ccf0ea11e3f6479f5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-descendants-of-a-child-element-xpath-linq-to-xml-c"></a><span data-ttu-id="ccb41-102">方法: 子要素の子孫を検索する (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ccb41-102">How to: Find Descendants of a Child Element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="ccb41-103">このトピックでは、特定の名前を持つ子要素の子孫要素を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ccb41-103">This topic shows how to get the descendant elements of a child element with a particular name.</span></span>  
  
 <span data-ttu-id="ccb41-104">XPath 式を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ccb41-104">The XPath expression is:</span></span>  
  
 `./Paragraph//Text/text()`  
  
## <a name="example"></a><span data-ttu-id="ccb41-105">例</span><span class="sxs-lookup"><span data-stu-id="ccb41-105">Example</span></span>  
 <span data-ttu-id="ccb41-106">この例では、ワード プロセッシング ドキュメントの XML 表現からテキストを抽出する際に発生する問題をシミュレートします。</span><span class="sxs-lookup"><span data-stu-id="ccb41-106">This example simulates the problems of extracting text from an XML representation of a word processing document.</span></span> <span data-ttu-id="ccb41-107">最初にすべての `Paragraph` 要素を選択し、次に各 `Text` 要素の `Paragraph` 子孫要素をすべて選択します。</span><span class="sxs-lookup"><span data-stu-id="ccb41-107">It first selects all `Paragraph` elements, and then it selects all `Text` descendant elements of each `Paragraph` element.</span></span> <span data-ttu-id="ccb41-108">`Text` 要素の `Comment` 子孫要素は選択しません。</span><span class="sxs-lookup"><span data-stu-id="ccb41-108">This doesn't select the descendant `Text` elements of the `Comment` element.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root>  
  <Paragraph>  
    <Text>This is the start of</Text>  
  </Paragraph>  
  <Comment>  
    <Text>This comment is not part of the paragraph text.</Text>  
  </Comment>  
  <Paragraph>  
    <Annotation Emphasis='true'>  
      <Text> a sentence.</Text>  
    </Annotation>  
  </Paragraph>  
  <Paragraph>  
    <Text>  This is a second sentence.</Text>  
  </Paragraph>  
</Root>");  
  
// LINQ to XML query  
string str1 =  
    root  
    .Elements("Paragraph")  
    .Descendants("Text")  
    .Select(s => s.Value)  
    .Aggregate(  
        new StringBuilder(),  
        (s, i) => s.Append(i),  
        s => s.ToString()  
    );  
  
// XPath expression  
string str2 =  
    ((IEnumerable)root.XPathEvaluate("./Paragraph//Text/text()"))  
    .Cast<XText>()  
    .Select(s => s.Value)  
    .Aggregate(  
        new StringBuilder(),  
        (s, i) => s.Append(i),  
        s => s.ToString()  
    );  
  
if (str1 == str2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(str2);  
```  
  
 <span data-ttu-id="ccb41-109">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ccb41-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
This is the start of a sentence.  This is a second sentence.  
```  
  
## <a name="see-also"></a><span data-ttu-id="ccb41-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="ccb41-110">See Also</span></span>  
 [<span data-ttu-id="ccb41-111">XPath ユーザー向けの LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="ccb41-111">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
