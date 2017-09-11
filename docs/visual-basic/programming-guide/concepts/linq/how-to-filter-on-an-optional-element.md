---
title: "方法: 省略可能な要素 (Visual Basic) をフィルター処理 |Microsoft ドキュメント"
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
ms.assetid: a74b76ad-6889-4185-a189-d6ef2c63841e
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 7534ccc197dd4a8f2603e12f13d69d2fec30df80
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017


---
# <a name="how-to-filter-on-an-optional-element-visual-basic"></a><span data-ttu-id="efb96-102">方法: 省略可能な要素 (Visual Basic) をフィルター処理</span><span class="sxs-lookup"><span data-stu-id="efb96-102">How to: Filter on an Optional Element (Visual Basic)</span></span>
<span data-ttu-id="efb96-103">要素に対するフィルター処理が、その要素が XML ドキュメント内に存在しているかどうか明確でない場合でも必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="efb96-103">Sometimes you want to filter for an element even though you are not sure it exists in your XML document.</span></span> <span data-ttu-id="efb96-104">特定の要素が子要素を持たない場合、その要素に対するフィルター処理によって null 参照例外が発生しないように検索を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="efb96-104">The search should be executed so that if the particular element does not have the child element, you do not trigger a null reference exception by filtering for it.</span></span> <span data-ttu-id="efb96-105">次の例では、`Child5` 要素には `Type` 子要素はありませんが、クエリは正常に実行されます。</span><span class="sxs-lookup"><span data-stu-id="efb96-105">In the following example, the `Child5` element does not have a `Type` child element, but the query still executes correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="efb96-106">例</span><span class="sxs-lookup"><span data-stu-id="efb96-106">Example</span></span>  
 <span data-ttu-id="efb96-107">この例では、<xref:System.Xml.Linq.Extensions.Elements%2A>拡張メソッド</xref:System.Xml.Linq.Extensions.Elements%2A>。</span><span class="sxs-lookup"><span data-stu-id="efb96-107">This example uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method.</span></span>  
  
```vb  
Dim root As XElement = _   
    <Root>  
        <Child1>  
            <Text>Child One Text</Text>  
            <Type Value="Yes"/>  
        </Child1>  
        <Child2>  
            <Text>Child Two Text</Text>  
            <Type Value="Yes"/>  
        </Child2>  
        <Child3>  
            <Text>Child Three Text</Text>  
            <Type Value="No"/>  
        </Child3>  
        <Child4>  
            <Text>Child Four Text</Text>  
            <Type Value="Yes"/>  
        </Child4>  
        <Child5>  
            <Text>Child Five Text</Text>  
        </Child5>  
    </Root>  
Dim cList As IEnumerable(Of String) = _  
    From typeElement In root.Elements().<Type> _  
    Where typeElement.@Value = "Yes" _  
    Select typeElement.Parent.<Text>.Value  
Dim str As String  
For Each str In cList  
    Console.WriteLine(str)  
Next  
```  
  
 <span data-ttu-id="efb96-108">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="efb96-108">This code produces the following output:</span></span>  
  
```  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="example"></a><span data-ttu-id="efb96-109">例</span><span class="sxs-lookup"><span data-stu-id="efb96-109">Example</span></span>  
 <span data-ttu-id="efb96-110">次の例は名前空間に含まれている XML 用のクエリです。これらのクエリは上の例と同じ機能を表しています。</span><span class="sxs-lookup"><span data-stu-id="efb96-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="efb96-111">詳細については、次を参照してください。 [XML 名前空間 (Visual Basic) の使用](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)します。</span><span class="sxs-lookup"><span data-stu-id="efb96-111">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child1>  
                    <Text>Child One Text</Text>  
                    <Type Value="Yes"/>  
                </Child1>  
                <Child2>  
                    <Text>Child Two Text</Text>  
                    <Type Value="Yes"/>  
                </Child2>  
                <Child3>  
                    <Text>Child Three Text</Text>  
                    <Type Value="No"/>  
                </Child3>  
                <Child4>  
                    <Text>Child Four Text</Text>  
                    <Type Value="Yes"/>  
                </Child4>  
                <Child5>  
                    <Text>Child Five Text</Text>  
                </Child5>  
            </Root>  
        Dim cList As IEnumerable(Of String) = _  
            From typeElement In root.Elements().<Type> _  
            Where typeElement.@Value = "Yes" _  
            Select typeElement.Parent.<Text>.Value  
        Dim str As String  
        For Each str In cList  
            Console.WriteLine(str)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="efb96-112">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="efb96-112">This code produces the following output:</span></span>  
  
```  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="see-also"></a><span data-ttu-id="efb96-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="efb96-113">See Also</span></span>  
 <span data-ttu-id="efb96-114"><xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="efb96-114"><xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName></span></span>   
 <span data-ttu-id="efb96-115"><xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="efb96-115"><xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName></span></span>   
 <span data-ttu-id="efb96-116"><xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName></xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="efb96-116"><xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName></span></span>   
<span data-ttu-id="efb96-117"> [基本的なクエリ (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md) </span><span class="sxs-lookup"><span data-stu-id="efb96-117"> [Basic Queries (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md) </span></span>  
<span data-ttu-id="efb96-118"> [XML 子軸プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md) </span><span class="sxs-lookup"><span data-stu-id="efb96-118"> [XML Child Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md) </span></span>  
<span data-ttu-id="efb96-119"> [XML 属性軸プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md) </span><span class="sxs-lookup"><span data-stu-id="efb96-119"> [XML Attribute Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md) </span></span>  
<span data-ttu-id="efb96-120"> [XML Value プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md) </span><span class="sxs-lookup"><span data-stu-id="efb96-120"> [XML Value Property](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md) </span></span>  
<span data-ttu-id="efb96-121"> [標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="efb96-121"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="efb96-122"> [射影操作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)</span><span class="sxs-lookup"><span data-stu-id="efb96-122"> [Projection Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)</span></span>
