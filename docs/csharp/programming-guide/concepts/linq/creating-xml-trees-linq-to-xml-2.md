---
title: "C# での XML ツリーの作成 (LINQ to XML)"
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
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ac95fcf49736b554c8a3d4d0061f63b3ac4d3f65
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="creating-xml-trees-in-c-linq-to-xml"></a><span data-ttu-id="b64cc-102">C# での XML ツリーの作成 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="b64cc-102">Creating XML Trees in C# (LINQ to XML)</span></span>
<span data-ttu-id="b64cc-103">ここでは、C# での XML ツリーの作成について説明します。</span><span class="sxs-lookup"><span data-stu-id="b64cc-103">This section provides information about creating XML trees in C#.</span></span>  
  
 <span data-ttu-id="b64cc-104">LINQ クエリの結果を <xref:System.Xml.Linq.XElement> のコンテンツとして使用する方法については、「[関数型構築 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b64cc-104">For information about using the results of LINQ queries as the content for an <xref:System.Xml.Linq.XElement>, see [Functional Construction (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span></span>  
  
## <a name="constructing-elements"></a><span data-ttu-id="b64cc-105">要素の構築</span><span class="sxs-lookup"><span data-stu-id="b64cc-105">Constructing Elements</span></span>  
 <span data-ttu-id="b64cc-106"><xref:System.Xml.Linq.XElement> コンストラクターと <xref:System.Xml.Linq.XAttribute> コンストラクターのシグネチャを使用すると、要素または属性のコンテンツを引数としてコンストラクターに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="b64cc-106">The signatures of the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors let you pass the contents of the element or attribute as arguments to the constructor.</span></span> <span data-ttu-id="b64cc-107">いずれかのコンストラクターは任意の数の引数を受け取るため、任意の数の子要素を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="b64cc-107">Because one of the constructors takes a variable number of arguments, you can pass any number of child elements.</span></span> <span data-ttu-id="b64cc-108">もちろん、それらの子要素のそれぞれに、さらに子要素を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="b64cc-108">Of course, each of those child elements can contain their own child elements.</span></span> <span data-ttu-id="b64cc-109">いずれの要素にも、任意の数の属性を追加できます。</span><span class="sxs-lookup"><span data-stu-id="b64cc-109">For any element, you can add any number of attributes.</span></span>  
  
 <span data-ttu-id="b64cc-110"><xref:System.Xml.Linq.XNode> オブジェクト (<xref:System.Xml.Linq.XElement> を含む) や <xref:System.Xml.Linq.XAttribute> オブジェクトの追加時に、新しいコンテンツに親がない場合、単にオブジェクトが XML ツリーにアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="b64cc-110">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="b64cc-111">新しいコンテンツに既に親があり、別の XML ツリーの一部となっている場合は、新しいコンテンツが複製され、新しく複製されたコンテンツが XML ツリーにアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="b64cc-111">If the new content already is parented, and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span> <span data-ttu-id="b64cc-112">このトピックの最後の例では、この動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="b64cc-112">The last example in this topic demonstrates this.</span></span>  
  
 <span data-ttu-id="b64cc-113">`contacts`<xref:System.Xml.Linq.XElement> を作成するには、次のコードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b64cc-113">To create a `contacts`<xref:System.Xml.Linq.XElement>, you could use the following code:</span></span>  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),   
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 <span data-ttu-id="b64cc-114">適切にインデントされていれば、<xref:System.Xml.Linq.XElement> オブジェクトを構築するコードは、基になる XML の構造によく似ています。</span><span class="sxs-lookup"><span data-stu-id="b64cc-114">If indented properly, the code to construct <xref:System.Xml.Linq.XElement> objects closely resembles the structure of the underlying XML.</span></span>  
  
## <a name="xelement-constructors"></a><span data-ttu-id="b64cc-115">XElement コンストラクター</span><span class="sxs-lookup"><span data-stu-id="b64cc-115">XElement Constructors</span></span>  
 <span data-ttu-id="b64cc-116"><xref:System.Xml.Linq.XElement> クラスは、関数型構築で次のコンストラクターを使用します。</span><span class="sxs-lookup"><span data-stu-id="b64cc-116">The <xref:System.Xml.Linq.XElement> class uses the following constructors for functional construction.</span></span> <span data-ttu-id="b64cc-117"><xref:System.Xml.Linq.XElement> のコンストラクターはこれ以外にも存在しますが、関数型構築に使用されないものはこの一覧に示していません。</span><span class="sxs-lookup"><span data-stu-id="b64cc-117">Note that there are some other constructors for <xref:System.Xml.Linq.XElement>, but because they are not used for functional construction they are not listed here.</span></span>  
  
|<span data-ttu-id="b64cc-118">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="b64cc-118">Constructor</span></span>|<span data-ttu-id="b64cc-119">説明</span><span class="sxs-lookup"><span data-stu-id="b64cc-119">Description</span></span>|  
|-----------------|-----------------|  
|`XElement(XName name, object content)`|<span data-ttu-id="b64cc-120"><xref:System.Xml.Linq.XElement> を作成します。</span><span class="sxs-lookup"><span data-stu-id="b64cc-120">Creates an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="b64cc-121">`name` パラメーターには要素の名前を指定し、`content` には要素のコンテンツを指定します。</span><span class="sxs-lookup"><span data-stu-id="b64cc-121">The `name` parameter specifies the name of the element; `content` specifies the content of the element.</span></span>|  
|`XElement(XName name)`|<span data-ttu-id="b64cc-122">指定した名前で <xref:System.Xml.Linq.XElement> を初期化して、<xref:System.Xml.Linq.XName> を作成します。</span><span class="sxs-lookup"><span data-stu-id="b64cc-122">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span>|  
|`XElement(XName name, params object[] content)`|<span data-ttu-id="b64cc-123">指定した名前で <xref:System.Xml.Linq.XElement> を初期化して、<xref:System.Xml.Linq.XName> を作成します。</span><span class="sxs-lookup"><span data-stu-id="b64cc-123">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span> <span data-ttu-id="b64cc-124">属性や子要素が、パラメーター リストのコンテンツから作成されます。</span><span class="sxs-lookup"><span data-stu-id="b64cc-124">The attributes and/or child elements are created from the contents of the parameter list.</span></span>|  
  
 <span data-ttu-id="b64cc-125">`content` パラメーターは非常に柔軟です。</span><span class="sxs-lookup"><span data-stu-id="b64cc-125">The `content` parameter is extremely flexible.</span></span> <span data-ttu-id="b64cc-126"><xref:System.Xml.Linq.XElement> の有効な子オブジェクトの型すべてがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b64cc-126">It supports any type of object that is a valid child of an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="b64cc-127">このパラメーターで渡されるさまざまな型のオブジェクトには、次の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="b64cc-127">The following rules apply to different types of objects passed in this parameter:</span></span>  
  
-   <span data-ttu-id="b64cc-128">文字列はテキスト コンテンツとして追加されます。</span><span class="sxs-lookup"><span data-stu-id="b64cc-128">A string is added as text content.</span></span>  
  
-   <span data-ttu-id="b64cc-129"><xref:System.Xml.Linq.XElement> は子要素として追加されます。</span><span class="sxs-lookup"><span data-stu-id="b64cc-129">An <xref:System.Xml.Linq.XElement> is added as a child element.</span></span>  
  
-   <span data-ttu-id="b64cc-130"><xref:System.Xml.Linq.XAttribute> は属性として追加されます。</span><span class="sxs-lookup"><span data-stu-id="b64cc-130">An <xref:System.Xml.Linq.XAttribute> is added as an attribute.</span></span>  
  
-   <span data-ttu-id="b64cc-131"><xref:System.Xml.Linq.XProcessingInstruction>、<xref:System.Xml.Linq.XComment>、または <xref:System.Xml.Linq.XText> は、子コンテンツとして追加されます。</span><span class="sxs-lookup"><span data-stu-id="b64cc-131">An <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment>, or <xref:System.Xml.Linq.XText> is added as child content.</span></span>  
  
-   <span data-ttu-id="b64cc-132"><xref:System.Collections.IEnumerable> は列挙され、その結果にこれらの規則が再帰的に適用されます。</span><span class="sxs-lookup"><span data-stu-id="b64cc-132">An <xref:System.Collections.IEnumerable> is enumerated, and these rules are applied recursively to the results.</span></span>  
  
-   <span data-ttu-id="b64cc-133">その他の型に対しては `ToString` メソッドが呼び出され、その結果がテキスト コンテンツとして追加されます。</span><span class="sxs-lookup"><span data-stu-id="b64cc-133">For any other type, its `ToString` method is called and the result is added as text content.</span></span>  
  
### <a name="creating-an-xelement-with-content"></a><span data-ttu-id="b64cc-134">コンテンツを持つ XElement の作成</span><span class="sxs-lookup"><span data-stu-id="b64cc-134">Creating an XElement with Content</span></span>  
 <span data-ttu-id="b64cc-135">単純コンテンツが含まれる <xref:System.Xml.Linq.XElement> は、1 回のメソッド呼び出しで作成できます。</span><span class="sxs-lookup"><span data-stu-id="b64cc-135">You can create an <xref:System.Xml.Linq.XElement> that contains simple content with a single method call.</span></span> <span data-ttu-id="b64cc-136">そのためには、次のように、コンテンツを 2 番目のパラメーターとして指定します。</span><span class="sxs-lookup"><span data-stu-id="b64cc-136">To do this, specify the content as the second parameter, as follows:</span></span>  
  
```csharp  
XElement n = new XElement("Customer", "Adventure Works");  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="b64cc-137">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b64cc-137">This example produces the following output:</span></span>  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
 <span data-ttu-id="b64cc-138">任意の型のオブジェクトをコンテンツとして渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="b64cc-138">You can pass any type of object as the content.</span></span> <span data-ttu-id="b64cc-139">たとえば、次のコードでは、浮動小数点数がコンテンツとして含まれる要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="b64cc-139">For example, the following code creates an element that contains a floating point number as content:</span></span>  
  
```csharp  
XElement n = new XElement("Cost", 324.50);  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="b64cc-140">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b64cc-140">This example produces the following output:</span></span>  
  
```xml  
<Cost>324.5</Cost>  
```  
  
 <span data-ttu-id="b64cc-141">浮動小数点数はボックス化されてコンストラクターに渡されます。</span><span class="sxs-lookup"><span data-stu-id="b64cc-141">The floating point number is boxed and passed in to the constructor.</span></span> <span data-ttu-id="b64cc-142">ボックス化された数は文字列に変換され、要素のコンテンツとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="b64cc-142">The boxed number is converted to a string and used as the content of the element.</span></span>  
  
### <a name="creating-an-xelement-with-a-child-element"></a><span data-ttu-id="b64cc-143">子要素を持つ XElement の作成</span><span class="sxs-lookup"><span data-stu-id="b64cc-143">Creating an XElement with a Child Element</span></span>  
 <span data-ttu-id="b64cc-144"><xref:System.Xml.Linq.XElement> クラスのインスタンスをコンテンツ引数として渡すと、コンストラクターによって、子要素を持つ要素が作成されます。</span><span class="sxs-lookup"><span data-stu-id="b64cc-144">If you pass an instance of the <xref:System.Xml.Linq.XElement> class for the content argument, the constructor creates an element with a child element:</span></span>  
  
```csharp  
XElement shippingUnit = new XElement("ShippingUnit",  
    new XElement("Cost", 324.50)  
);  
Console.WriteLine(shippingUnit);  
```  
  
 <span data-ttu-id="b64cc-145">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b64cc-145">This example produces the following output:</span></span>  
  
```xml  
<ShippingUnit>  
  <Cost>324.5</Cost>  
</ShippingUnit>  
```  
  
### <a name="creating-an-xelement-with-multiple-child-elements"></a><span data-ttu-id="b64cc-146">複数の子要素を持つ XElement の作成</span><span class="sxs-lookup"><span data-stu-id="b64cc-146">Creating an XElement with Multiple Child Elements</span></span>  
 <span data-ttu-id="b64cc-147">複数の <xref:System.Xml.Linq.XElement> オブジェクトをコンテンツとして渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="b64cc-147">You can pass in a number of <xref:System.Xml.Linq.XElement> objects for the content.</span></span> <span data-ttu-id="b64cc-148">各 <xref:System.Xml.Linq.XElement> オブジェクトは、子要素として格納されます。</span><span class="sxs-lookup"><span data-stu-id="b64cc-148">Each of the <xref:System.Xml.Linq.XElement> objects is included as a child element.</span></span>  
  
```csharp  
XElement address = new XElement("Address",  
    new XElement("Street1", "123 Main St"),  
    new XElement("City", "Mercer Island"),  
    new XElement("State", "WA"),  
    new XElement("Postal", "68042")  
);  
Console.WriteLine(address);  
```  
  
 <span data-ttu-id="b64cc-149">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b64cc-149">This example produces the following output:</span></span>  
  
```xml  
<Address>  
  <Street1>123 Main St</Street1>  
  <City>Mercer Island</City>  
  <State>WA</State>  
  <Postal>68042</Postal>  
</Address>  
```  
  
 <span data-ttu-id="b64cc-150">上の例を次のように拡張すると、完全な XML ツリーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b64cc-150">By extending the above example, you can create an entire XML tree, as follows:</span></span>  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),                                                   
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
Console.WriteLine(contacts);  
```  
  
 <span data-ttu-id="b64cc-151">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b64cc-151">This example produces the following output:</span></span>  
  
```xml  
<Contacts>  
  <Contact>  
    <Name>Patrick Hines</Name>  
    <Phone>206-555-0144</Phone>  
    <Address>  
      <Street1>123 Main St</Street1>  
      <City>Mercer Island</City>  
      <State>WA</State>  
      <Postal>68042</Postal>  
    </Address>  
  </Contact>  
</Contacts>  
```  
  
### <a name="creating-an-empty-element"></a><span data-ttu-id="b64cc-152">空要素の作成</span><span class="sxs-lookup"><span data-stu-id="b64cc-152">Creating an Empty Element</span></span>  
 <span data-ttu-id="b64cc-153">空の <xref:System.Xml.Linq.XElement> を作成する場合は、コンストラクターにコンテンツを渡しません。</span><span class="sxs-lookup"><span data-stu-id="b64cc-153">To create an empty <xref:System.Xml.Linq.XElement>, you do not pass any content to the constructor.</span></span> <span data-ttu-id="b64cc-154">次の例では、空要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="b64cc-154">The following example creates an empty element:</span></span>  
  
```csharp  
XElement n = new XElement("Customer");  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="b64cc-155">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b64cc-155">This example produces the following output:</span></span>  
  
```xml  
<Customer />  
```  
  
### <a name="attaching-vs-cloning"></a><span data-ttu-id="b64cc-156">アタッチと複製</span><span class="sxs-lookup"><span data-stu-id="b64cc-156">Attaching vs. Cloning</span></span>  
 <span data-ttu-id="b64cc-157">既に説明したように、<xref:System.Xml.Linq.XNode> オブジェクト (<xref:System.Xml.Linq.XElement> を含む) や <xref:System.Xml.Linq.XAttribute> オブジェクトの追加時に、新しいコンテンツに親がない場合、単にオブジェクトが XML ツリーにアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="b64cc-157">As mentioned previously, when adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="b64cc-158">新しいコンテンツに既に親があり、別の XML ツリーの一部となっている場合は、新しいコンテンツが複製され、新しく複製されたコンテンツが XML ツリーにアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="b64cc-158">If the new content already is parented and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  
  
```csharp  
// Create a tree with a child element.  
XElement xmlTree1 = new XElement("Root",  
    new XElement("Child1", 1)  
);  
  
// Create an element that is not parented.  
XElement child2 = new XElement("Child2", 2);  
  
// Create a tree and add Child1 and Child2 to it.  
XElement xmlTree2 = new XElement("Root",  
    xmlTree1.Element("Child1"),  
    child2  
);  
  
// Compare Child1 identity.  
Console.WriteLine("Child1 was {0}",  
    xmlTree1.Element("Child1") == xmlTree2.Element("Child1") ?  
    "attached" : "cloned");  
  
// Compare Child2 identity.  
Console.WriteLine("Child2 was {0}",  
    child2 == xmlTree2.Element("Child2") ?  
    "attached" : "cloned");  
```  
  
 <span data-ttu-id="b64cc-159">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b64cc-159">This example produces the following output:</span></span>  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="b64cc-160">関連項目</span><span class="sxs-lookup"><span data-stu-id="b64cc-160">See Also</span></span>  
 [<span data-ttu-id="b64cc-161">XML ツリーの作成 (C#)</span><span class="sxs-lookup"><span data-stu-id="b64cc-161">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)

