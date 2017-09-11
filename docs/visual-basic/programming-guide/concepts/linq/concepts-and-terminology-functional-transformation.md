---
title: "概念と用語 (関数型変換) (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 24fd244d-ebae-4721-8858-89bb544aea0b
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9b07bfffbb4f5c9d833f821c9c548892aab0e606
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017


---
# <a name="concepts-and-terminology-functional-transformation-visual-basic"></a><span data-ttu-id="37596-102">概念と用語 (関数型変換) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37596-102">Concepts and Terminology (Functional Transformation) (Visual Basic)</span></span>
<span data-ttu-id="37596-103">このトピックでは、純粋関数型変換の概念と用語について説明します。</span><span class="sxs-lookup"><span data-stu-id="37596-103">This topic introduces the concepts and terminology of pure functional transformations.</span></span> <span data-ttu-id="37596-104">データの変換に対して関数型変換の方法を使用すると、多くの場合、従来の命令型のプログラミングよりすばやいプログラミングが可能になります。また、さまざまな表現を使用した、デバッグや保守の容易なコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="37596-104">The functional transformation approach to transforming data yields code that is often quicker to program, more expressive, and easier to debug and maintain than more traditional, imperative programming.</span></span>  
  
 <span data-ttu-id="37596-105">このセクションのトピックでは、関数型プログラミングのすべてを説明するのではなく、</span><span class="sxs-lookup"><span data-stu-id="37596-105">Note that the topics in this section are not intended to fully explain functional programming.</span></span> <span data-ttu-id="37596-106">XML の変換を容易にするいくつかの機能を紹介することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="37596-106">Instead, these topics identify some of the functional programming capabilities that make it easier to transform XML from one shape to another.</span></span>  
  
## <a name="what-is-pure-functional-transformation"></a><span data-ttu-id="37596-107">純粋関数型変換とは</span><span class="sxs-lookup"><span data-stu-id="37596-107">What Is Pure Functional Transformation?</span></span>  
 <span data-ttu-id="37596-108">*純粋関数型変換*、呼び出された関数のセット*純粋関数*、元の形式の構造化データのセットを別の形式に変換する方法を定義します。</span><span class="sxs-lookup"><span data-stu-id="37596-108">In *pure functional transformation*, a set of functions, called *pure functions*, define how to transform a set of structured data from its original form into another form.</span></span> <span data-ttu-id="37596-109">「純粋」という語は、関数がであることを示します*コンポーザブル*である必要があります。</span><span class="sxs-lookup"><span data-stu-id="37596-109">The word "pure" indicates that the functions are *composable*, which requires that they are:</span></span>  
  
-   <span data-ttu-id="37596-110">*自己完結型*、自由に順序付けおよびできます結び付きやせず、プログラムの残りの部分との相互依存関係ようにします。</span><span class="sxs-lookup"><span data-stu-id="37596-110">*Self-contained*, so that they can be freely ordered and rearranged without entanglement or interdependencies with the rest of the program.</span></span> <span data-ttu-id="37596-111">純粋変換では、その環境を考慮する必要はなく、また環境に対して影響を与えることもありません。</span><span class="sxs-lookup"><span data-stu-id="37596-111">Pure transformations have no knowledge of or effect upon their environment.</span></span> <span data-ttu-id="37596-112">つまり、変換で使用される関数がない*副作用*します。</span><span class="sxs-lookup"><span data-stu-id="37596-112">That is, the functions used in the transformation have no *side effects*.</span></span>  
  
-   <span data-ttu-id="37596-113">*ステートレス*、同じ出力が常に発生を同じ入力で同じ関数または関数のセットを実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="37596-113">*Stateless*, so that executing the same function or specific set of functions on the same input will always result in the same output.</span></span> <span data-ttu-id="37596-114">純粋変換には、以前に使用されたときの情報は保持されません。</span><span class="sxs-lookup"><span data-stu-id="37596-114">Pure transformations have no memory of their prior use.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="37596-115">このチュートリアルの以降では、"純粋関数" という用語を、特定の言語機能ではなくプログラミング方法を指す広い意味で使用します。</span><span class="sxs-lookup"><span data-stu-id="37596-115">In the rest of this tutorial, the term "pure function" is used in a general sense to indicate a programming approach, and not a specific language feature.</span></span>  
>   
>  <span data-ttu-id="37596-116">純粋関数を Visual Basic では関数として実装する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="37596-116">Note that pure functions must be implemented as functions in Visual Basic.</span></span>  
>   
>  <span data-ttu-id="37596-117">また、純粋関数を C++ の純粋仮想メソッドと混同しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="37596-117">Also, you should not confuse pure functions with pure virtual methods in C++.</span></span> <span data-ttu-id="37596-118">純粋仮想メソッドとは、そのメソッドを含むクラスが抽象クラスであり、メソッドの本体が提供されないことを指します。</span><span class="sxs-lookup"><span data-stu-id="37596-118">The latter indicates that the containing class is abstract and that no method body is supplied.</span></span>  
  
### <a name="functional-programming"></a><span data-ttu-id="37596-119">関数型プログラミング</span><span class="sxs-lookup"><span data-stu-id="37596-119">Functional Programming</span></span>  
 <span data-ttu-id="37596-120">*関数型プログラミング*純粋関数型変換を直接サポートするプログラミング方法です。</span><span class="sxs-lookup"><span data-stu-id="37596-120">*Functional programming* is a programming approach that directly supports pure functional transformation.</span></span>  
  
 <span data-ttu-id="37596-121">従来は、ML、スキーム、Haskell、および f# などの汎用関数型プログラミング言語で、主に学術にとって関心のあった。</span><span class="sxs-lookup"><span data-stu-id="37596-121">Historically, general-purpose functional programming languages, such as ML, Scheme, Haskell, and F#, have been primarily of interest to the academic community.</span></span> <span data-ttu-id="37596-122">Visual Basic で純粋関数型変換を記述することはいつもが難しさから、ほとんどのプログラマにとって魅力的なオプションです。</span><span class="sxs-lookup"><span data-stu-id="37596-122">Although it has always been possible to write pure functional transformations in Visual Basic, the difficulty of doing so has not made it an attractive option to most programmers.</span></span> <span data-ttu-id="37596-123">以降のバージョンの Visual Basic では、ただし、新しい言語構成要素など、ラムダ式や型推論により、関数型プログラミングとはるかに簡単で生産性が向上します。</span><span class="sxs-lookup"><span data-stu-id="37596-123">With later versions of Visual Basic, however, new language constructs such as lambda expressions and type inference make it functional programming much easier and more productive.</span></span>  
  
 <span data-ttu-id="37596-124">関数型プログラミングの詳細については、次を参照してください。[関数型プログラミングとします。命令型プログラミング (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)します。</span><span class="sxs-lookup"><span data-stu-id="37596-124">For more information about functional programming, see [Functional Programming vs. Imperative Programming (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md).</span></span>  
  
#### <a name="domain-specific-fp-languages"></a><span data-ttu-id="37596-125">特定領域の FP 言語</span><span class="sxs-lookup"><span data-stu-id="37596-125">Domain-Specific FP Languages</span></span>  
 <span data-ttu-id="37596-126">広く採用されるに至らなかった汎用関数型プログラミング言語に比べると、特定領域の関数型プログラミング言語は成功していると言えます。</span><span class="sxs-lookup"><span data-stu-id="37596-126">Although general functional programming languages have not been widely adopted, specific domain-specific functional programming languages have had better success.</span></span> <span data-ttu-id="37596-127">たとえば、カスケード スタイル シート (CSS) は多くの Web ページのルック アンド フィールの決定に利用されていますし、Extensible Stylesheet Language Transformations (XSLT) スタイル シートは XML データ操作に広く利用されています。</span><span class="sxs-lookup"><span data-stu-id="37596-127">For example, Cascading Style Sheets (CSS) are used to determine the look and feel of many Web pages, and Extensible Stylesheet Language Transformations (XSLT) style sheets are used extensively in XML data manipulation.</span></span> <span data-ttu-id="37596-128">XSLT の詳細については、次を参照してください。 [XSLT 変換](http://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03)します。</span><span class="sxs-lookup"><span data-stu-id="37596-128">For more information about XSLT, see [XSLT Transformations](http://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03).</span></span>  
  
## <a name="terminology"></a><span data-ttu-id="37596-129">用語</span><span class="sxs-lookup"><span data-stu-id="37596-129">Terminology</span></span>  
 <span data-ttu-id="37596-130">次の表に、関数型変換に関連するいくつかの用語の定義を示します。</span><span class="sxs-lookup"><span data-stu-id="37596-130">The following table defines some terms related to functional transformations.</span></span>  
  
 <span data-ttu-id="37596-131">高階 (ファーストクラス) 関数</span><span class="sxs-lookup"><span data-stu-id="37596-131">higher-order (first-class) function</span></span>  
 <span data-ttu-id="37596-132">プログラム オブジェクトとして扱うことのできる関数です。</span><span class="sxs-lookup"><span data-stu-id="37596-132">A function that can be treated as a programmatic object.</span></span> <span data-ttu-id="37596-133">たとえば、他の関数に渡したり、他の関数から返したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="37596-133">For example, a higher-order function can be passed to or returned from other functions.</span></span> <span data-ttu-id="37596-134">Visual basic では、デリゲートやラムダ式は高階関数をサポートする言語機能です。</span><span class="sxs-lookup"><span data-stu-id="37596-134">In Visual Basic, delegates and lambda expressions are language features that support higher-order functions.</span></span> <span data-ttu-id="37596-135">高階関数を記述するには、デリゲートを受け取る引数を&1; つ以上宣言し、通常はラムダ式を使用して呼び出します。</span><span class="sxs-lookup"><span data-stu-id="37596-135">To write a higher-order function, you declare one or more arguments to take delegates, and you often use lambda expressions when calling it.</span></span> <span data-ttu-id="37596-136">標準クエリ演算子の多くは高階関数です。</span><span class="sxs-lookup"><span data-stu-id="37596-136">Many of the standard query operators are higher-order functions.</span></span>  
  
 <span data-ttu-id="37596-137">詳細については、次を参照してください。[標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)します。</span><span class="sxs-lookup"><span data-stu-id="37596-137">For more information, see [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
 <span data-ttu-id="37596-138">ラムダ式</span><span class="sxs-lookup"><span data-stu-id="37596-138">lambda expression</span></span>  
 <span data-ttu-id="37596-139">基本的には、デリゲート型が必要とされる場所で使用できるインラインの匿名関数です。</span><span class="sxs-lookup"><span data-stu-id="37596-139">Essentially, an inline anonymous function that can be used wherever a delegate type is expected.</span></span> <span data-ttu-id="37596-140">これはラムダ式の簡略化した定義ですが、このチュートリアルの目的には十分です。</span><span class="sxs-lookup"><span data-stu-id="37596-140">This is a simplified definition of lambda expressions, but it is adequate for the purposes of this tutorial.</span></span>  
  
 <span data-ttu-id="37596-141">詳細については、次を参照してください。[ラムダ式](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)します。</span><span class="sxs-lookup"><span data-stu-id="37596-141">For more information about, see [Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="37596-142">コレクション</span><span class="sxs-lookup"><span data-stu-id="37596-142">collection</span></span>  
 <span data-ttu-id="37596-143">データの構造化されたセットです。コレクション内のデータは同じ型であるのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="37596-143">A structured set of data, usually of a uniform type.</span></span> <span data-ttu-id="37596-144">LINQ との互換性には、コレクションを実装する必要があります、<xref:System.Collections.IEnumerable>インターフェイスまたは<xref:System.Linq.IQueryable>インターフェイス (または対応するジェネリックの&1; つ<xref:System.Collections.Generic.IEnumerator%601>または<xref:System.Linq.IQueryable%601>).</xref:System.Linq.IQueryable%601> </xref:System.Collections.Generic.IEnumerator%601> </xref:System.Linq.IQueryable> </xref:System.Collections.IEnumerable></span><span class="sxs-lookup"><span data-stu-id="37596-144">To be compatible with LINQ, a collection must implement the <xref:System.Collections.IEnumerable> interface or the <xref:System.Linq.IQueryable> interface (or one of their generic counterparts, <xref:System.Collections.Generic.IEnumerator%601> or <xref:System.Linq.IQueryable%601>).</span></span>  
  
 <span data-ttu-id="37596-145">タプル (匿名型)</span><span class="sxs-lookup"><span data-stu-id="37596-145">tuple (anonymous types)</span></span>  
 <span data-ttu-id="37596-146">タプルは数学的概念で、それぞれが特定の型を持つオブジェクトの有限のシーケンスを意味します。</span><span class="sxs-lookup"><span data-stu-id="37596-146">A mathematical concept, a tuple is a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="37596-147">順序付きリストとも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="37596-147">A tuple is also known as an ordered list.</span></span> <span data-ttu-id="37596-148">匿名型は、この概念の言語実装です。匿名型を使用すると、名前のないクラス型を宣言し、同時にその型のオブジェクトをインスタンス化することができます。</span><span class="sxs-lookup"><span data-stu-id="37596-148">Anonymous types are a language implementation of this concept, which enable an unnamed class type to be declared and an object of that type to be instantiated at the same time.</span></span>  
  
 <span data-ttu-id="37596-149">詳細については、次を参照してください。[匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)します。</span><span class="sxs-lookup"><span data-stu-id="37596-149">For more information, see  [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
 <span data-ttu-id="37596-150">型推論 (暗黙の型指定)</span><span class="sxs-lookup"><span data-stu-id="37596-150">type inference (implicit typing)</span></span>  
 <span data-ttu-id="37596-151">明示的な型宣言がない場合に変数の型を特定するコンパイラの機能です。</span><span class="sxs-lookup"><span data-stu-id="37596-151">The ability of a compiler to determine the type of a variable in the absence of an explicit type declaration.</span></span>  
  
 <span data-ttu-id="37596-152">詳細については、次を参照してください。[ローカル型推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)します。</span><span class="sxs-lookup"><span data-stu-id="37596-152">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
 <span data-ttu-id="37596-153">遅延実行とレイジー評価</span><span class="sxs-lookup"><span data-stu-id="37596-153">deferred execution and lazy evaluation</span></span>  
 <span data-ttu-id="37596-154">解決された値が実際に必要となるまで式の評価を遅らせることを意味します。</span><span class="sxs-lookup"><span data-stu-id="37596-154">The delaying of evaluation of an expression until its resolved value is actually required.</span></span> <span data-ttu-id="37596-155">遅延実行はコレクションでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="37596-155">Deferred execution is supported in collections.</span></span>  
  
 <span data-ttu-id="37596-156">詳細については、次を参照してください。[基本的なクエリ操作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md)と[遅延実行とレイジー評価 linq to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="37596-156">For more information, see [Basic Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md) and [Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="37596-157">これらの言語機能は、このセクション全体にわたってサンプル コードで使用されています。</span><span class="sxs-lookup"><span data-stu-id="37596-157">These language features will be used in code samples throughout this section.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37596-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="37596-158">See Also</span></span>  
 <span data-ttu-id="37596-159">[純粋関数型変換 (Visual Basic) の概要](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="37596-159">[Introduction to Pure Functional Transformations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md) </span></span>  
<span data-ttu-id="37596-160"> [関数型プログラミングと命令型プログラミング (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)</span><span class="sxs-lookup"><span data-stu-id="37596-160"> [Functional Programming vs. Imperative Programming (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)</span></span>
