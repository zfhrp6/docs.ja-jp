---
title: '方法: 要素 (LINQ to XML) の値の取得 (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 76b9b2a5-b3ba-49da-ba74-82100e1bd21c
ms.openlocfilehash: ff2a1712a79bdedd74fe51391f01dd900ae585e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-visual-basic"></a><span data-ttu-id="cecb7-102">方法: 要素 (LINQ to XML) の値の取得 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cecb7-102">How to: Retrieve the Value of an Element (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="cecb7-103">このトピックでは、要素の値を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cecb7-103">This topic shows how to get the value of elements.</span></span> <span data-ttu-id="cecb7-104">これには主に 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="cecb7-104">There are two main ways to do this.</span></span> <span data-ttu-id="cecb7-105">1 つは <xref:System.Xml.Linq.XElement> または <xref:System.Xml.Linq.XAttribute> を目的の型にキャストする方法です。</span><span class="sxs-lookup"><span data-stu-id="cecb7-105">One way is to cast an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XAttribute> to the desired type.</span></span> <span data-ttu-id="cecb7-106">その後、明示的な変換演算子によって、要素または属性のコンテンツが指定した型に変換され、変数に代入されます。</span><span class="sxs-lookup"><span data-stu-id="cecb7-106">The explicit conversion operator then converts the contents of the element or attribute to the specified type and assigns it to your variable.</span></span> <span data-ttu-id="cecb7-107">もう 1 つは、<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> プロパティまたは <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> プロパティを使用する方法です。</span><span class="sxs-lookup"><span data-stu-id="cecb7-107">Alternatively, you can use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property or the <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="cecb7-108">Visual Basic では、<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> プロパティを使用する方法が最適です。</span><span class="sxs-lookup"><span data-stu-id="cecb7-108">With Visual Basic, the best approach is to use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cecb7-109">例</span><span class="sxs-lookup"><span data-stu-id="cecb7-109">Example</span></span>  
 <span data-ttu-id="cecb7-110">要素の値を取得するには、<xref:System.Xml.Linq.XElement> オブジェクトを目的の型にキャストします。</span><span class="sxs-lookup"><span data-stu-id="cecb7-110">To retrieve the value of an element, you just cast the <xref:System.Xml.Linq.XElement> object to your desired type.</span></span> <span data-ttu-id="cecb7-111">次に示すように、要素はいつでも文字列にキャストできます。</span><span class="sxs-lookup"><span data-stu-id="cecb7-111">You can always cast an element to a string, as follows:</span></span>  
  
```vb  
Dim e As XElement = <StringElement>abcde</StringElement>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & e.Value)  
```  
  
 <span data-ttu-id="cecb7-112">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="cecb7-112">This example produces the following output:</span></span>  
  
```xml  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="cecb7-113">例</span><span class="sxs-lookup"><span data-stu-id="cecb7-113">Example</span></span>  
 <span data-ttu-id="cecb7-114">文字列以外の型に要素をキャストすることもできます。</span><span class="sxs-lookup"><span data-stu-id="cecb7-114">You can also cast elements to types other than string.</span></span> <span data-ttu-id="cecb7-115">たとえば、次のコードに示すように、整数を含んだ要素を `int` にキャストできます。</span><span class="sxs-lookup"><span data-stu-id="cecb7-115">For example, if you have an element that contains an integer, you can cast it to `int`, as shown in the following code:</span></span>  
  
```vb  
Dim e As XElement = <Age>44</Age>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & CInt(e))  
```  
  
 <span data-ttu-id="cecb7-116">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="cecb7-116">This example produces the following output:</span></span>  
  
```xml  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="cecb7-117"> では、`string`、`bool`、`bool?`、`int`、`int?`、`uint`、`uint?`、`long`、`long?`、`ulong`、`ulong?`、`float`、`float?`、`double`、`double?`、`decimal`、`decimal?`、`DateTime`、`DateTime?`、`TimeSpan`、`TimeSpan?`、`GUID`、および `GUID?` というデータ型について明示的なキャスト演算子を用意しています。</span><span class="sxs-lookup"><span data-stu-id="cecb7-117"> provides explicit cast operators for the following data types: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
 <span data-ttu-id="cecb7-118">また、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] は、<xref:System.Xml.Linq.XAttribute> オブジェクトについても同様のキャスト演算子を用意しています。</span><span class="sxs-lookup"><span data-stu-id="cecb7-118">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides the same cast operators for <xref:System.Xml.Linq.XAttribute> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cecb7-119">例</span><span class="sxs-lookup"><span data-stu-id="cecb7-119">Example</span></span>  
 <span data-ttu-id="cecb7-120"><xref:System.Xml.Linq.XElement.Value%2A> プロパティを使用すると、要素のコンテンツを取得できます。</span><span class="sxs-lookup"><span data-stu-id="cecb7-120">You can use the <xref:System.Xml.Linq.XElement.Value%2A> property to retrieve the contents of an element:</span></span>  
  
```vb  
Dim e As XElement = <StringElement>abcde</StringElement>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & e.Value)  
```  
  
 <span data-ttu-id="cecb7-121">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="cecb7-121">This example produces the following output:</span></span>  
  
```xml  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="cecb7-122">例</span><span class="sxs-lookup"><span data-stu-id="cecb7-122">Example</span></span>  
 <span data-ttu-id="cecb7-123">存在しているかどうかが明確でない要素の値の取得を試行する場合があります。</span><span class="sxs-lookup"><span data-stu-id="cecb7-123">Sometimes you try to retrieve the value of an element even though you are not sure it exists.</span></span> <span data-ttu-id="cecb7-124">この場合、NULL 値が許容される型 (`string` または [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] での NULL 値が許容される型のいずれか) に、キャストされた要素を代入すると、要素が存在しない場合に、代入された変数が `Nothing` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="cecb7-124">In this case, when you assign the casted element to a nullable type (either `string` or one of the nullable types in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]), if the element does not exist the assigned variable is just set to `Nothing`.</span></span> <span data-ttu-id="cecb7-125">要素が存在するかどうかわからないときは、<xref:System.Xml.Linq.XElement.Value%2A> プロパティよりもキャストを使用した方が簡単であることを、次のコードは示しています。</span><span class="sxs-lookup"><span data-stu-id="cecb7-125">The following code shows that when the element might or might not exist, it is easier to use casting than to use the <xref:System.Xml.Linq.XElement.Value%2A> property.</span></span>  
  
```vb  
Dim root As XElement = <Root>  
                           <Child1>child 1 content</Child1>  
                           <Child2>2</Child2>  
                       </Root>  
  
' The following assignments show why it is easier to use  
' casting when the element might or might not exist.  
  
Dim c1 As String = CStr(root.Element("Child1"))  
Console.WriteLine("c1:{0}", IIf(c1 Is Nothing, "element does not exist", c1))  
  
Dim c2 As Nullable(Of Integer) = CType(root.Element("Child2"), Nullable(Of Integer))  
Console.WriteLine("c2:{0}", IIf(Not (c2.HasValue), "element does not exist", c2.ToString()))  
  
Dim c3 As String = CStr(root.Element("Child3"))  
Console.WriteLine("c3:{0}", IIf(c3 Is Nothing, "element does not exist", c3))  
  
Dim c4 As Nullable(Of Integer) = CType(root.Element("Child4"), Nullable(Of Integer))  
Console.WriteLine("c4:{0}", IIf(Not (c4.HasValue), "element does not exist", c4.ToString()))  
  
Console.WriteLine()  
  
' The following assignments show the required code when using  
' the Value property when the attribute might or might not exist.  
' Notice that this is more difficult than the casting approach.  
  
Dim e1 As XElement = root.Element("Child1")  
Dim v1 As String  
If (e1 Is Nothing) Then  
    v1 = Nothing  
Else  
    v1 = e1.Value  
End If  
Console.WriteLine("v1:{0}", IIf(v1 Is Nothing, "element does not exist", v1))  
  
Dim e2 As XElement = root.Element("Child2")  
Dim v2 As Nullable(Of Integer)  
If (e2 Is Nothing) Then  
    v2 = Nothing  
Else  
    v2 = e2.Value  
End If  
Console.WriteLine("v2:{0}", IIf(Not (v2.HasValue), "element does not exist", v2))  
  
Dim e3 As XElement = root.Element("Child3")  
Dim v3 As String  
If (e3 Is Nothing) Then  
    v3 = Nothing  
Else  
    v3 = e3.Value  
End If  
Console.WriteLine("v3:{0}", IIf(v3 Is Nothing, "element does not exist", v3))  
  
Dim e4 As XElement = root.Element("Child4")  
Dim v4 As Nullable(Of Integer)  
If (e4 Is Nothing) Then  
    v4 = Nothing  
Else  
    v4 = e4.Value  
End If  
Console.WriteLine("v4:{0}", IIf(Not (v4.HasValue), "element does not exist", v4))  
```  
  
 <span data-ttu-id="cecb7-126">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="cecb7-126">This code produces the following output:</span></span>  
  
```  
c1:child 1 content  
c2:2  
c3:element does not exist  
c4:element does not exist  
  
v1:child 1 content  
v2:2  
v3:element does not exist  
v4:element does not exist  
```  
  
 <span data-ttu-id="cecb7-127">通常、要素や属性のコンテンツを取得するには、キャストを使用する方が単純なコードになります。</span><span class="sxs-lookup"><span data-stu-id="cecb7-127">In general, you can write simpler code when using casting to retrieve the contents of elements and attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cecb7-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="cecb7-128">See Also</span></span>  
 [<span data-ttu-id="cecb7-129">LINQ to XML 軸 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cecb7-129">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
