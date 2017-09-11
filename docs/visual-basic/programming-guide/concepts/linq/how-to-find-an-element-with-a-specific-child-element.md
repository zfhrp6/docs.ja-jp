---
title: "方法: 特定の子要素 (Visual Basic) を持つ要素を検索 |Microsoft ドキュメント"
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
ms.assetid: b0d0a463-6a85-46c3-8453-ad25b0ecf93c
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4adb17ec4bbbe9caf2220a2c9b5bbe207f095350
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017


---
# <a name="how-to-find-an-element-with-a-specific-child-element-visual-basic"></a><span data-ttu-id="6d486-102">方法: 特定の子要素 (Visual Basic) を持つ要素を検索</span><span class="sxs-lookup"><span data-stu-id="6d486-102">How to: Find an Element with a Specific Child Element (Visual Basic)</span></span>
<span data-ttu-id="6d486-103">このトピックでは、特定の値を含む子要素を持つ特定の要素を検索する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6d486-103">This topic shows how to find a particular element that has a child element with a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d486-104">例</span><span class="sxs-lookup"><span data-stu-id="6d486-104">Example</span></span>  
 <span data-ttu-id="6d486-105">この例では、"Examp2.EXE" の値を含む `Test` 子要素を持つ `CommandLine` 要素を検索します。</span><span class="sxs-lookup"><span data-stu-id="6d486-105">The example finds the `Test` element that has a `CommandLine` child element with the value of "Examp2.EXE".</span></span>  
  
 <span data-ttu-id="6d486-106">この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: テスト構成 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="6d486-106">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("TestConfig.xml")  
Dim tests As IEnumerable(Of XElement) = _  
    From el In root.<Test> _  
    Where el.<CommandLine>.Value = "Examp2.EXE" _  
    Select el  
For Each el as XElement In tests  
    Console.WriteLine(el.@TestId)  
Next  
```  
  
 <span data-ttu-id="6d486-107">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="6d486-107">This code produces the following output:</span></span>  
  
```  
0002  
0006  
```  
  
 <span data-ttu-id="6d486-108">この例ではメモ、 [XML 子軸プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)、 [XML 属性軸プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)、および[XML 値プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)します。</span><span class="sxs-lookup"><span data-stu-id="6d486-108">Note that this example uses the [XML Child axis property](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md), the [XML Attribute axis property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md), and the [XML Value property](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d486-109">例</span><span class="sxs-lookup"><span data-stu-id="6d486-109">Example</span></span>  
 <span data-ttu-id="6d486-110">次の例は名前空間に含まれている XML 用のクエリです。これらのクエリは上の例と同じ機能を表しています。</span><span class="sxs-lookup"><span data-stu-id="6d486-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="6d486-111">詳細については、次を参照してください。 [XML 名前空間 (Visual Basic) の使用](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)します。</span><span class="sxs-lookup"><span data-stu-id="6d486-111">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="6d486-112">この例は、次の XML ドキュメントを使用して:[サンプル XML ファイル: テスト構成、Namespace で](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-in-a-namespace.md)します。</span><span class="sxs-lookup"><span data-stu-id="6d486-112">This example uses the following XML document: [Sample XML File: Test Configuration in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("TestConfigInNamespace.xml")  
        Dim tests As IEnumerable(Of XElement) = _  
            From el In root.<Test> _  
            Where el.<CommandLine>.Value = "Examp2.EXE" _  
            Select el  
        For Each el As XElement In tests  
            Console.WriteLine(el.@TestId)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="6d486-113">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="6d486-113">This code produces the following output:</span></span>  
  
```  
0002  
0006  
```  
  
## <a name="see-also"></a><span data-ttu-id="6d486-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="6d486-114">See Also</span></span>  
 <span data-ttu-id="6d486-115"><xref:System.Xml.Linq.XElement.Attribute%2A></xref:System.Xml.Linq.XElement.Attribute%2A></span><span class="sxs-lookup"><span data-stu-id="6d486-115"><xref:System.Xml.Linq.XElement.Attribute%2A></span></span>   
 <span data-ttu-id="6d486-116"><xref:System.Xml.Linq.XContainer.Elements%2A></xref:System.Xml.Linq.XContainer.Elements%2A></span><span class="sxs-lookup"><span data-stu-id="6d486-116"><xref:System.Xml.Linq.XContainer.Elements%2A></span></span>   
<span data-ttu-id="6d486-117"> [基本的なクエリ (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md) </span><span class="sxs-lookup"><span data-stu-id="6d486-117"> [Basic Queries (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md) </span></span>  
<span data-ttu-id="6d486-118"> [標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="6d486-118"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="6d486-119"> [射影操作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)</span><span class="sxs-lookup"><span data-stu-id="6d486-119"> [Projection Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)</span></span>
