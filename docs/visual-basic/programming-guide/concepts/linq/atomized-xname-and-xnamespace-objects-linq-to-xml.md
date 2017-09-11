---
title: "最小単位に分割 XName および XNamespace オブジェクト (LINQ to XML) (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 21ee7585-7df9-40b4-8c76-a12bb5f29bb3
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: a32f50ce8a92fa22d9627a1510a4b3ec1087364e
ms.openlocfilehash: 1303d0be3715bb6462ef28b1b2286b999661d240
ms.contentlocale: ja-jp
ms.lasthandoff: 06/01/2017


---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-visual-basic"></a><span data-ttu-id="ac39b-102">最小単位に分割 XName および XNamespace オブジェクト (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac39b-102">Atomized XName and XNamespace Objects (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="ac39b-103"><xref:System.Xml.Linq.XName><xref:System.Xml.Linq.XNamespace>オブジェクトは、*最小単位に分割*; は、同じ修飾名を含んでいる場合、オブジェクトを参照して、同じです</xref:System.Xml.Linq.XNamespace>。</xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="ac39b-103"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> objects are *atomized*; that is, if they contain the same qualified name, they refer to the same object.</span></span> <span data-ttu-id="ac39b-104">これによってクエリのパフォーマンスが向上します。これは、2 つのアトミック化された名前の等価性を比べる場合に、基になる中間言語が、2 つの参照が同じオブジェクトを指しているかどうかを判別するだけで済むためです。</span><span class="sxs-lookup"><span data-stu-id="ac39b-104">This yields performance benefits for queries: When you compare two atomized names for equality, the underlying intermediate language only has to determine whether the two references point to the same object.</span></span> <span data-ttu-id="ac39b-105">基になるコードは、時間のかかる文字列比較を行う必要がありません。</span><span class="sxs-lookup"><span data-stu-id="ac39b-105">The underlying code does not have to do string comparisons, which would be time consuming.</span></span>  
  
## <a name="atomization-semantics"></a><span data-ttu-id="ac39b-106">アトミック化のセマンティクス</span><span class="sxs-lookup"><span data-stu-id="ac39b-106">Atomization Semantics</span></span>  
 <span data-ttu-id="ac39b-107">アトミック化という&2; つ<xref:System.Xml.Linq.XName>オブジェクトが同じローカル名を所有していて、同じ名前空間内にある、同じインスタンスを共有する</xref:System.Xml.Linq.XName>。</span><span class="sxs-lookup"><span data-stu-id="ac39b-107">Atomization means that if two <xref:System.Xml.Linq.XName> objects have the same local name, and they are in the same namespace, they share the same instance.</span></span> <span data-ttu-id="ac39b-108">2 つの場合は、同じ方法で<xref:System.Xml.Linq.XNamespace>オブジェクトが同じ名前空間 URI を持つ、同じインスタンスを共有します</xref:System.Xml.Linq.XNamespace>。</span><span class="sxs-lookup"><span data-stu-id="ac39b-108">In the same way, if two <xref:System.Xml.Linq.XNamespace> objects have the same namespace URI, they share the same instance.</span></span>  
  
 <span data-ttu-id="ac39b-109">アトミック化されたオブジェクトをクラスに対して有効にするには、クラスのコンストラクターがパブリックではなく、プライベートであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="ac39b-109">For a class to enable atomized objects, the constructor for the class must be private, not public.</span></span> <span data-ttu-id="ac39b-110">その理由は、コンストラクターがパブリックであれば、アトミック化されていないオブジェクトを作成できるからです。</span><span class="sxs-lookup"><span data-stu-id="ac39b-110">This is because if the constructor were public, you could create a non-atomized object.</span></span> <span data-ttu-id="ac39b-111"><xref:System.Xml.Linq.XName>および<xref:System.Xml.Linq.XNamespace>クラスの実装に<xref:System.Xml.Linq.XName>または<xref:System.Xml.Linq.XNamespace>.</xref:System.Xml.Linq.XNamespace></xref:System.Xml.Linq.XName>文字列に変換する暗黙的な変換演算子</xref:System.Xml.Linq.XNamespace></xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="ac39b-111">The <xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> classes implement an implicit conversion operator to convert a string into an <xref:System.Xml.Linq.XName> or <xref:System.Xml.Linq.XNamespace>.</span></span> <span data-ttu-id="ac39b-112">この方法でこれらのオブジェクトのインスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="ac39b-112">This is how you get an instance of these objects.</span></span> <span data-ttu-id="ac39b-113">コンストラクターにはアクセスできないため、コンストラクターを使用してインスタンスを取得することはできません。</span><span class="sxs-lookup"><span data-stu-id="ac39b-113">You cannot get an instance by using a constructor, because the constructor is inaccessible.</span></span>  
  
 <span data-ttu-id="ac39b-114"><xref:System.Xml.Linq.XName><xref:System.Xml.Linq.XNamespace>実装等値演算子および非等値演算子の&2; つのオブジェクト比較対象となるが、同じインスタンスを参照するかどうかを判断することもできます</xref:System.Xml.Linq.XNamespace>。</xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="ac39b-114"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> also implement the equality and inequality operators, to determine whether the two objects being compared are references to the same instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac39b-115">例</span><span class="sxs-lookup"><span data-stu-id="ac39b-115">Example</span></span>  
 <span data-ttu-id="ac39b-116">次のコードを作成<xref:System.Xml.Linq.XElement>オブジェクトし、同じ名前が同じインスタンスを共有することを示しています</xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="ac39b-116">The following code creates some <xref:System.Xml.Linq.XElement> objects and demonstrates that identical names share the same instance.</span></span>  
  
```vb  
Dim r1 As New XElement("Root", "data1")  
Dim r2 As XElement = XElement.Parse("<Root>data2</Root>")  
  
If DirectCast(r1.Name, Object) = DirectCast(r2.Name, Object) Then  
    Console.WriteLine("r1 and r2 have names that refer to the same instance.")  
Else  
    Console.WriteLine("Different")  
End If  
  
Dim n As XName = "Root"  
  
If DirectCast(n, Object) = DirectCast(r1.Name, Object) Then  
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.")  
Else  
    Console.WriteLine("Different")  
End If  
```  
  
 <span data-ttu-id="ac39b-117">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ac39b-117">This example produces the following output:</span></span>  
  
```  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 <span data-ttu-id="ac39b-118">前述のように、アトミック化されたオブジェクトの利点は、されるときに、軸メソッドのいずれかを使用する、<xref:System.Xml.Linq.XName>をパラメーターとして、軸メソッドのみが決定する&2; つの名前の参照を同じインスタンスを目的の要素を選択します</xref:System.Xml.Linq.XName>。</span><span class="sxs-lookup"><span data-stu-id="ac39b-118">As mentioned earlier, the benefit of atomized objects is that when you use one of the axis methods that take an <xref:System.Xml.Linq.XName> as a parameter, the axis method only has to determine that two names reference the same instance to select the desired elements.</span></span>  
  
 <span data-ttu-id="ac39b-119">次の例では、<xref:System.Xml.Linq.XName>に、<xref:System.Xml.Linq.XContainer.Descendants%2A>ので、アトミック化パターンによってパフォーマンスの向上がメソッド呼び出し</xref:System.Xml.Linq.XContainer.Descendants%2A></xref:System.Xml.Linq.XName>。</span><span class="sxs-lookup"><span data-stu-id="ac39b-119">The following example passes an <xref:System.Xml.Linq.XName> to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method call, which then has better performance because of the atomization pattern.</span></span>  
  
```vb  
Dim root As New XElement("Root", New XElement("C1", 1), New XElement("Z1", New XElement("C1", 2), New XElement("C1", 1)))  
  
Dim query = From e In root.Descendants("C1") Where CInt(e) = 1e  
  
For Each z As var In query  
    Console.WriteLine(z)  
Next  
```  
  
 <span data-ttu-id="ac39b-120">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ac39b-120">This example produces the following output:</span></span>  
  
```xml  
<C1>1</C1>  
<C1>1</C1>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac39b-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="ac39b-121">See Also</span></span>  
 [<span data-ttu-id="ac39b-122">パフォーマンス (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac39b-122">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)

