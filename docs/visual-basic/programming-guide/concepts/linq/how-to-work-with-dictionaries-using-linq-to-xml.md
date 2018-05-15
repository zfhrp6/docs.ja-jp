---
title: '方法: LINQ to XML (Visual Basic) を使用してディクショナリを使用'
ms.date: 07/20/2015
ms.assetid: 6cb3f969-1986-414a-b850-87418712edea
ms.openlocfilehash: b6e41f61358563472f49b22df389df00e721503e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-visual-basic"></a><span data-ttu-id="c9b21-102">方法: LINQ to XML (Visual Basic) を使用してディクショナリを使用</span><span class="sxs-lookup"><span data-stu-id="c9b21-102">How to: Work with Dictionaries Using LINQ to XML (Visual Basic)</span></span>
<span data-ttu-id="c9b21-103">さまざまなデータ構造と XML を相互に変換すると便利な場合がよくあります。</span><span class="sxs-lookup"><span data-stu-id="c9b21-103">It is often convenient to convert varieties of data structures to XML, and XML back to other data structures.</span></span> <span data-ttu-id="c9b21-104">このトピックでは、<xref:System.Collections.Generic.Dictionary%602> と XML を相互に変換することによる、一般的な相互変換の実装について説明します。</span><span class="sxs-lookup"><span data-stu-id="c9b21-104">This topic shows a specific implementation of this general approach by converting a <xref:System.Collections.Generic.Dictionary%602> to XML and back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9b21-105">例</span><span class="sxs-lookup"><span data-stu-id="c9b21-105">Example</span></span>  
 <span data-ttu-id="c9b21-106">この例では、埋め込み式の中で XML リテラルと、クエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="c9b21-106">This example uses XML literals and a query in an embedded expression.</span></span> <span data-ttu-id="c9b21-107">新しいクエリ プロジェクト<xref:System.Xml.Linq.XElement>するオブジェクトの新しいコンテンツになる、 `Root` <xref:System.Xml.Linq.XElement>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="c9b21-107">The query projects new <xref:System.Xml.Linq.XElement> objects, which then become the new content for the `Root` <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```vb  
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)()  
dict.Add("Child1", "Value1")  
dict.Add("Child2", "Value2")  
dict.Add("Child3", "Value3")  
dict.Add("Child4", "Value4")  
Dim root As XElement = _  
    <Root>  
        <%= From keyValue In dict _  
            Select New XElement(keyValue.Key, keyValue.Value) %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="c9b21-108">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="c9b21-108">This code produces the following output:</span></span>  
  
```xml  
          <Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="c9b21-109">例</span><span class="sxs-lookup"><span data-stu-id="c9b21-109">Example</span></span>  
 <span data-ttu-id="c9b21-110">次のコードは、XML からディクショナリを作成します。</span><span class="sxs-lookup"><span data-stu-id="c9b21-110">The following code creates a dictionary from XML.</span></span>  
  
```vb  
Dim root As XElement = _  
        <Root>  
            <Child1>Value1</Child1>  
            <Child2>Value2</Child2>  
            <Child3>Value3</Child3>  
            <Child4>Value4</Child4>  
        </Root>  
  
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)  
For Each el As XElement In root.Elements  
    dict.Add(el.Name.LocalName, el.Value)  
Next  
For Each str As String In dict.Keys  
    Console.WriteLine("{0}:{1}", str, dict(str))  
Next  
```  
  
 <span data-ttu-id="c9b21-111">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="c9b21-111">This code produces the following output:</span></span>  
  
```  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
  
## <a name="see-also"></a><span data-ttu-id="c9b21-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="c9b21-112">See Also</span></span>  
 [<span data-ttu-id="c9b21-113">射影と変換 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9b21-113">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
