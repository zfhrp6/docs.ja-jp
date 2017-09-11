---
title: "方法: 要素の値を取得する (LINQ to XML) (C#)"
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
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 70e60c799157c7aa577bb8abd1fa6aaad746d3d1
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-c"></a><span data-ttu-id="ec3b6-102">方法: 要素の値を取得する (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ec3b6-102">How to: Retrieve the Value of an Element (LINQ to XML) (C#)</span></span>
<span data-ttu-id="ec3b6-103">このトピックでは、要素の値を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ec3b6-103">This topic shows how to get the value of elements.</span></span> <span data-ttu-id="ec3b6-104">これには主に 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="ec3b6-104">There are two main ways to do this.</span></span> <span data-ttu-id="ec3b6-105">1 つは <xref:System.Xml.Linq.XElement> または <xref:System.Xml.Linq.XAttribute> を目的の型にキャストする方法です。</span><span class="sxs-lookup"><span data-stu-id="ec3b6-105">One way is to cast an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XAttribute> to the desired type.</span></span> <span data-ttu-id="ec3b6-106">その後、明示的な変換演算子によって、要素または属性のコンテンツが指定した型に変換され、変数に代入されます。</span><span class="sxs-lookup"><span data-stu-id="ec3b6-106">The explicit conversion operator then converts the contents of the element or attribute to the specified type and assigns it to your variable.</span></span> <span data-ttu-id="ec3b6-107">もう 1 つは、<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=fullName> プロパティまたは <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName> プロパティを使用する方法です。</span><span class="sxs-lookup"><span data-stu-id="ec3b6-107">Alternatively, you can use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=fullName> property or the <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName> property.</span></span>  
  
 <span data-ttu-id="ec3b6-108">ただし C# では、通常、キャストがより適切な方法です。</span><span class="sxs-lookup"><span data-stu-id="ec3b6-108">With C#, however, casting is generally the better approach.</span></span> <span data-ttu-id="ec3b6-109">要素または属性を NULL 値が許容される型にキャストすると、存在が不明確な要素 (または属性) の値を取得する場合にコードをより簡単に記述できます。</span><span class="sxs-lookup"><span data-stu-id="ec3b6-109">If you cast the element or attribute to a nullable type, the code is simpler to write when retrieving the value of an element (or attribute) that might or might not exist.</span></span> <span data-ttu-id="ec3b6-110">このトピックの最後の例では、この動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="ec3b6-110">The last example in this topic demonstrates this.</span></span> <span data-ttu-id="ec3b6-111">ただし、<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=fullName> プロパティの場合とは異なり、キャストを通じて要素のコンテンツを設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="ec3b6-111">However, you cannot set the contents of an element through casting, as you can through <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=fullName> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec3b6-112">例</span><span class="sxs-lookup"><span data-stu-id="ec3b6-112">Example</span></span>  
 <span data-ttu-id="ec3b6-113">要素の値を取得するには、<xref:System.Xml.Linq.XElement> オブジェクトを目的の型にキャストします。</span><span class="sxs-lookup"><span data-stu-id="ec3b6-113">To retrieve the value of an element, you just cast the <xref:System.Xml.Linq.XElement> object to your desired type.</span></span> <span data-ttu-id="ec3b6-114">次に示すように、要素はいつでも文字列にキャストできます。</span><span class="sxs-lookup"><span data-stu-id="ec3b6-114">You can always cast an element to a string, as follows:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (string)e);  
```  
  
 <span data-ttu-id="ec3b6-115">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ec3b6-115">This example produces the following output:</span></span>  
  
```  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="ec3b6-116">例</span><span class="sxs-lookup"><span data-stu-id="ec3b6-116">Example</span></span>  
 <span data-ttu-id="ec3b6-117">文字列以外の型に要素をキャストすることもできます。</span><span class="sxs-lookup"><span data-stu-id="ec3b6-117">You can also cast elements to types other than string.</span></span> <span data-ttu-id="ec3b6-118">たとえば、次のコードに示すように、整数を含んだ要素を `int` にキャストできます。</span><span class="sxs-lookup"><span data-stu-id="ec3b6-118">For example, if you have an element that contains an integer, you can cast it to `int`, as shown in the following code:</span></span>  
  
```csharp  
XElement e = new XElement("Age", "44");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (int)e);  
```  
  
 <span data-ttu-id="ec3b6-119">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ec3b6-119">This example produces the following output:</span></span>  
  
```  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="ec3b6-120"> では、`string`、`bool`、`bool?`、`int`、`int?`、`uint`、`uint?`、`long`、`long?`、`ulong`、`ulong?`、`float`、`float?`、`double`、`double?`、`decimal`、`decimal?`、`DateTime`、`DateTime?`、`TimeSpan`、`TimeSpan?`、`GUID`、および `GUID?` というデータ型について明示的なキャスト演算子を用意しています。</span><span class="sxs-lookup"><span data-stu-id="ec3b6-120"> provides explicit cast operators for the following data types: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
 <span data-ttu-id="ec3b6-121">また、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] は、<xref:System.Xml.Linq.XAttribute> オブジェクトについても同様のキャスト演算子を用意しています。</span><span class="sxs-lookup"><span data-stu-id="ec3b6-121">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides the same cast operators for <xref:System.Xml.Linq.XAttribute> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec3b6-122">例</span><span class="sxs-lookup"><span data-stu-id="ec3b6-122">Example</span></span>  
 <span data-ttu-id="ec3b6-123"><xref:System.Xml.Linq.XElement.Value%2A> プロパティを使用すると、要素のコンテンツを取得できます。</span><span class="sxs-lookup"><span data-stu-id="ec3b6-123">You can use the <xref:System.Xml.Linq.XElement.Value%2A> property to retrieve the contents of an element:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");   
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + e.Value);  
```  
  
 <span data-ttu-id="ec3b6-124">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ec3b6-124">This example produces the following output:</span></span>  
  
```  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="ec3b6-125">例</span><span class="sxs-lookup"><span data-stu-id="ec3b6-125">Example</span></span>  
 <span data-ttu-id="ec3b6-126">存在しているかどうかが明確でない要素の値の取得を試行する場合があります。</span><span class="sxs-lookup"><span data-stu-id="ec3b6-126">Sometimes you try to retrieve the value of an element even though you are not sure it exists.</span></span> <span data-ttu-id="ec3b6-127">この場合、NULL 値が許容される型 (`string` または [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] での NULL 値が許容される型のいずれか) に、キャストされた要素を代入すると、要素が存在しない場合に、代入された変数が `null` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ec3b6-127">In this case, when you assign the casted element to a nullable type (either `string` or one of the nullable types in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]), if the element does not exist the assigned variable is just set to `null`.</span></span> <span data-ttu-id="ec3b6-128">要素が存在するかどうかわからないときは、<xref:System.Xml.Linq.XElement.Value%2A> プロパティよりもキャストを使用した方が簡単であることを、次のコードは示しています。</span><span class="sxs-lookup"><span data-stu-id="ec3b6-128">The following code shows that when the element might or might not exist, it is easier to use casting than to use the <xref:System.Xml.Linq.XElement.Value%2A> property.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", "child 1 content"),  
    new XElement("Child2", "2")  
);  
  
// The following assignments show why it is easier to use  
// casting when the element might or might not exist.  
  
string c1 = (string)root.Element("Child1");  
Console.WriteLine("c1:{0}", c1 == null ? "element does not exist" : c1);  
  
int? c2 = (int?)root.Element("Child2");  
Console.WriteLine("c2:{0}", c2 == null ? "element does not exist" : c2.ToString());  
  
string c3 = (string)root.Element("Child3");  
Console.WriteLine("c3:{0}", c3 == null ? "element does not exist" : c3);  
  
int? c4 = (int?)root.Element("Child4");  
Console.WriteLine("c4:{0}", c4 == null ? "element does not exist" : c4.ToString());  
  
Console.WriteLine();  
  
// The following assignments show the required code when using  
// the Value property when the element might or might not exist.  
// Notice that this is more difficult than the casting approach.  
  
XElement e1 = root.Element("Child1");  
string v1;  
if (e1 == null)  
    v1 = null;  
else  
    v1 = e1.Value;  
Console.WriteLine("v1:{0}", v1 == null ? "element does not exist" : v1);  
  
XElement e2 = root.Element("Child2");  
int? v2;  
if (e2 == null)  
    v2 = null;  
else  
    v2 = Int32.Parse(e2.Value);  
Console.WriteLine("v2:{0}", v2 == null ? "element does not exist" : v2.ToString());  
  
XElement e3 = root.Element("Child3");  
string v3;  
if (e3 == null)  
    v3 = null;  
else  
    v3 = e3.Value;  
Console.WriteLine("v3:{0}", v3 == null ? "element does not exist" : v3);  
  
XElement e4 = root.Element("Child4");  
int? v4;  
if (e4 == null)  
    v4 = null;  
else  
    v4 = Int32.Parse(e4.Value);  
Console.WriteLine("v4:{0}", v4 == null ? "element does not exist" : v4.ToString());  
```  
  
 <span data-ttu-id="ec3b6-129">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ec3b6-129">This code produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="ec3b6-130">通常、要素や属性のコンテンツを取得するには、キャストを使用する方が単純なコードになります。</span><span class="sxs-lookup"><span data-stu-id="ec3b6-130">In general, you can write simpler code when using casting to retrieve the contents of elements and attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec3b6-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="ec3b6-131">See Also</span></span>  
 [<span data-ttu-id="ec3b6-132">LINQ to XML 軸 (C#)</span><span class="sxs-lookup"><span data-stu-id="ec3b6-132">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)

