---
title: "方法: 単一の属性 (LINQ to XML) を取得する (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 11b938d7-c011-4048-900e-8b9183c41c94
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 7b4242e051c6171c51c6ace12798e54ae7374e02
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017


---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-visual-basic"></a><span data-ttu-id="31986-102">方法: 単一の属性 (LINQ to XML) を取得する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31986-102">How to: Retrieve a Single Attribute (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="31986-103">このトピックでは、属性名を指定して要素の単一の属性を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="31986-103">This topic explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="31986-104">これは、特定の属性を持つ要素を検索するクエリ式を記述する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="31986-104">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>  
  
 <span data-ttu-id="31986-105"><xref:System.Xml.Linq.XElement.Attribute%2A>のメソッド、<xref:System.Xml.Linq.XElement>クラスを返します、<xref:System.Xml.Linq.XAttribute>指定した名前です。</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement.Attribute%2A> 。</span><span class="sxs-lookup"><span data-stu-id="31986-105">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31986-106">例</span><span class="sxs-lookup"><span data-stu-id="31986-106">Example</span></span>  
 <span data-ttu-id="31986-107">次の例では、<xref:System.Xml.Linq.XElement.Attribute%2A>メソッド</xref:System.Xml.Linq.XElement.Attribute%2A>。</span><span class="sxs-lookup"><span data-stu-id="31986-107">The following example uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method.</span></span>  
  
```vb  
Dim cust As XElement = <PhoneNumbers>  
                           <Phone type="home">555-555-5555</Phone>  
                           <Phone type="work">555-555-6666</Phone>  
                       </PhoneNumbers>  
Dim elList = From el In cust...<Phone>  
For Each e As XElement In elList  
    Console.WriteLine(e.@type)  
Next  
```  
  
 <span data-ttu-id="31986-108">この例では、`Phone` という名前のツリー内のすべての子孫を検索し、次に `type` という名前の属性を検索します。</span><span class="sxs-lookup"><span data-stu-id="31986-108">This example finds all the descendants in the tree named `Phone`, and then finds the attribute named `type`.</span></span>  
  
 <span data-ttu-id="31986-109">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="31986-109">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
## <a name="example"></a><span data-ttu-id="31986-110">例</span><span class="sxs-lookup"><span data-stu-id="31986-110">Example</span></span>  
 <span data-ttu-id="31986-111">属性の値を取得する場合は、キャストできますで場合と同様<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="31986-111">If you want to retrieve the value of the attribute, you can cast it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="31986-112">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="31986-112">The following example demonstrates this.</span></span>  
  
```vb  
Dim cust As XElement = <PhoneNumbers>  
                           <Phone type="home">555-555-5555</Phone>  
                           <Phone type="work">555-555-6666</Phone>  
                       </PhoneNumbers>  
Dim elList As IEnumerable(Of XElement) = _  
    From el In cust...<Phone> _  
    Select el  
For Each el As XElement In elList  
    Console.WriteLine(el.@type)  
Next  
```  
  
 <span data-ttu-id="31986-113">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="31986-113">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="31986-114">provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="31986-114"> provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="31986-115">例</span><span class="sxs-lookup"><span data-stu-id="31986-115">Example</span></span>  
 <span data-ttu-id="31986-116">上記と同じコードを使用して、名前空間内の属性を取得する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="31986-116">The following example shows the same code for an attribute that is in a namespace.</span></span> <span data-ttu-id="31986-117">詳細については、次を参照してください。 [XML 名前空間 (Visual Basic) の使用](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)します。</span><span class="sxs-lookup"><span data-stu-id="31986-117">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim cust As XElement = _  
            <aw:PhoneNumbers>  
                <aw:Phone aw:type="home">555-555-5555</aw:Phone>  
                <aw:Phone aw:type="work">555-555-6666</aw:Phone>  
            </aw:PhoneNumbers>  
        Dim elList As IEnumerable(Of XElement) = _  
            From el In cust...<aw:Phone> _  
            Select el  
        For Each el As XElement In elList  
            Console.WriteLine(el.@aw:type)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="31986-118">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="31986-118">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
## <a name="see-also"></a><span data-ttu-id="31986-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="31986-119">See Also</span></span>  
 [<span data-ttu-id="31986-120">LINQ to XML 軸 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31986-120">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
