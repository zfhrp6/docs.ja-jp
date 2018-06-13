---
title: IDisposable を実装するオブジェクトの使用
ms.date: 04/07/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- try/finally block
- garbage collection, encapsulating resources
ms.assetid: 81b2cdb5-c91a-4a31-9c83-eadc52da5cf0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c586c725a385029db80763ba13915be79c6cd7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576325"
---
# <a name="using-objects-that-implement-idisposable"></a><span data-ttu-id="38614-102">IDisposable を実装するオブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="38614-102">Using objects that implement IDisposable</span></span>

<span data-ttu-id="38614-103">共通言語ランタイムのガベージ コレクターは、アンマネージ オブジェクトによって使用されているメモリを解放しますが、アンマネージ リソースを使用する型は、これらのアンマネージ リソースに割り当てられたメモリが解放されるように <xref:System.IDisposable> インターフェイスを実装しています。</span><span class="sxs-lookup"><span data-stu-id="38614-103">The common language runtime's garbage collector reclaims the memory used by managed objects, but types that use unmanaged resources implement the <xref:System.IDisposable> interface to allow the memory allocated to these unmanaged resources to be reclaimed.</span></span> <span data-ttu-id="38614-104"><xref:System.IDisposable> を実装するオブジェクトを使い終わったら、オブジェクトの <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> の実装を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="38614-104">When you finish using an object that implements <xref:System.IDisposable>, you should call the object's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="38614-105">2 つの方法のいずれかでこれを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="38614-105">You can do this in one of two ways:</span></span>  
  
* <span data-ttu-id="38614-106">C# の `using` ステートメントまたは Visual Basic の `Using` ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="38614-106">With the C# `using` statement or the Visual Basic `Using` statement.</span></span>  
  
* <span data-ttu-id="38614-107">`try/finally` ブロックを実装します。</span><span class="sxs-lookup"><span data-stu-id="38614-107">By implementing a `try/finally` block.</span></span>  

## <a name="the-using-statement"></a><span data-ttu-id="38614-108">using ステートメント</span><span class="sxs-lookup"><span data-stu-id="38614-108">The using statement</span></span>

<span data-ttu-id="38614-109">C# の `using` ステートメントおよび Visual Basic の `Using` ステートメントを使用すると、オブジェクトの作成時やクリーンアップ時に記述する必要のあるコードが簡略化されます。</span><span class="sxs-lookup"><span data-stu-id="38614-109">The `using` statement in C# and the `Using` statement in Visual Basic simplify the code that you must write to create and clean up an object.</span></span> <span data-ttu-id="38614-110">`using` ステートメントは、1 つ以上のリソースを取得し、指定されたステートメントを実行し、オブジェクトを自動的に破棄します。</span><span class="sxs-lookup"><span data-stu-id="38614-110">The `using` statement obtains one or more resources, executes the statements that you specify, and automatically disposes of the object.</span></span> <span data-ttu-id="38614-111">ただし、`using` ステートメントは、オブジェクトが構築されるメソッドのスコープ内で使用されるオブジェクトに対してのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="38614-111">However, the `using` statement is useful only for objects that are used within the scope of the method in which they are constructed.</span></span>  
  
<span data-ttu-id="38614-112">次の例では、`using` ステートメントを使用して <xref:System.IO.StreamReader?displayProperty=nameWithType> オブジェクトを作成し解放します。</span><span class="sxs-lookup"><span data-stu-id="38614-112">The following example uses the `using` statement to create and release a <xref:System.IO.StreamReader?displayProperty=nameWithType> object.</span></span>  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
<span data-ttu-id="38614-113"><xref:System.IO.StreamReader> クラスは <xref:System.IDisposable> インターフェイスを実装し、これはアンマネージ リソースを使用することを示していますが、例では <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> メソッドを明示的に呼び出していないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="38614-113">Note that although the <xref:System.IO.StreamReader> class implements the <xref:System.IDisposable> interface, which indicates that it uses an unmanaged resource, the example doesn't explicitly call the <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="38614-114">C# または Visual Basic コンパイラが `using` ステートメントを見つけると、明示的に `try/finally` ブロックを含む次のコードと同等の中間言語 (IL) を生成します。</span><span class="sxs-lookup"><span data-stu-id="38614-114">When the C# or Visual Basic compiler encounters the `using` statement, it emits intermediate language (IL) that is equivalent to the following code that explicitly contains a `try/finally` block.</span></span>  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
<span data-ttu-id="38614-115">また、C# の `using` ステートメントでは、単一のステートメントで複数のリソースを取得できます。そのようなステートメントは、内部的には複数の `using` ステートメントを入れ子にした場合と同等です。</span><span class="sxs-lookup"><span data-stu-id="38614-115">The C# `using` statement also allows you to acquire multiple resources in a single statement, which is internally equivalent to nested `using` statements.</span></span> <span data-ttu-id="38614-116">次の例では、2 つの異なるファイルの内容を読み取るために、<xref:System.IO.StreamReader> の 2 つのオブジェクトをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="38614-116">The following example instantiates two <xref:System.IO.StreamReader> objects to read the contents of two different files.</span></span>  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a><span data-ttu-id="38614-117">Try/Finally ブロック</span><span class="sxs-lookup"><span data-stu-id="38614-117">Try/finally block</span></span>

<span data-ttu-id="38614-118">`using` ステートメントで `try/finally` ブロックをラップする代わりに、`try/finally` ブロックを直接実装することもできます。</span><span class="sxs-lookup"><span data-stu-id="38614-118">Instead of wrapping a `try/finally` block in a `using` statement, you may choose to implement the `try/finally` block directly.</span></span> <span data-ttu-id="38614-119">これは、個人のコーディング スタイルであることも、次のいずれかの理由からそうすることもあります。</span><span class="sxs-lookup"><span data-stu-id="38614-119">This may be your personal coding style, or you might want to do this for one of the following reasons:</span></span>  
  
* <span data-ttu-id="38614-120">`catch` ブロックでスローされた例外をすべて処理する `try` ブロックを含めるため。</span><span class="sxs-lookup"><span data-stu-id="38614-120">To include a `catch` block to handle any exceptions thrown in the `try` block.</span></span> <span data-ttu-id="38614-121">そうしないと、`try/catch` ブロックがない場合に `using` ブロック内でスローされた例外と同様に、`using` ステートメントによってスローされた例外は処理されません。</span><span class="sxs-lookup"><span data-stu-id="38614-121">Otherwise, any exceptions thrown by the `using` statement are unhandled, as are any exceptions thrown within the `using` block if a `try/catch` block isn't present.</span></span>  
  
* <span data-ttu-id="38614-122">宣言されたブロックに対してスコープがローカルでない <xref:System.IDisposable> を実装するオブジェクトをインスタンス化するため。</span><span class="sxs-lookup"><span data-stu-id="38614-122">To instantiate an object that implements <xref:System.IDisposable> whose scope is not local to the block within which it is declared.</span></span>  
  
<span data-ttu-id="38614-123">次の例は前の例に似ていますが、`try/catch/finally` ブロックを使用して、<xref:System.IO.StreamReader> オブジェクトのインスタンス化、使用、破棄を実行し、<xref:System.IO.StreamReader> コンストラクターと <xref:System.IO.StreamReader.ReadToEnd%2A> メソッドによってスローされた例外を処理しています。</span><span class="sxs-lookup"><span data-stu-id="38614-123">The following example is similar to the previous example, except that it uses a `try/catch/finally` block to instantiate, use, and dispose of a <xref:System.IO.StreamReader> object, and to handle any exceptions thrown by the <xref:System.IO.StreamReader> constructor and its <xref:System.IO.StreamReader.ReadToEnd%2A> method.</span></span> <span data-ttu-id="38614-124">`finally` メソッドを呼び出す前に <xref:System.IDisposable> を実装するオブジェクトが `null` でないことを <xref:System.IDisposable.Dispose%2A> ブロックのコードがチェックしていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="38614-124">Note that the code in the `finally` block checks that the object that implements <xref:System.IDisposable> isn't `null` before it calls the <xref:System.IDisposable.Dispose%2A> method.</span></span> <span data-ttu-id="38614-125">これを行わない場合、実行時に <xref:System.NullReferenceException> 例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="38614-125">Failure to do this can result in a <xref:System.NullReferenceException> exception at run time.</span></span>  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
<span data-ttu-id="38614-126">この基本パターンを利用できるのは、プログラミング言語で `using` ステートメントがサポートされていないが、<xref:System.IDisposable.Dispose%2A> メソッドを直接呼び出すことはできるため、`try/finally` ブロックの実装を選択した場合、または実装する必要がある場合です。</span><span class="sxs-lookup"><span data-stu-id="38614-126">You can follow this basic pattern if you choose to implement or must implement a `try/finally` block, because your programming language doesn't support a `using` statement but does allow direct calls to the <xref:System.IDisposable.Dispose%2A> method.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="38614-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="38614-127">See also</span></span>

<span data-ttu-id="38614-128">[アンマネージ リソースのクリーンアップ](../../../docs/standard/garbage-collection/unmanaged.md) </span><span class="sxs-lookup"><span data-stu-id="38614-128">[Cleaning Up Unmanaged Resources](../../../docs/standard/garbage-collection/unmanaged.md) </span></span>  
<span data-ttu-id="38614-129">[using ステートメント (C# リファレンス)](~/docs/csharp/language-reference/keywords/using-statement.md) </span><span class="sxs-lookup"><span data-stu-id="38614-129">[using Statement (C# Reference)](~/docs/csharp/language-reference/keywords/using-statement.md) </span></span>  
[<span data-ttu-id="38614-130">Using ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38614-130">Using Statement (Visual Basic)</span></span>](~/docs/visual-basic/language-reference/statements/using-statement.md)
