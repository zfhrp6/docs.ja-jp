---
title: "方法: (XPATH-LINQ to XML) の位置に基づいて子要素を検索する (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 6831e1db-5e97-444f-a7a1-d0a87104b005
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 5e42a12605eecc6633da45342ee0111dcc4b0cc1
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017


---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="33f94-102">方法: (XPATH-LINQ to XML) の位置に基づいて子要素を検索する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33f94-102">How to: Find Child Elements Based on Position (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="33f94-103">要素をその位置に基づいて検索しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="33f94-103">Sometimes you want to find elements based on their position.</span></span> <span data-ttu-id="33f94-104">2 番目の要素を検索したり、3 番目から&5; 番目の要素を検索したりすることがあります。</span><span class="sxs-lookup"><span data-stu-id="33f94-104">You might want to find the second element, or you might want to find the third through the fifth element.</span></span>  
  
 <span data-ttu-id="33f94-105">XPath 式を次に示します。</span><span class="sxs-lookup"><span data-stu-id="33f94-105">The XPath expression is:</span></span>  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 <span data-ttu-id="33f94-106">レイジー方式でこの [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] クエリを記述する方法は&2; つあります。</span><span class="sxs-lookup"><span data-stu-id="33f94-106">There are two approaches to writing this [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] query in a lazy way.</span></span> <span data-ttu-id="33f94-107">使用することができます、<xref:System.Linq.Enumerable.Skip%2A>と<xref:System.Linq.Enumerable.Take%2A>演算子、または使用して、 <xref:System.Linq.Enumerable.Where%2A>、インデックスを受け取るオーバー ロード</xref:System.Linq.Enumerable.Where%2A></xref:System.Linq.Enumerable.Take%2A></xref:System.Linq.Enumerable.Skip%2A>。</span><span class="sxs-lookup"><span data-stu-id="33f94-107">You can use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> operators, or you can use the <xref:System.Linq.Enumerable.Where%2A> overload that takes an index.</span></span> <span data-ttu-id="33f94-108">使用すると、<xref:System.Linq.Enumerable.Where%2A>を&2; つの引数を受け取るラムダ式を使用するオーバー ロード、.</xref:System.Linq.Enumerable.Where%2A></span><span class="sxs-lookup"><span data-stu-id="33f94-108">When you use the <xref:System.Linq.Enumerable.Where%2A> overload, you use a lambda expression that takes two arguments.</span></span> <span data-ttu-id="33f94-109">次の例では、位置に基づいて選択する両方のメソッドを示します。</span><span class="sxs-lookup"><span data-stu-id="33f94-109">The following example shows both methods of selecting based on position.</span></span>  
  
## <a name="example"></a><span data-ttu-id="33f94-110">例</span><span class="sxs-lookup"><span data-stu-id="33f94-110">Example</span></span>  
 <span data-ttu-id="33f94-111">この例では、2 番目から&4; 番目の `Test` 要素を検索します。</span><span class="sxs-lookup"><span data-stu-id="33f94-111">This example finds the second through the fourth `Test` element.</span></span> <span data-ttu-id="33f94-112">結果は要素のコレクションです。</span><span class="sxs-lookup"><span data-stu-id="33f94-112">The result is a collection of elements.</span></span>  
  
 <span data-ttu-id="33f94-113">この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: テスト構成 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="33f94-113">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```vb  
Dim testCfg As XElement = XElement.Load("TestConfig.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    testCfg.Elements("Test").Skip(1).Take(3)  
  
'LINQ to XML query  
Dim list2 As IEnumerable(Of XElement) = _  
    testCfg.Elements("Test"). _  
    Where(Function(ByVal el, ByVal idx) idx >= 1 And idx <= 3)  
  
' XPath expression  
Dim list3 As IEnumerable(Of XElement) = _  
    testCfg.XPathSelectElements("Test[position() >= 2 and position() <= 4]")  
  
If list1.Count() = list2.Count() And _  
       list1.Count() = list3.Count() And _  
       list1.Intersect(list2).Count() = list1.Count() And _  
       list1.Intersect(list3).Count() = list1.Count() Then  
  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="33f94-114">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="33f94-114">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Test TestId="0002" TestType="CMD">  
  <Name>Find succeeding characters</Name>  
  <CommandLine>Examp2.EXE</CommandLine>  
  <Input>abc</Input>  
  <Output>def</Output>  
</Test>  
<Test TestId="0003" TestType="GUI">  
  <Name>Convert multiple numbers to strings</Name>  
  <CommandLine>Examp2.EXE /Verbose</CommandLine>  
  <Input>123</Input>  
  <Output>One Two Three</Output>  
</Test>  
<Test TestId="0004" TestType="GUI">  
  <Name>Find correlated key</Name>  
  <CommandLine>Examp3.EXE</CommandLine>  
  <Input>a1</Input>  
  <Output>b1</Output>  
</Test>  
```  
  
## <a name="see-also"></a><span data-ttu-id="33f94-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="33f94-115">See Also</span></span>  
 [<span data-ttu-id="33f94-116">LINQ to XML の XPath ユーザー (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33f94-116">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)

