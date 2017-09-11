---
title: "宣言型コードと命令型コードの混在のバグ (LINQ to XML) (C#)"
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
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
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
ms.openlocfilehash: 2fb679ee2593520e633daba969ccaa4db4d30509
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="mixed-declarative-codeimperative-code-bugs-linq-to-xml-c"></a><span data-ttu-id="d4e74-102">宣言型コードと命令型コードの混在のバグ (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d4e74-102">Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="d4e74-103"> には、XML ツリーを直接変更できるさまざまなメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d4e74-103"> contains various methods that allow you to modify an XML tree directly.</span></span> <span data-ttu-id="d4e74-104">たとえば、要素の追加、要素の削除、要素の内容の変更、属性の追加などの操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="d4e74-104">You can add elements, delete elements, change the contents of an element, add attributes, and so on.</span></span> <span data-ttu-id="d4e74-105">このプログラミング インターフェイスについては、「[XML ツリーの変更 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4e74-105">This programming interface is described in [Modifying XML Trees (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span></span> <span data-ttu-id="d4e74-106">いずれかの軸 (<xref:System.Xml.Linq.XContainer.Elements%2A> など) を反復処理する場合に、その過程で XML ツリーを変更すると、見慣れないバグが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="d4e74-106">If you are iterating through one of the axes, such as <xref:System.Xml.Linq.XContainer.Elements%2A>, and you are modifying the XML tree as you iterate through the axis, you can end up with some strange bugs.</span></span>  
  
 <span data-ttu-id="d4e74-107">この問題は、"ハロウィーン問題" と呼ばれることがあります。</span><span class="sxs-lookup"><span data-stu-id="d4e74-107">This problem is sometimes known as "The Halloween Problem".</span></span>  
  
## <a name="definition-of-the-problem"></a><span data-ttu-id="d4e74-108">問題の定義</span><span class="sxs-lookup"><span data-stu-id="d4e74-108">Definition of the Problem</span></span>  
 <span data-ttu-id="d4e74-109">コレクションを反復処理するコードを LINQ を使用して記述する場合は、宣言型スタイルでコードを記述することになります。</span><span class="sxs-lookup"><span data-stu-id="d4e74-109">When you write some code using LINQ that iterates through a collection, you are writing code in a declarative style.</span></span> <span data-ttu-id="d4e74-110">この場合、*どのように*処理するかではなく、*何が*必要かを記述します。</span><span class="sxs-lookup"><span data-stu-id="d4e74-110">It is more akin to describing *what* you want, rather that *how* you want to get it done.</span></span> <span data-ttu-id="d4e74-111">たとえば、1) 最初の要素を取得する、2) この要素を何らかの条件に対してテストする、3) この要素を変更する、4) この要素をリストに戻す、というコードを記述した場合、それは命令型のコードです。</span><span class="sxs-lookup"><span data-stu-id="d4e74-111">If you write code that 1) gets the first element, 2) tests it for some condition, 3) modifies it, and 4) puts it back into the list, then this would be imperative code.</span></span> <span data-ttu-id="d4e74-112">必要な処理を*どのように*行うかをコンピューターに指示しています。</span><span class="sxs-lookup"><span data-stu-id="d4e74-112">You are telling the computer *how* to do what you want done.</span></span>  
  
 <span data-ttu-id="d4e74-113">この 2 つのスタイルのコードが同じ操作に混在していると、問題の原因になります。</span><span class="sxs-lookup"><span data-stu-id="d4e74-113">Mixing these styles of code in the same operation is what leads to problems.</span></span> <span data-ttu-id="d4e74-114">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d4e74-114">Consider the following:</span></span>  
  
 <span data-ttu-id="d4e74-115">3 つの項目 (a、b、および c) を含むリンク リストがあるとします。</span><span class="sxs-lookup"><span data-stu-id="d4e74-115">Suppose you have a linked list with three items in it (a, b, and c):</span></span>  
  
 `a -> b -> c`  
  
 <span data-ttu-id="d4e74-116">このリンク リスト内を移動しながら 3 つの新しい項目 (a'、b'、および c') を追加して、</span><span class="sxs-lookup"><span data-stu-id="d4e74-116">Now, suppose that you want to move through the linked list, adding three new items (a', b', and c').</span></span> <span data-ttu-id="d4e74-117">次のようなリンク リストが生成されるようにします。</span><span class="sxs-lookup"><span data-stu-id="d4e74-117">You want the resulting linked list to look like this:</span></span>  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 <span data-ttu-id="d4e74-118">ここで、リストを反復処理して各項目の後ろに新しいアイテムを追加するコードを記述した場合、</span><span class="sxs-lookup"><span data-stu-id="d4e74-118">So you write code that iterates through the list, and for every item, adds a new item right after it.</span></span> <span data-ttu-id="d4e74-119">その結果は、コードによって最初に `a` 要素が検出され、その後ろに `a'` が追加されます。</span><span class="sxs-lookup"><span data-stu-id="d4e74-119">What happens is that your code will first see the `a` element, and insert `a'` after it.</span></span> <span data-ttu-id="d4e74-120">その後、リストの次のノードに移動しますが、それは既に `a'` になっています。</span><span class="sxs-lookup"><span data-stu-id="d4e74-120">Now, your code will move to the next node in the list, which is now `a'`!</span></span> <span data-ttu-id="d4e74-121">そのため、新しい項目として `a''` がリストに追加されてしまいます。</span><span class="sxs-lookup"><span data-stu-id="d4e74-121">It happily adds a new item to the list, `a''`.</span></span>  
  
 <span data-ttu-id="d4e74-122">現実にこのような問題が発生したら、どうすればよいでしょうか。</span><span class="sxs-lookup"><span data-stu-id="d4e74-122">How would you solve this in the real world?</span></span> <span data-ttu-id="d4e74-123">まず、元のリンク リストをコピーして、まったく新しいリストを作成する方法が考えられます。</span><span class="sxs-lookup"><span data-stu-id="d4e74-123">Well, you might make a copy of the original linked list, and create a completely new list.</span></span> <span data-ttu-id="d4e74-124">また、純粋な命令型のコードを記述するのであれば、最初の項目を検出し、新しい項目を追加したら、リンク リストの 2 つ先 (追加した要素を越えた先) に移動するという方法もあります。</span><span class="sxs-lookup"><span data-stu-id="d4e74-124">Or if you are writing purely imperative code, you might find the first item, add the new item, and then advance twice in the linked list, advancing over the element that you just added.</span></span>  
  
## <a name="adding-while-iterating"></a><span data-ttu-id="d4e74-125">反復処理と追加</span><span class="sxs-lookup"><span data-stu-id="d4e74-125">Adding While Iterating</span></span>  
 <span data-ttu-id="d4e74-126">たとえば、ツリーのすべての要素に対してその複製となる要素を作成するコードを記述するとします。</span><span class="sxs-lookup"><span data-stu-id="d4e74-126">For example, suppose you want to write some code that for every element in a tree, you want to create a duplicate element:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    root.Add(new XElement(e.Name, (string)e));  
```  
  
 <span data-ttu-id="d4e74-127">このコードは、無限ループに入ります。</span><span class="sxs-lookup"><span data-stu-id="d4e74-127">This code goes into an infinite loop.</span></span> <span data-ttu-id="d4e74-128">`foreach` ステートメントは、`Elements()` 軸を反復処理して `doc` 要素に新しい要素を追加しますが、</span><span class="sxs-lookup"><span data-stu-id="d4e74-128">The `foreach` statement iterates through the `Elements()` axis, adding new elements to the `doc` element.</span></span> <span data-ttu-id="d4e74-129">追加した要素も反復処理されることになります。</span><span class="sxs-lookup"><span data-stu-id="d4e74-129">It ends up iterating also through the elements it just added.</span></span> <span data-ttu-id="d4e74-130">ループが繰り返されるたびに新しいオブジェクトが割り当てられるため、最後には使用可能なメモリがすべて消費されてしまいます。</span><span class="sxs-lookup"><span data-stu-id="d4e74-130">And because it allocates new objects with every iteration of the loop, it will eventually consume all available memory.</span></span>  
  
 <span data-ttu-id="d4e74-131">この問題を修正するには、次のように、標準クエリ演算子の <xref:System.Linq.Enumerable.ToList%2A> を使用してコレクションをメモリに読み込みます。</span><span class="sxs-lookup"><span data-stu-id="d4e74-131">You can fix this problem by pulling the collection into memory using the <xref:System.Linq.Enumerable.ToList%2A> standard query operator, as follows:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements().ToList())  
    root.Add(new XElement(e.Name, (string)e));  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="d4e74-132">これで、コードが機能するようになります。</span><span class="sxs-lookup"><span data-stu-id="d4e74-132">Now the code works.</span></span> <span data-ttu-id="d4e74-133">結果の XML ツリーは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="d4e74-133">The resulting XML tree is the following:</span></span>  
  
```xml  
<Root>  
  <A>1</A>  
  <B>2</B>  
  <C>3</C>  
  <A>1</A>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
## <a name="deleting-while-iterating"></a><span data-ttu-id="d4e74-134">反復処理と削除</span><span class="sxs-lookup"><span data-stu-id="d4e74-134">Deleting While Iterating</span></span>  
 <span data-ttu-id="d4e74-135">特定のレベルのノードをすべて削除する場合、次のようなコードを記述することが考えられます。</span><span class="sxs-lookup"><span data-stu-id="d4e74-135">If you want to delete all nodes at a certain level, you might be tempted to write code like the following:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    e.Remove();  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="d4e74-136">しかし、これでは目的の操作は行われません。</span><span class="sxs-lookup"><span data-stu-id="d4e74-136">However, this does not do what you want.</span></span> <span data-ttu-id="d4e74-137">最初の要素 A を削除すると、ルートに含まれる XML ツリーから A が削除されるため、反復処理を行っている Elements メソッド内のコードが次の要素を見つけられなくなります。</span><span class="sxs-lookup"><span data-stu-id="d4e74-137">In this situation, after you have removed the first element, A, it is removed from the XML tree contained in root, and the code in the Elements method that is doing the iterating cannot find the next element.</span></span>  
  
 <span data-ttu-id="d4e74-138">上のコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="d4e74-138">The preceding code produces the following output:</span></span>  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 <span data-ttu-id="d4e74-139">この問題を解決するには、先ほどと同じように、<xref:System.Linq.Enumerable.ToList%2A> を呼び出してコレクションを具体化します。</span><span class="sxs-lookup"><span data-stu-id="d4e74-139">The solution again is to call <xref:System.Linq.Enumerable.ToList%2A> to materialize the collection, as follows:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements().ToList())  
    e.Remove();  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="d4e74-140">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="d4e74-140">This produces the following output:</span></span>  
  
```xml  
<Root />  
```  
  
 <span data-ttu-id="d4e74-141">他の方法として、親要素で <xref:System.Xml.Linq.XElement.RemoveAll%2A> を呼び出して、反復処理を完全に取り除くこともできます。</span><span class="sxs-lookup"><span data-stu-id="d4e74-141">Alternatively, you can eliminate the iteration altogether by calling <xref:System.Xml.Linq.XElement.RemoveAll%2A> on the parent element:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
root.RemoveAll();  
Console.WriteLine(root);  
```  
  
## <a name="why-cant-linq-automatically-handle-this"></a><span data-ttu-id="d4e74-142">この問題が LINQ で自動的に処理されない理由</span><span class="sxs-lookup"><span data-stu-id="d4e74-142">Why Can't LINQ Automatically Handle This?</span></span>  
 <span data-ttu-id="d4e74-143">まず、レイジー評価を行う代わりに常にすべてをメモリに読み込む方法が考えられます。</span><span class="sxs-lookup"><span data-stu-id="d4e74-143">One approach would be to always bring everything into memory instead of doing lazy evaluation.</span></span> <span data-ttu-id="d4e74-144">しかし、この方法では、パフォーマンスとメモリ使用量のコストが非常に高くなります。</span><span class="sxs-lookup"><span data-stu-id="d4e74-144">However, it would be very expensive in terms of performance and memory use.</span></span> <span data-ttu-id="d4e74-145">実際、仮に LINQ (LINQ to XML) でこの方法を使用したとしても、現実には使いものにならないでしょう。</span><span class="sxs-lookup"><span data-stu-id="d4e74-145">In fact, if LINQ and (LINQ to XML) were to take this approach, it would fail in real-world situations.</span></span>  
  
 <span data-ttu-id="d4e74-146">その他に、ある種のトランザクション構文を LINQ に追加して、コンパイラがコードを分析して特定のコレクションを具体化する必要があるかどうかを特定するようにする方法も考えられます。</span><span class="sxs-lookup"><span data-stu-id="d4e74-146">Another possible approach would be to put in some sort of transaction syntax into LINQ, and have the compiler attempt to analyze the code and determine if any particular collection needed to be materialized.</span></span> <span data-ttu-id="d4e74-147">しかし、副作用のあるコードをすべて特定しようとすると非常に複雑になります。</span><span class="sxs-lookup"><span data-stu-id="d4e74-147">However, attempting to determine all code that has side-effects is incredibly complex.</span></span> <span data-ttu-id="d4e74-148">次のコードがあるとします。</span><span class="sxs-lookup"><span data-stu-id="d4e74-148">Consider the following code:</span></span>  
  
```csharp  
var z =  
    from e in root.Elements()  
    where TestSomeCondition(e)  
    select DoMyProjection(e);  
```  
  
 <span data-ttu-id="d4e74-149">このような分析コードで副作用のあるコードの有無を特定するには、TestSomeCondition および DoMyProjection の 2 つのメソッドと、これらが呼び出すすべてのメソッドを分析する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4e74-149">Such analysis code would need to analyze the methods TestSomeCondition and DoMyProjection, and all methods that those methods called, to determine if any code had side-effects.</span></span> <span data-ttu-id="d4e74-150">しかし、その分析コードでは、ただ副作用のあるコードを探すだけでなく、</span><span class="sxs-lookup"><span data-stu-id="d4e74-150">But the analysis code could not just look for any code that had side-effects.</span></span> <span data-ttu-id="d4e74-151">この状況では、`root` の子要素に対して副作用があるコードのみを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4e74-151">It would need to select for just the code that had side-effects on the child elements of `root` in this situation.</span></span>  
  
 <span data-ttu-id="d4e74-152">LINQ to XML ではこのような分析は行われません。</span><span class="sxs-lookup"><span data-stu-id="d4e74-152">LINQ to XML does not attempt to do any such analysis.</span></span>  
  
 <span data-ttu-id="d4e74-153">これらの問題は、開発者が回避する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4e74-153">It is up to you to avoid these problems.</span></span>  
  
## <a name="guidance"></a><span data-ttu-id="d4e74-154">ガイダンス</span><span class="sxs-lookup"><span data-stu-id="d4e74-154">Guidance</span></span>  
 <span data-ttu-id="d4e74-155">第 1 に、宣言型のコードと命令型のコードを混在させないようにします。</span><span class="sxs-lookup"><span data-stu-id="d4e74-155">First, do not mix declarative and imperative code.</span></span>  
  
 <span data-ttu-id="d4e74-156">仮に、コレクションのセマンティクスと、XML ツリーを変更するメソッドのセマンティクスを正確に把握していて、このカテゴリの問題を巧妙に回避するコードを記述できたとしても、将来そのコードの保守を行う別の開発者が同じようにこの問題に通じているとは限りません。</span><span class="sxs-lookup"><span data-stu-id="d4e74-156">Even if you know exactly the semantics of your collections and the semantics of the methods that modify the XML tree, if you write some clever code that avoids these categories of problems, your code will need to be maintained by other developers in the future, and they may not be as clear on the issues.</span></span> <span data-ttu-id="d4e74-157">宣言型と命令型のコーディング スタイルが混在していると、コードが不安定になります。</span><span class="sxs-lookup"><span data-stu-id="d4e74-157">If you mix declarative and imperative coding styles, your code will be more brittle.</span></span>  
  
 <span data-ttu-id="d4e74-158">これらの問題を回避するためにコレクションを具体化するコードを記述する場合は、コードを保守するプログラマが問題を把握できるように、必要に応じてコメントを付けるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="d4e74-158">If you write code that materializes a collection so that these problems are avoided, note it with comments as appropriate in your code, so that maintenance programmers will understand the issue.</span></span>  
  
 <span data-ttu-id="d4e74-159">第 2 に、パフォーマンスやその他の事情が許すのであれば、宣言型のコードのみを使用するようにします。</span><span class="sxs-lookup"><span data-stu-id="d4e74-159">Second, if performance and other considerations allow, use only declarative code.</span></span> <span data-ttu-id="d4e74-160">既存の XML ツリーは変更せずに、</span><span class="sxs-lookup"><span data-stu-id="d4e74-160">Don't modify your existing XML tree.</span></span> <span data-ttu-id="d4e74-161">新しいツリーを生成します。</span><span class="sxs-lookup"><span data-stu-id="d4e74-161">Generate a new one.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
XElement newRoot = new XElement("Root",  
    root.Elements(),  
    root.Elements()  
);  
Console.WriteLine(newRoot);  
```  
  
## <a name="see-also"></a><span data-ttu-id="d4e74-162">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4e74-162">See Also</span></span>  
 [<span data-ttu-id="d4e74-163">高度な LINQ to XML プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="d4e74-163">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)

