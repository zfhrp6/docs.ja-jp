---
title: "try-finally (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- finally
- finally_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
caps.latest.revision: 25
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
ms.openlocfilehash: 88b9960b8c026d1fcd8eed1815ade57422cd2a15
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="try-finally-c-reference"></a><span data-ttu-id="ac689-102">try-finally (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="ac689-102">try-finally (C# Reference)</span></span>
<span data-ttu-id="ac689-103">`finally` ブロックを使用すると、[try](../../../csharp/language-reference/keywords/try-catch.md) ブロックで割り当てられたリソースをクリーンアップし、`try` ブロックで例外が発生してもコードを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="ac689-103">By using a `finally` block, you can clean up any resources that are allocated in a [try](../../../csharp/language-reference/keywords/try-catch.md) block, and you can run code even if an exception occurs in the `try` block.</span></span> <span data-ttu-id="ac689-104">通常、制御が `finally` ステートメントを離れると、`try` ブロックのステートメントが実行されます。</span><span class="sxs-lookup"><span data-stu-id="ac689-104">Typically, the statements of a `finally` block run when control leaves a `try` statement.</span></span> <span data-ttu-id="ac689-105">制御の移動は、`break` ステートメント、`continue` ステートメント、`goto` ステートメント、`return` またはステートメントの正常な実行の結果や、`try` ステートメントで生じた例外の反映の結果として生じます。</span><span class="sxs-lookup"><span data-stu-id="ac689-105">The transfer of control can occur as a result of normal execution, of execution of a `break`, `continue`, `goto`, or `return` statement, or of propagation of an exception out of the `try` statement.</span></span>  
  
 <span data-ttu-id="ac689-106">ハンドルされている例外では、関連する `finally` ブロックの実行が保証されます。</span><span class="sxs-lookup"><span data-stu-id="ac689-106">Within a handled exception, the associated `finally` block is guaranteed to be run.</span></span> <span data-ttu-id="ac689-107">ただし、例外がハンドルされていない場合、`finally` ブロックの実行は、例外のアンワインド操作のトリガー方法に依存します。</span><span class="sxs-lookup"><span data-stu-id="ac689-107">However, if the exception is unhandled, execution of the `finally` block is dependent on how the exception unwind operation is triggered.</span></span> <span data-ttu-id="ac689-108">つまり、コンピューターの設定に依存するということでもあります。</span><span class="sxs-lookup"><span data-stu-id="ac689-108">That, in turn, is dependent on how your computer is set up.</span></span> <span data-ttu-id="ac689-109">詳細については、「[CLR のハンドルされない例外の処理](http://go.microsoft.com/fwlink/?LinkId=128371)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac689-109">For more information, see [Unhandled Exception Processing in the CLR](http://go.microsoft.com/fwlink/?LinkId=128371).</span></span>  
  
 <span data-ttu-id="ac689-110">通常、ハンドルされていない例外によってアプリケーションが終了した場合、`finally` ブロックが実行されるかどうかは重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="ac689-110">Usually, when an unhandled exception ends an application, whether or not the `finally` block is run is not important.</span></span> <span data-ttu-id="ac689-111">ただし、このような状況でも実行する必要のあるステートメントが `finally` ブロックにある場合は、`try`-`finally` ステートメントに `catch` ブロックを追加するという方法があります。</span><span class="sxs-lookup"><span data-stu-id="ac689-111">However, if you have statements in a `finally` block that must be run even in that situation, one solution is to add a `catch` block to the `try`-`finally` statement.</span></span> <span data-ttu-id="ac689-112">または、`try`-`finally` ステートメントの `try` ブロックでスローされた例外があれば、コール スタックの上の方でキャッチすることもできます。</span><span class="sxs-lookup"><span data-stu-id="ac689-112">Alternatively, you can catch the exception that might be thrown in the `try` block of a `try`-`finally` statement higher up the call stack.</span></span> <span data-ttu-id="ac689-113">つまり、`try`-`finally` ステートメントが含まれているメソッドを呼び出すメソッド内でも、そのメソッドを呼び出すメソッド内でも、コール スタック内の任意のメソッド内でも、例外をキャッチできるということです。</span><span class="sxs-lookup"><span data-stu-id="ac689-113">That is, you can catch the exception in the method that calls the method that contains the `try`-`finally` statement, or in the method that calls that method, or in any method in the call stack.</span></span> <span data-ttu-id="ac689-114">例外がキャッチされない場合、`finally` ブロックの実行は、例外のアンワインド操作がオペレーティング システムによってトリガーされるかどうかに依存します。</span><span class="sxs-lookup"><span data-stu-id="ac689-114">If the exception is not caught, execution of the `finally` block depends on whether the operating system chooses to trigger an exception unwind operation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac689-115">例</span><span class="sxs-lookup"><span data-stu-id="ac689-115">Example</span></span>  
 <span data-ttu-id="ac689-116">次の例では、無効な変換ステートメントによって `System.InvalidCastException` 例外が発生しています。</span><span class="sxs-lookup"><span data-stu-id="ac689-116">In the following example, an invalid conversion statement causes a `System.InvalidCastException` exception.</span></span> <span data-ttu-id="ac689-117">この例外はハンドルされていません。</span><span class="sxs-lookup"><span data-stu-id="ac689-117">The exception is unhandled.</span></span>  
  
 <span data-ttu-id="ac689-118">[!code-cs[csrefKeywordsExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="ac689-118">[!code-cs[csrefKeywordsExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_1.cs)]</span></span>  
  
 <span data-ttu-id="ac689-119">次の例では、コール スタックのずっと上の方のメソッド内で `TryCast` メソッドからの例外がキャッチされます。</span><span class="sxs-lookup"><span data-stu-id="ac689-119">In the following example, an exception from the `TryCast` method is caught in a method farther up the call stack.</span></span>  
  
 <span data-ttu-id="ac689-120">[!code-cs[csrefKeywordsExceptions#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="ac689-120">[!code-cs[csrefKeywordsExceptions#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_2.cs)]</span></span>  
  
 <span data-ttu-id="ac689-121">`finally` の詳細については、「[try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac689-121">For more information about `finally`, see [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).</span></span>  
  
 <span data-ttu-id="ac689-122">C# には、<xref:System.IDisposable> オブジェクトに対して同様の機能を便利な構文で提供する [using ステートメント](../../../csharp/language-reference/keywords/using-statement.md)も含まれています。</span><span class="sxs-lookup"><span data-stu-id="ac689-122">C# also contains the [using statement](../../../csharp/language-reference/keywords/using-statement.md), which provides similar functionality for <xref:System.IDisposable> objects in a convenient syntax.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="ac689-123">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="ac689-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ac689-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="ac689-124">See Also</span></span>  
 <span data-ttu-id="ac689-125">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="ac689-125">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="ac689-126">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="ac689-126">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="ac689-127">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="ac689-127">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="ac689-128">[try、throw、catch ステートメント (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp) </span><span class="sxs-lookup"><span data-stu-id="ac689-128">[try, throw, and catch Statements (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp) </span></span>  
 <span data-ttu-id="ac689-129">[例外処理ステートメント](../../../csharp/language-reference/keywords/exception-handling-statements.md) </span><span class="sxs-lookup"><span data-stu-id="ac689-129">[Exception Handling Statements](../../../csharp/language-reference/keywords/exception-handling-statements.md) </span></span>  
 <span data-ttu-id="ac689-130">[throw](../../../csharp/language-reference/keywords/throw.md) </span><span class="sxs-lookup"><span data-stu-id="ac689-130">[throw](../../../csharp/language-reference/keywords/throw.md) </span></span>  
 <span data-ttu-id="ac689-131">[try-catch](../../../csharp/language-reference/keywords/try-catch.md) </span><span class="sxs-lookup"><span data-stu-id="ac689-131">[try-catch](../../../csharp/language-reference/keywords/try-catch.md) </span></span>  
 [<span data-ttu-id="ac689-132">方法: 例外を明示的にスローする</span><span class="sxs-lookup"><span data-stu-id="ac689-132">How to: Explicitly Throw Exceptions</span></span>](https://msdn.microsoft.com/library/xhcbs8fz)

