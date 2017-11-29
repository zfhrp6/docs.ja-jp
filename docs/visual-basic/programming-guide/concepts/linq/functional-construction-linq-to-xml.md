---
title: "関数型構築 (LINQ to XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d5c68fb71fd59d08574cee9eec933cee25e504d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="functional-construction-linq-to-xml-visual-basic"></a><span data-ttu-id="21ad7-102">関数型構築 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21ad7-102">Functional Construction (LINQ to XML) (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="21ad7-103"> には、"*関数型構築*" と呼ばれる強力な XML 要素作成機能があります。</span><span class="sxs-lookup"><span data-stu-id="21ad7-103"> provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="21ad7-104">関数型構築は、単一のステートメントで XML ツリーを作成するための機能です。</span><span class="sxs-lookup"><span data-stu-id="21ad7-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="21ad7-105">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] プログラミング インターフェイスには、関数型構築を利用するためのいくつかの重要な機能があります。</span><span class="sxs-lookup"><span data-stu-id="21ad7-105">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
-   <span data-ttu-id="21ad7-106"><xref:System.Xml.Linq.XElement> コンストラクターは、さまざまな種類のコンテンツ引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="21ad7-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="21ad7-107">たとえば、このコンストラクターに、子要素になる別の <xref:System.Xml.Linq.XElement> オブジェクトや、</span><span class="sxs-lookup"><span data-stu-id="21ad7-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="21ad7-108">要素の属性になる <xref:System.Xml.Linq.XAttribute> オブジェクトを渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="21ad7-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="21ad7-109">また、文字列に変換され、要素のテキスト コンテンツになる他の任意の種類のオブジェクトを渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="21ad7-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
-   <span data-ttu-id="21ad7-110"><xref:System.Xml.Linq.XElement> コンストラクターは、`params` 型の <xref:System.Object> 配列を受け取ります。そのため、任意の数のオブジェクトを配列に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="21ad7-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="21ad7-111">これにより、複雑なコンテンツを持つ要素を作成できます。</span><span class="sxs-lookup"><span data-stu-id="21ad7-111">This enables you to create an element that has complex content.</span></span>  
  
-   <span data-ttu-id="21ad7-112">オブジェクトが <xref:System.Collections.Generic.IEnumerable%601> を実装している場合、オブジェクト内のコレクションが列挙され、コレクション内のすべての項目が追加されます。</span><span class="sxs-lookup"><span data-stu-id="21ad7-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="21ad7-113">コレクションに <xref:System.Xml.Linq.XElement> オブジェクトまたは <xref:System.Xml.Linq.XAttribute> オブジェクトが含まれている場合、コレクション内の各項目が個別に追加されます。</span><span class="sxs-lookup"><span data-stu-id="21ad7-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="21ad7-114">これは重要な機能といえます。その理由は、この機能により、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリの結果をコンストラクターに渡すことができるためです。</span><span class="sxs-lookup"><span data-stu-id="21ad7-114">This is important because it lets you pass the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to the constructor.</span></span>  
  
 <span data-ttu-id="21ad7-115">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="21ad7-115">The following is an example:</span></span>  
  
 <span data-ttu-id="21ad7-116">これらの機能を有効にすると、XML リテラルを使用して、XML ツリーを作成しの結果を使用するコードを記述するコードを記述[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]XML ツリーを作成するときにクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="21ad7-116">These features enable you to write code using XML literals to create an XML tree, and also to write code that uses the results of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries when you create an XML tree:</span></span>  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where CInt(el) > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
```  
  
 <span data-ttu-id="21ad7-117">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="21ad7-117">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="21ad7-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="21ad7-118">See Also</span></span>  
 [<span data-ttu-id="21ad7-119">XML ツリー (Visual Basic) を作成します。</span><span class="sxs-lookup"><span data-stu-id="21ad7-119">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
