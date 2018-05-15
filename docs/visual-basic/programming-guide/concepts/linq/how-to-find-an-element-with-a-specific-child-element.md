---
title: '方法: 特定の子要素 (Visual Basic) を持つ要素を検索'
ms.date: 07/20/2015
ms.assetid: b0d0a463-6a85-46c3-8453-ad25b0ecf93c
ms.openlocfilehash: 9ebc7fd826e2245cea661b2441fa9989b0aee8b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-find-an-element-with-a-specific-child-element-visual-basic"></a><span data-ttu-id="68561-102">方法: 特定の子要素 (Visual Basic) を持つ要素を検索</span><span class="sxs-lookup"><span data-stu-id="68561-102">How to: Find an Element with a Specific Child Element (Visual Basic)</span></span>
<span data-ttu-id="68561-103">このトピックでは、特定の値を含む子要素を持つ特定の要素を検索する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="68561-103">This topic shows how to find a particular element that has a child element with a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68561-104">例</span><span class="sxs-lookup"><span data-stu-id="68561-104">Example</span></span>  
 <span data-ttu-id="68561-105">この例では、"Examp2.EXE" の値を含む `Test` 子要素を持つ `CommandLine` 要素を検索します。</span><span class="sxs-lookup"><span data-stu-id="68561-105">The example finds the `Test` element that has a `CommandLine` child element with the value of "Examp2.EXE".</span></span>  
  
 <span data-ttu-id="68561-106">この例では、「[サンプル XML ファイル: テスト構成 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="68561-106">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="68561-107">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="68561-107">This code produces the following output:</span></span>  
  
```  
0002  
0006  
```  
  
 <span data-ttu-id="68561-108">この例では注意してください、 [XML 子軸プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)、 [XML 属性軸プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)、および[XML Value プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)です。</span><span class="sxs-lookup"><span data-stu-id="68561-108">Note that this example uses the [XML Child axis property](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md), the [XML Attribute axis property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md), and the [XML Value property](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="68561-109">例</span><span class="sxs-lookup"><span data-stu-id="68561-109">Example</span></span>  
 <span data-ttu-id="68561-110">次の例は名前空間に含まれている XML 用のクエリです。これらのクエリは上の例と同じ機能を表しています。</span><span class="sxs-lookup"><span data-stu-id="68561-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="68561-111">詳細については、次を参照してください。 [XML 名前空間 (Visual Basic) の操作](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)です。</span><span class="sxs-lookup"><span data-stu-id="68561-111">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="68561-112">この例では、「[サンプル XML ファイル : 名前空間内のテスト構成](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-in-a-namespace.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="68561-112">This example uses the following XML document: [Sample XML File: Test Configuration in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="68561-113">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="68561-113">This code produces the following output:</span></span>  
  
```  
0002  
0006  
```  
  
## <a name="see-also"></a><span data-ttu-id="68561-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="68561-114">See Also</span></span>  
 <xref:System.Xml.Linq.XElement.Attribute%2A>  
 <xref:System.Xml.Linq.XContainer.Elements%2A>  
 [<span data-ttu-id="68561-115">基本的なクエリ (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68561-115">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)  
 [<span data-ttu-id="68561-116">標準クエリ演算子の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68561-116">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="68561-117">射影操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68561-117">Projection Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
