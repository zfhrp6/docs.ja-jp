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
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7c1ef9db560de02efa20dbe88ff0e73ffd9e7fff
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-visual-basic"></a>方法: (XPATH-LINQ to XML) の位置に基づいて子要素を検索する (Visual Basic)
要素をその位置に基づいて検索しなければならない場合があります。 2 番目の要素を検索したり、3 番目から&5; 番目の要素を検索したりすることがあります。  
  
 XPath 式を次に示します。  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 レイジー方式でこの [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] クエリを記述する方法は&2; つあります。 使用することができます、<xref:System.Linq.Enumerable.Skip%2A>と<xref:System.Linq.Enumerable.Take%2A>演算子、または使用して、 <xref:System.Linq.Enumerable.Where%2A>、インデックスを受け取るオーバー ロード</xref:System.Linq.Enumerable.Where%2A></xref:System.Linq.Enumerable.Take%2A></xref:System.Linq.Enumerable.Skip%2A>。 使用すると、<xref:System.Linq.Enumerable.Where%2A>を&2; つの引数を受け取るラムダ式を使用するオーバー ロード、.</xref:System.Linq.Enumerable.Where%2A> 次の例では、位置に基づいて選択する両方のメソッドを示します。  
  
## <a name="example"></a>例  
 この例では、2 番目から&4; 番目の `Test` 要素を検索します。 結果は要素のコレクションです。  
  
 この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: テスト構成 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md)します。  
  
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
  
 この例を実行すると、次の出力が生成されます。  
  
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
  
## <a name="see-also"></a>関連項目  
 [LINQ to XML の XPath ユーザー (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)

