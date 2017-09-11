---
title: "関数型構築 (LINQ to XML) (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: b88b67aca337b893f9f276c8e4a6589b6946069b
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="functional-construction-linq-to-xml-visual-basic"></a><span data-ttu-id="05a2c-102">関数型構築 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="05a2c-102">Functional Construction (LINQ to XML) (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="05a2c-103">呼ばれる XML 要素を作成するための優れた方法は、*関数型構築*します。</span><span class="sxs-lookup"><span data-stu-id="05a2c-103"> provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="05a2c-104">関数型構築は、単一のステートメントで XML ツリーを作成するための機能です。</span><span class="sxs-lookup"><span data-stu-id="05a2c-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="05a2c-105">[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] プログラミング インターフェイスには、関数型構築を利用するためのいくつかの重要な機能があります。</span><span class="sxs-lookup"><span data-stu-id="05a2c-105">There are several key features of the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] programming interface that enable functional construction:</span></span>  
  
-   <span data-ttu-id="05a2c-106"><xref:System.Xml.Linq.XElement>コンス トラクターはさまざまな種類のコンテンツ引数を受け取ります</xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="05a2c-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="05a2c-107">別の渡すなど<xref:System.Xml.Linq.XElement>子要素になるオブジェクト</xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="05a2c-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="05a2c-108">渡すことができます、<xref:System.Xml.Linq.XAttribute>要素の属性になるオブジェクト</xref:System.Xml.Linq.XAttribute>。</span><span class="sxs-lookup"><span data-stu-id="05a2c-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="05a2c-109">また、文字列に変換され、要素のテキスト コンテンツになる他の任意の種類のオブジェクトを渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="05a2c-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
-   <span data-ttu-id="05a2c-110"><xref:System.Xml.Linq.XElement>コンス トラクターは、`params`型の配列<xref:System.Object>、オブジェクトの数をコンス トラクターに渡すことができます</xref:System.Object></xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="05a2c-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="05a2c-111">これにより、複雑なコンテンツを持つ要素を作成できます。</span><span class="sxs-lookup"><span data-stu-id="05a2c-111">This enables you to create an element that has complex content.</span></span>  
  
-   <span data-ttu-id="05a2c-112">オブジェクトを実装する場合<xref:System.Collections.Generic.IEnumerable%601>、オブジェクトのコレクションが列挙され、コレクション内のすべての項目が追加されます</xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="05a2c-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="05a2c-113">コレクションに含まれる場合<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XAttribute>オブジェクト、コレクション内の各アイテムは個別に追加されます</xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="05a2c-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="05a2c-114">これは、重要の結果を渡すことができるので、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]コンス トラクターにクエリします。</span><span class="sxs-lookup"><span data-stu-id="05a2c-114">This is important because it lets you pass the results of a [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] query to the constructor.</span></span>  
  
 <span data-ttu-id="05a2c-115">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="05a2c-115">The following is an example:</span></span>  
  
 <span data-ttu-id="05a2c-116">これらの機能を使用する XML ツリーを作成しの結果を使用するコードを記述に XML リテラルを使用するコードを記述する[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]XML ツリーを作成するときにクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="05a2c-116">These features enable you to write code using XML literals to create an XML tree, and also to write code that uses the results of [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] queries when you create an XML tree:</span></span>  
  
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
  
 <span data-ttu-id="05a2c-117">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="05a2c-117">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="05a2c-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="05a2c-118">See Also</span></span>  
 [<span data-ttu-id="05a2c-119">XML ツリー (Visual Basic) の作成</span><span class="sxs-lookup"><span data-stu-id="05a2c-119">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
