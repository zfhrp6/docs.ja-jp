---
title: "メモリ内の XML ツリーの変更と関数型構築 (LINQ to XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d91c4ebf-6549-43cc-9961-26d4a82f722b
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3652933a5d25b298167f54525800eceee16264e8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-visual-basic"></a><span data-ttu-id="f664a-102">メモリ内の XML ツリーの変更と関数型構築 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f664a-102">In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="f664a-103">XML ドキュメントの構造を変更する場合は、XML ツリーを直接変更するのが従来の方法です。</span><span class="sxs-lookup"><span data-stu-id="f664a-103">Modifying an XML tree in place is a traditional approach to changing the shape of an XML document.</span></span> <span data-ttu-id="f664a-104">一般的なアプリケーションでは、ドキュメントを DOM や [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] などのデータ ストアに読み込み、プログラミング インターフェイスを使用してノードの挿入、削除、または内容変更を行い、その後に XML をファイルに保存するか、またはネットワーク上に送信します。</span><span class="sxs-lookup"><span data-stu-id="f664a-104">A typical application loads a document into a data store such as DOM or [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; uses a programming interface to insert nodes, delete nodes, or change the content of nodes; and then saves the XML to a file or transmits it over a network.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="f664a-105"> では、多くのシナリオで役立つもう 1 つの方法として、*関数型構築*を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f664a-105"> enables another approach that is useful in many scenarios*: functional construction*.</span></span> <span data-ttu-id="f664a-106">関数型構築では、データの変更が、データ ストアの詳細な操作としてではなく変換の問題として扱われます。</span><span class="sxs-lookup"><span data-stu-id="f664a-106">Functional construction treats modifying data as a problem of transformation, rather than as detailed manipulation of a data store.</span></span> <span data-ttu-id="f664a-107">データの表現をある形式から別の形式に効率よく変換できれば、データ ストアを何らかの方法で操作して別の構造にする場合と同じ結果を得られます。</span><span class="sxs-lookup"><span data-stu-id="f664a-107">If you can take a representation of data and transform it efficiently from one form to another, the result is the same as if you took one data store and manipulated it in some way to take another shape.</span></span> <span data-ttu-id="f664a-108">関数型構築の方法で重要なのは、クエリの結果を <xref:System.Xml.Linq.XDocument> コンストラクターと <xref:System.Xml.Linq.XElement> コンストラクターに渡す処理です。</span><span class="sxs-lookup"><span data-stu-id="f664a-108">A key to the functional construction approach is to pass the results of queries to <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement> constructors.</span></span>  
  
 <span data-ttu-id="f664a-109">多くの場合、変換コードは、データ ストアを操作する場合に比べてはるかに短時間で作成でき、堅牢性と保守性にも優れています。</span><span class="sxs-lookup"><span data-stu-id="f664a-109">In many cases you can write the transformational code in a fraction of the time that it would take to manipulate the data store, and that code is more robust and easier to maintain.</span></span> <span data-ttu-id="f664a-110">この場合、変換コードによる方法では、より大きな処理能力を必要とする可能性はありますが、効果的にデータを変更できます。</span><span class="sxs-lookup"><span data-stu-id="f664a-110">In these cases, even though the transformational approach can take more processing power, it is a more effective way to modify data.</span></span> <span data-ttu-id="f664a-111">開発者が関数型の方法に精通していれば、ほとんどの場合、作成されるコードもよりわかりやすくなります。</span><span class="sxs-lookup"><span data-stu-id="f664a-111">If a developer is familiar with the functional approach, the resulting code in many cases is easier to understand.</span></span> <span data-ttu-id="f664a-112">ツリーの各部分を変更するコードが簡単に見つかります。</span><span class="sxs-lookup"><span data-stu-id="f664a-112">It is easy to find the code that modifies each part of the tree.</span></span>  
  
 <span data-ttu-id="f664a-113">DOM プログラマの多くは、XML ツリーを直接変更する方法に慣れています。関数型の方法をまだ理解していない開発者は、この方法で記述されたコードに慣れていない場合があります。</span><span class="sxs-lookup"><span data-stu-id="f664a-113">The approach where you modify an XML tree in-place is more familiar to many DOM programmers, whereas code written using the functional approach might look unfamiliar to a developer who doesn't yet understand that approach.</span></span> <span data-ttu-id="f664a-114">大きな XML ツリーに小さな変更を加えるだけであれば、ツリーを直接変更する方法の方が使用する CPU 時間が少ない場合がほとんどです。</span><span class="sxs-lookup"><span data-stu-id="f664a-114">If you have to only make a small modification to a large XML tree, the approach where you modify a tree in place in many cases will take less CPU time.</span></span>  
  
 <span data-ttu-id="f664a-115">このトピックでは、両方の方法での実装例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="f664a-115">This topic provides an example that is implemented with both approaches.</span></span>  
  
## <a name="transforming-attributes-into-elements"></a><span data-ttu-id="f664a-116">属性から要素への変換</span><span class="sxs-lookup"><span data-stu-id="f664a-116">Transforming Attributes into Elements</span></span>  
 <span data-ttu-id="f664a-117">この例では、属性が要素となるように、次の単純な XML ドキュメントを変更するケースを想定します。</span><span class="sxs-lookup"><span data-stu-id="f664a-117">For this example, suppose you want to modify the following simple XML document so that the attributes become elements.</span></span> <span data-ttu-id="f664a-118">まず、直接変更する従来の方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f664a-118">This topic first presents the traditional in-place modification approach.</span></span> <span data-ttu-id="f664a-119">その後に関数型構築の方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f664a-119">It then shows the functional construction approach.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root Data1="123" Data2="456">  
  <Child1>Content</Child1>  
</Root>  
```  
  
### <a name="modifying-the-xml-tree"></a><span data-ttu-id="f664a-120">XML ツリーの変更</span><span class="sxs-lookup"><span data-stu-id="f664a-120">Modifying the XML Tree</span></span>  
 <span data-ttu-id="f664a-121">属性から要素を作成した後に属性を削除する、次のようなプロシージャ コードを記述します。</span><span class="sxs-lookup"><span data-stu-id="f664a-121">You can write some procedural code to create elements from the attributes, and then delete the attributes, as follows:</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
For Each att As XAttribute In root.Attributes()  
    root.Add(New XElement(att.Name, att.Value))  
Next  
root.Attributes().Remove()  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="f664a-122">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f664a-122">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Content</Child1>  
  <Data1>123</Data1>  
  <Data2>456</Data2>  
</Root>  
```  
  
### <a name="functional-construction-approach"></a><span data-ttu-id="f664a-123">関数型構築の方法</span><span class="sxs-lookup"><span data-stu-id="f664a-123">Functional Construction Approach</span></span>  
 <span data-ttu-id="f664a-124">上のコードとは対照的に、関数型の方法を構成するコードでは、新しいツリーを作成し、ソース ツリーから要素と属性を選択し、その要素と属性を新しいツリーに追加するときに適宜変換します。</span><span class="sxs-lookup"><span data-stu-id="f664a-124">By contrast, a functional approach consists of code to form a new tree, picking and choosing elements and attributes from the source tree, and transforming them as appropriate as they are added to the new tree.</span></span> <span data-ttu-id="f664a-125">関数型の方法は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="f664a-125">The functional approach looks like the following:</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
Dim newTree As XElement = _  
    <Root>  
        <%= root.<Child1> %>  
        <%= From att In root.Attributes() _  
            Select New XElement(att.Name, att.Value) %>  
    </Root>  
Console.WriteLine(newTree)  
```  
  
 <span data-ttu-id="f664a-126">この例では、最初の例と同じ XML が出力されます。</span><span class="sxs-lookup"><span data-stu-id="f664a-126">This example outputs the same XML as the first example.</span></span> <span data-ttu-id="f664a-127">ただし、関数型の方法では、新しい XML の構造が実際に作成されます。</span><span class="sxs-lookup"><span data-stu-id="f664a-127">However, notice that you can actually see the resulting structure of the new XML in the functional approach.</span></span> <span data-ttu-id="f664a-128">`Root` 要素、ソース ツリーから `Child1` 要素を取り出すコード、およびソース ツリーから取得した属性を新しいツリーの要素に変換するコードが作成されることがわかります。</span><span class="sxs-lookup"><span data-stu-id="f664a-128">You can see the creation of the `Root` element, the code that pulls the `Child1` element from the source tree, and the code that transforms the attributes from the source tree to elements in the new tree.</span></span>  
  
 <span data-ttu-id="f664a-129">ここで示した関数型の例は、最初の例と比べて短くはなく、単純でもありません。</span><span class="sxs-lookup"><span data-stu-id="f664a-129">The functional example in this case is not any shorter than the first example, and it is not really any simpler.</span></span> <span data-ttu-id="f664a-130">しかし XML ツリーに多数の変更を加える場合、関数型でない方法では、処理がかなり複雑になり、効率的とはいえません。</span><span class="sxs-lookup"><span data-stu-id="f664a-130">However, if you have many changes to make to an XML tree, the non functional approach will become quite complex and somewhat obtuse.</span></span> <span data-ttu-id="f664a-131">一方、関数型の方法では、クエリと式を適宜組み込んだ必要な XML を作成するだけで、必要な内容を取り出せます。</span><span class="sxs-lookup"><span data-stu-id="f664a-131">In contrast, when using the functional approach, you still just form the desired XML, embedding queries and expressions as appropriate, to pull in the desired content.</span></span> <span data-ttu-id="f664a-132">関数型の方法で生成されたコードの方が、保守も簡単です。</span><span class="sxs-lookup"><span data-stu-id="f664a-132">The functional approach yields code that is easier to maintain.</span></span>  
  
 <span data-ttu-id="f664a-133">この例では、ツリーを操作する方法に比べて関数型の方法のパフォーマンスが低くなる可能性があるので注意してください。</span><span class="sxs-lookup"><span data-stu-id="f664a-133">Notice that in this case the functional approach probably would not perform quite as well as the tree manipulation approach.</span></span> <span data-ttu-id="f664a-134">主な問題は、関数型の方法では存続期間の短いオブジェクトが多数作成されることです。</span><span class="sxs-lookup"><span data-stu-id="f664a-134">The main issue is that the functional approach creates more short lived objects.</span></span> <span data-ttu-id="f664a-135">その代わりに、関数型の方法の方がプログラマの生産性が高いという効果があります。</span><span class="sxs-lookup"><span data-stu-id="f664a-135">However, the tradeoff is an effective one if using the functional approach allows for greater programmer productivity.</span></span>  
  
 <span data-ttu-id="f664a-136">ここで示したのはごく単純な例ですが、2 つの方法に関する考え方の違いをよく表しています。</span><span class="sxs-lookup"><span data-stu-id="f664a-136">This is a very simple example, but it serves to show the difference in philosophy between the two approaches.</span></span> <span data-ttu-id="f664a-137">大きな XML ドキュメントを変換する場合は、関数型の方法を使用した方が生産性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="f664a-137">The functional approach yields greater productivity gains for transforming larger XML documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f664a-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="f664a-138">See Also</span></span>  
 [<span data-ttu-id="f664a-139">XML ツリー (LINQ to XML) の変更 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f664a-139">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
