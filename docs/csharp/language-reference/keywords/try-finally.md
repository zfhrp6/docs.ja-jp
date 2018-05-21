---
title: try-finally (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: 696eb531fe3e340f7fe0ae12483648119cf5a7eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="try-finally-c-reference"></a><span data-ttu-id="be552-102">try-finally (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="be552-102">try-finally (C# Reference)</span></span>
<span data-ttu-id="be552-103">`finally` ブロックを使用すると、[try](../../../csharp/language-reference/keywords/try-catch.md) ブロックで割り当てられたリソースをクリーンアップし、`try` ブロックで例外が発生してもコードを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="be552-103">By using a `finally` block, you can clean up any resources that are allocated in a [try](../../../csharp/language-reference/keywords/try-catch.md) block, and you can run code even if an exception occurs in the `try` block.</span></span> <span data-ttu-id="be552-104">通常、制御が `finally` ステートメントを離れると、`try` ブロックのステートメントが実行されます。</span><span class="sxs-lookup"><span data-stu-id="be552-104">Typically, the statements of a `finally` block run when control leaves a `try` statement.</span></span> <span data-ttu-id="be552-105">制御の移動は、`break` ステートメント、`continue` ステートメント、`goto` ステートメント、`return` またはステートメントの正常な実行の結果や、`try` ステートメントで生じた例外の反映の結果として生じます。</span><span class="sxs-lookup"><span data-stu-id="be552-105">The transfer of control can occur as a result of normal execution, of execution of a `break`, `continue`, `goto`, or `return` statement, or of propagation of an exception out of the `try` statement.</span></span>  
  
 <span data-ttu-id="be552-106">ハンドルされている例外では、関連する `finally` ブロックの実行が保証されます。</span><span class="sxs-lookup"><span data-stu-id="be552-106">Within a handled exception, the associated `finally` block is guaranteed to be run.</span></span> <span data-ttu-id="be552-107">ただし、例外がハンドルされていない場合、`finally` ブロックの実行は、例外のアンワインド操作のトリガー方法に依存します。</span><span class="sxs-lookup"><span data-stu-id="be552-107">However, if the exception is unhandled, execution of the `finally` block is dependent on how the exception unwind operation is triggered.</span></span> <span data-ttu-id="be552-108">つまり、コンピューターの設定に依存するということでもあります。</span><span class="sxs-lookup"><span data-stu-id="be552-108">That, in turn, is dependent on how your computer is set up.</span></span>
  
 <span data-ttu-id="be552-109">通常、ハンドルされていない例外によってアプリケーションが終了した場合、`finally` ブロックが実行されるかどうかは重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="be552-109">Usually, when an unhandled exception ends an application, whether or not the `finally` block is run is not important.</span></span> <span data-ttu-id="be552-110">ただし、このような状況でも実行する必要のあるステートメントが `finally` ブロックにある場合は、`try`-`finally` ステートメントに `catch` ブロックを追加するという方法があります。</span><span class="sxs-lookup"><span data-stu-id="be552-110">However, if you have statements in a `finally` block that must be run even in that situation, one solution is to add a `catch` block to the `try`-`finally` statement.</span></span> <span data-ttu-id="be552-111">または、`try`-`finally` ステートメントの `try` ブロックでスローされた例外があれば、コール スタックの上の方でキャッチすることもできます。</span><span class="sxs-lookup"><span data-stu-id="be552-111">Alternatively, you can catch the exception that might be thrown in the `try` block of a `try`-`finally` statement higher up the call stack.</span></span> <span data-ttu-id="be552-112">つまり、`try`-`finally` ステートメントが含まれているメソッドを呼び出すメソッド内でも、そのメソッドを呼び出すメソッド内でも、コール スタック内の任意のメソッド内でも、例外をキャッチできるということです。</span><span class="sxs-lookup"><span data-stu-id="be552-112">That is, you can catch the exception in the method that calls the method that contains the `try`-`finally` statement, or in the method that calls that method, or in any method in the call stack.</span></span> <span data-ttu-id="be552-113">例外がキャッチされない場合、`finally` ブロックの実行は、例外のアンワインド操作がオペレーティング システムによってトリガーされるかどうかに依存します。</span><span class="sxs-lookup"><span data-stu-id="be552-113">If the exception is not caught, execution of the `finally` block depends on whether the operating system chooses to trigger an exception unwind operation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be552-114">例</span><span class="sxs-lookup"><span data-stu-id="be552-114">Example</span></span>  
 <span data-ttu-id="be552-115">次の例では、無効な変換ステートメントによって `System.InvalidCastException` 例外が発生しています。</span><span class="sxs-lookup"><span data-stu-id="be552-115">In the following example, an invalid conversion statement causes a `System.InvalidCastException` exception.</span></span> <span data-ttu-id="be552-116">この例外はハンドルされていません。</span><span class="sxs-lookup"><span data-stu-id="be552-116">The exception is unhandled.</span></span>  
  
 [!code-csharp[csrefKeywordsExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_1.cs)]  
  
 <span data-ttu-id="be552-117">次の例では、コール スタックのずっと上の方のメソッド内で `TryCast` メソッドからの例外がキャッチされます。</span><span class="sxs-lookup"><span data-stu-id="be552-117">In the following example, an exception from the `TryCast` method is caught in a method farther up the call stack.</span></span>  
  
 [!code-csharp[csrefKeywordsExceptions#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_2.cs)]  
  
 <span data-ttu-id="be552-118">`finally` の詳細については、「[try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be552-118">For more information about `finally`, see [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).</span></span>  
  
 <span data-ttu-id="be552-119">C# には、<xref:System.IDisposable> オブジェクトに対して同様の機能を便利な構文で提供する [using ステートメント](../../../csharp/language-reference/keywords/using-statement.md)も含まれています。</span><span class="sxs-lookup"><span data-stu-id="be552-119">C# also contains the [using statement](../../../csharp/language-reference/keywords/using-statement.md), which provides similar functionality for <xref:System.IDisposable> objects in a convenient syntax.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="be552-120">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="be552-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="be552-121">参照</span><span class="sxs-lookup"><span data-stu-id="be552-121">See Also</span></span>  
 [<span data-ttu-id="be552-122">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="be552-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="be552-123">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="be552-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="be552-124">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="be552-124">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="be552-125">try、throw、catch ステートメント (C++)</span><span class="sxs-lookup"><span data-stu-id="be552-125">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)  
 [<span data-ttu-id="be552-126">例外処理ステートメント</span><span class="sxs-lookup"><span data-stu-id="be552-126">Exception Handling Statements</span></span>](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
 [<span data-ttu-id="be552-127">throw</span><span class="sxs-lookup"><span data-stu-id="be552-127">throw</span></span>](../../../csharp/language-reference/keywords/throw.md)  
 [<span data-ttu-id="be552-128">try-catch</span><span class="sxs-lookup"><span data-stu-id="be552-128">try-catch</span></span>](../../../csharp/language-reference/keywords/try-catch.md)  
 [<span data-ttu-id="be552-129">方法: 例外を明示的にスローする</span><span class="sxs-lookup"><span data-stu-id="be552-129">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
