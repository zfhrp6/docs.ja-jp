---
title: "方法: 要素 (Visual Basic) の浅い値を取得 |Microsoft ドキュメント"
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
ms.assetid: 730a6670-fb8c-41fc-8a1b-eb97a837e432
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: a32f50ce8a92fa22d9627a1510a4b3ec1087364e
ms.openlocfilehash: c313f1f13e2dc3cc42d182b3c9542a46f2f4d831
ms.contentlocale: ja-jp
ms.lasthandoff: 06/01/2017


---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-visual-basic"></a><span data-ttu-id="9a54e-102">方法: 要素 (Visual Basic) の浅い値を取得</span><span class="sxs-lookup"><span data-stu-id="9a54e-102">How to: Retrieve the Shallow Value of an Element (Visual Basic)</span></span>
<span data-ttu-id="9a54e-103">このトピックでは、要素の浅い値を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9a54e-103">This topic shows how to get the shallow value of an element.</span></span> <span data-ttu-id="9a54e-104">浅い値は、特定の要素のみの値のことです。これに対し、深い値とは、すべての子孫要素の値が単一の文字列として連結された値をいいます。</span><span class="sxs-lookup"><span data-stu-id="9a54e-104">The shallow value is the value of the specific element only, as opposed to the deep value, which includes the values of all descendent elements concatenated into a single string.</span></span>  
  
 <span data-ttu-id="9a54e-105">キャストを使用して、要素の値を取得する場合、または<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=fullName>プロパティには、深い値を取得します</xref:System.Xml.Linq.XElement.Value%2A?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="9a54e-105">When you retrieve an element value by using either casting or the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=fullName> property, you retrieve the deep value.</span></span> <span data-ttu-id="9a54e-106">浅い値を取得するには、次の例のように `ShallowValue` 拡張メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="9a54e-106">To retrieve the shallow value, you can use the `ShallowValue` extension method, as shown in the follwing example.</span></span> <span data-ttu-id="9a54e-107">浅い値を取得することは、要素をその内容に基づいて選択する必要がある場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="9a54e-107">Retrieving the shallow value is useful when you want to select elements based on their content.</span></span>  
  
 <span data-ttu-id="9a54e-108">次の例では、要素の浅い値を取得する拡張メソッドを宣言しています。</span><span class="sxs-lookup"><span data-stu-id="9a54e-108">The following example declares an extension method that retrieves the shallow value of an element.</span></span> <span data-ttu-id="9a54e-109">次に、この拡張メソッドをクエリの中で使用して、計算値を含んだすべての要素をリストします。</span><span class="sxs-lookup"><span data-stu-id="9a54e-109">It then uses the extension method in a query to list all elements that contain a calculated value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a54e-110">例</span><span class="sxs-lookup"><span data-stu-id="9a54e-110">Example</span></span>  
 <span data-ttu-id="9a54e-111">次のテキスト ファイル (Report.xml) は、この例のソースです。</span><span class="sxs-lookup"><span data-stu-id="9a54e-111">The following text file, Report.xml, is the source for this example.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Report>  
  <Section>  
    <Heading>  
      <Column Name="CustomerId">=Customer.CustomerId.Heading</Column>  
      <Column Name="Name">=Customer.Name.Heading</Column>  
    </Heading>  
    <Detail>  
      <Column Name="CustomerId">=Customer.CustomerId</Column>  
      <Column Name="Name">=Customer.Name</Column>  
    </Detail>  
  </Section>  
</Report>  
```  
  
```vb  
Module Module1  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function ShallowValue(ByVal xe As XElement)  
        Return xe _  
               .Nodes() _  
               .OfType(Of XText)() _  
               .Aggregate(New StringBuilder(), _  
                              Function(s, c) s.Append(c), _  
                              Function(s) s.ToString())  
    End Function  
  
    Sub Main()  
        Dim root As XElement = XElement.Load("Report.xml")  
  
        Dim query As IEnumerable(Of XElement) = _  
            From el In root.Descendants() _  
            Where (el.ShallowValue().StartsWith("=")) _  
            Select el  
  
        For Each q As XElement In query  
            Console.WriteLine("{0}{1}{2}", _  
                q.Name.ToString().PadRight(8), _  
                q.Attribute("Name").ToString().PadRight(20), _  
                q.ShallowValue())  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="9a54e-112">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="9a54e-112">This example produces the following output:</span></span>  
  
```  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a><span data-ttu-id="9a54e-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a54e-113">See Also</span></span>  
 [<span data-ttu-id="9a54e-114">LINQ to XML 軸 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a54e-114">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
