---
title: "方法: 位置に基づいて子要素を検索する (XPath-LINQ to XML) (C#)"
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
ms.assetid: e35bb269-ec86-4c96-8321-12491a0eb2c3
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 247cb8f2be3a005413045198443b132b25241775
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-c"></a>方法: 位置に基づいて子要素を検索する (XPath-LINQ to XML) (C#)
要素をその位置に基づいて検索しなければならない場合があります。 2 番目の要素を検索したり、3 番目から 5 番目の要素を検索したりすることがあります。  
  
 XPath 式を次に示します。  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 レイジー方式でこの [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] クエリを記述する方法は 2 つあります。 1 つは <xref:System.Linq.Enumerable.Skip%2A> 演算子と <xref:System.Linq.Enumerable.Take%2A> 演算子を使用する方法で、もう 1 つはインデックスを受け取る <xref:System.Linq.Enumerable.Where%2A> オーバーロードを使用する方法です。 <xref:System.Linq.Enumerable.Where%2A> オーバーロードを使用する場合は、2 つの引数を受け取るラムダ式を使用します。 次の例では、位置に基づいて選択する両方のメソッドを示します。  
  
## <a name="example"></a>例  
 この例では、2 番目から 4 番目の `Test` 要素を検索します。 結果は要素のコレクションです。  
  
 この例では、「[サンプル XML ファイル: テスト構成 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md)」の XML ドキュメントを使用します。  
  
```csharp  
XElement testCfg = XElement.Load("TestConfig.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    testCfg  
    .Elements("Test")  
    .Skip(1)  
    .Take(3);  
  
// LINQ to XML query  
IEnumerable<XElement> list2 =  
    testCfg  
    .Elements("Test")  
    .Where((el, idx) => idx >= 1 && idx <= 3);  
  
// XPath expression  
IEnumerable<XElement> list3 =  
  testCfg.XPathSelectElements("Test[position() >= 2 and position() <= 4]");  
  
if (list1.Count() == list2.Count() &&  
    list1.Count() == list3.Count() &&  
    list1.Intersect(list2).Count() == list1.Count() &&  
    list1.Intersect(list3).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
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
 [XPath ユーザー向けの LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)

