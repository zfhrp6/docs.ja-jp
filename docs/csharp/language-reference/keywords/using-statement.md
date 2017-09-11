---
title: "using ステートメント (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
caps.latest.revision: 31
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 201dde951b4f92d92b7d78b3d71a3f3cfb559507
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="using-statement-c-reference"></a><span data-ttu-id="c2415-102">using ステートメント (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="c2415-102">using Statement (C# Reference)</span></span>
<span data-ttu-id="c2415-103"><xref:System.IDisposable> オブジェクトの正しい使用を保証する簡易構文を提供します。</span><span class="sxs-lookup"><span data-stu-id="c2415-103">Provides a convenient syntax that ensures the correct use of <xref:System.IDisposable> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2415-104">例</span><span class="sxs-lookup"><span data-stu-id="c2415-104">Example</span></span>  
 <span data-ttu-id="c2415-105">using ステートメントを使用する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="c2415-105">The following example shows how to use the using statement.</span></span>  
  
 <span data-ttu-id="c2415-106">[!code-cs[csrefKeywordsNamespace#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="c2415-106">[!code-cs[csrefKeywordsNamespace#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_1.cs)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2415-107">コメント</span><span class="sxs-lookup"><span data-stu-id="c2415-107">Remarks</span></span>  
 <span data-ttu-id="c2415-108"><xref:System.IO.File> と <xref:System.Drawing.Font> は、アンマネージ リソース (この場合はファイル ハンドルとデバイス コンテキスト) にアクセスするマネージ型の例です。</span><span class="sxs-lookup"><span data-stu-id="c2415-108"><xref:System.IO.File> and <xref:System.Drawing.Font> are examples of managed types that access unmanaged resources (in this case file handles and device contexts).</span></span> <span data-ttu-id="c2415-109">アンマネージ リソースや、それをカプセル化するクラス ライブラリ型は他にもたくさんあります。</span><span class="sxs-lookup"><span data-stu-id="c2415-109">There are many other kinds of unmanaged resources and class library types that encapsulate them.</span></span> <span data-ttu-id="c2415-110">このような型はすべて、<xref:System.IDisposable> インターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2415-110">All such types must implement the <xref:System.IDisposable> interface.</span></span>  
  
 <span data-ttu-id="c2415-111">一般に、`IDisposable` オブジェクトを使用するときは、それを `using` ステートメントで宣言して、インスタンス化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2415-111">As a rule, when you use an `IDisposable` object, you should declare and instantiate it in a `using` statement.</span></span> <span data-ttu-id="c2415-112">`using` ステートメントは、オブジェクトで正しく <xref:System.IDisposable.Dispose%2A> メソッドを呼び出します。(前述のようにこのステートメントを使用する場合) <xref:System.IDisposable.Dispose%2A> が呼び出されるとすぐに、オブジェクト自体がスコープの外側に出されます。</span><span class="sxs-lookup"><span data-stu-id="c2415-112">The `using` statement calls the <xref:System.IDisposable.Dispose%2A> method on the object in the correct way, and (when you use it as shown earlier) it also causes the object itself to go out of scope as soon as <xref:System.IDisposable.Dispose%2A> is called.</span></span> <span data-ttu-id="c2415-113">オブジェクトは、`using` ブロック内では読み取り専用です。変更したり再割り当てしたりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="c2415-113">Within the `using` block, the object is read-only and cannot be modified or reassigned.</span></span>  
  
 <span data-ttu-id="c2415-114">`using` ステートメントを使用すると、オブジェクトでのメソッドの呼び出し中に例外が発生した場合でも <xref:System.IDisposable.Dispose%2A> が必ず呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="c2415-114">The `using` statement ensures that <xref:System.IDisposable.Dispose%2A> is called even if an exception occurs while you are calling methods on the object.</span></span> <span data-ttu-id="c2415-115">オブジェクトを try ブロックに配置し、finally ブロックで <xref:System.IDisposable.Dispose%2A> を呼び出しても、同じ結果が得られます。実際には、コンパイラは `using` ステートメントをこのように変換します。</span><span class="sxs-lookup"><span data-stu-id="c2415-115">You can achieve the same result by putting the object inside a try block and then calling <xref:System.IDisposable.Dispose%2A> in a finally block; in fact, this is how the `using` statement is translated by the compiler.</span></span> <span data-ttu-id="c2415-116">前のコード例は、コンパイル時に次のコードに展開されます (オブジェクトのスコープ制限を定義する中かっこが加えられていることに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="c2415-116">The code example earlier expands to the following code at compile time (note the extra curly braces to create the limited scope for the object):</span></span>  
  
 <span data-ttu-id="c2415-117">[!code-cs[csrefKeywordsNamespace#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="c2415-117">[!code-cs[csrefKeywordsNamespace#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_2.cs)]</span></span>  
  
 <span data-ttu-id="c2415-118">次の例のように、`using` ステートメントでは型の複数のインスタンスを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="c2415-118">Multiple instances of a type can be declared in a `using` statement, as shown in the following example.</span></span>  
  
 <span data-ttu-id="c2415-119">[!code-cs[csrefKeywordsNamespace#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="c2415-119">[!code-cs[csrefKeywordsNamespace#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_3.cs)]</span></span>  
  
 <span data-ttu-id="c2415-120">リソース オブジェクトをインスタンス化してから、変数を `using` ステートメントに渡すことはできますが、これはベスト プラクティスではありません。</span><span class="sxs-lookup"><span data-stu-id="c2415-120">You can instantiate the resource object and then pass the variable to the `using` statement, but this is not a best practice.</span></span> <span data-ttu-id="c2415-121">この場合、アンマネージ リソースへのアクセスがなくなっている可能性が高いのにもかかわらず、制御が `using` ブロックを離れた後もオブジェクトはスコープ内に残ります。</span><span class="sxs-lookup"><span data-stu-id="c2415-121">In this case, the object remains in scope after control leaves the `using` block even though it will probably no longer have access to its unmanaged resources.</span></span> <span data-ttu-id="c2415-122">つまり、完全に初期化されることはありません。</span><span class="sxs-lookup"><span data-stu-id="c2415-122">In other words, it will no longer be fully initialized.</span></span> <span data-ttu-id="c2415-123">`using` ブロックの外側でオブジェクトを使用しようとすると、例外がスローされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c2415-123">If you try to use the object outside the `using` block, you risk causing an exception to be thrown.</span></span> <span data-ttu-id="c2415-124">このため、通常は、オブジェクトを `using` ステートメントでインスタンス化して、そのスコープを `using` ブロックに制限することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c2415-124">For this reason, it is generally better to instantiate the object in the `using` statement and limit its scope to the `using` block.</span></span>  
  
 <span data-ttu-id="c2415-125">[!code-cs[csrefKeywordsNamespace#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="c2415-125">[!code-cs[csrefKeywordsNamespace#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_4.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="c2415-126">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="c2415-126">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c2415-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="c2415-127">See Also</span></span>  
 <span data-ttu-id="c2415-128">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="c2415-128">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="c2415-129">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="c2415-129">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="c2415-130">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="c2415-130">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="c2415-131">[using ディレクティブ](../../../csharp/language-reference/keywords/using-directive.md) </span><span class="sxs-lookup"><span data-stu-id="c2415-131">[using Directive](../../../csharp/language-reference/keywords/using-directive.md) </span></span>  
 <span data-ttu-id="c2415-132">[ガベージ コレクション](../../../standard/garbage-collection/index.md) </span><span class="sxs-lookup"><span data-stu-id="c2415-132">[Garbage Collection](../../../standard/garbage-collection/index.md) </span></span>  
 [<span data-ttu-id="c2415-133">Dispose メソッドの実装</span><span class="sxs-lookup"><span data-stu-id="c2415-133">Implementing a Dispose Method</span></span>](../../../standard/garbage-collection/implementing-dispose.md)

