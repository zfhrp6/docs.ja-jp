---
title: "例外処理 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], handling
ms.assetid: b4e4ecf2-b907-4e58-891f-2563762258e9
caps.latest.revision: 24
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
ms.openlocfilehash: ab03e00a6b62d0c737c90fdb489be2a78f7ab6af
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="exception-handling-c-programming-guide"></a><span data-ttu-id="55570-102">例外処理 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="55570-102">Exception Handling (C# Programming Guide)</span></span>
<span data-ttu-id="55570-103">[try](../../../csharp/language-reference/keywords/try-catch.md) ブロックは、例外の影響を受ける可能性があるコードを区分化するために、 C# プログラマによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="55570-103">A [try](../../../csharp/language-reference/keywords/try-catch.md) block is used by C# programmers to partition code that might be affected by an exception.</span></span> <span data-ttu-id="55570-104">関連付けられた [catch](../../../csharp/language-reference/keywords/try-catch.md) ブロックは、スローされた例外を処理するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="55570-104">Associated [catch](../../../csharp/language-reference/keywords/try-catch.md) blocks are used to handle any resulting exceptions.</span></span> <span data-ttu-id="55570-105">[finally](../../../csharp/language-reference/keywords/try-finally.md) ブロックには、`try` ブロックで例外がスローされたかどうかにかかわらず実行されるコードが記述されます (`try` ブロックに割り当てられたリソースの解放など)。</span><span class="sxs-lookup"><span data-stu-id="55570-105">A [finally](../../../csharp/language-reference/keywords/try-finally.md) block contains code that is run regardless of whether or not an exception is thrown in the `try` block, such as releasing resources that are allocated in the `try` block.</span></span> <span data-ttu-id="55570-106">`try` ブロックには、1 つ以上の `catch` ブロック、`finally` ブロック、またはその両方が関連付けられる必要があります。</span><span class="sxs-lookup"><span data-stu-id="55570-106">A `try` block requires one or more associated `catch` blocks, or a `finally` block, or both.</span></span>  
  
 <span data-ttu-id="55570-107">次のコードは、`try-catch` ステートメント、`try-finally` ステートメント、および `try-catch-finally` ステートメントの例です。</span><span class="sxs-lookup"><span data-stu-id="55570-107">The following examples show a `try-catch` statement, a `try-finally` statement, and a `try-catch-finally` statement.</span></span>  
  
 <span data-ttu-id="55570-108">[!code-cs[csProgGuideExceptions#6](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="55570-108">[!code-cs[csProgGuideExceptions#6](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_1.cs)]</span></span>  
  
 <span data-ttu-id="55570-109">[!code-cs[csProgGuideExceptions#7](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="55570-109">[!code-cs[csProgGuideExceptions#7](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_2.cs)]</span></span>  
  
 <span data-ttu-id="55570-110">[!code-cs[csProgGuideExceptions#8](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="55570-110">[!code-cs[csProgGuideExceptions#8](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_3.cs)]</span></span>  
  
 <span data-ttu-id="55570-111">`try` ブロックに `catch` または `finally` ブロックがない場合は、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="55570-111">A `try` block without a `catch` or `finally` block causes a compiler error.</span></span>  
  
## <a name="catch-blocks"></a><span data-ttu-id="55570-112">catch ブロック</span><span class="sxs-lookup"><span data-stu-id="55570-112">Catch Blocks</span></span>  
 <span data-ttu-id="55570-113">`catch` ブロックでは、キャッチする例外の種類を指定できます。</span><span class="sxs-lookup"><span data-stu-id="55570-113">A `catch` block can specify the type of exception to catch.</span></span> <span data-ttu-id="55570-114">この型指定は、*例外フィルター*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="55570-114">The type specification is called an *exception filter*.</span></span> <span data-ttu-id="55570-115">例外の種類は、<xref:System.Exception> から派生している必要があります。</span><span class="sxs-lookup"><span data-stu-id="55570-115">The exception type should be derived from <xref:System.Exception>.</span></span> <span data-ttu-id="55570-116">一般に、`try` ブロックでスローされる可能性があるすべての例外の処理方法を把握している場合や、`catch` ブロックの末尾に [throw](../../../csharp/language-reference/keywords/throw.md) ステートメントを記述している場合を除いては、例外フィルターとして <xref:System.Exception> を指定することは避けてください。</span><span class="sxs-lookup"><span data-stu-id="55570-116">In general, do not specify <xref:System.Exception> as the exception filter unless either you know how to handle all exceptions that might be thrown in the `try` block, or you have included a [throw](../../../csharp/language-reference/keywords/throw.md) statement at the end of your `catch` block.</span></span>  
  
 <span data-ttu-id="55570-117">複数の `catch` ブロックに異なる例外フィルターが含まれている場合は、それらを連結することができます。</span><span class="sxs-lookup"><span data-stu-id="55570-117">Multiple `catch` blocks with different exception filters can be chained together.</span></span> <span data-ttu-id="55570-118">`catch` ブロックはコード内で上から下に評価されますが、スローされた各例外に対して実行される `catch` ブロックは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="55570-118">The `catch` blocks are evaluated from top to bottom in your code, but only one `catch` block is executed for each exception that is thrown.</span></span> <span data-ttu-id="55570-119">スローされた例外の厳密な型か、その基底クラスを指定する最初の `catch` ブロックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="55570-119">The first `catch` block that specifies the exact type or a base class of the thrown exception is executed.</span></span> <span data-ttu-id="55570-120">一致する例外フィルターを指定した `catch` ブロックがない場合は、フィルターのない `catch` ブロックが選択されます (それがステートメント内に存在する場合)。</span><span class="sxs-lookup"><span data-stu-id="55570-120">If no `catch` block specifies a matching exception filter, a `catch` block that does not have a filter is selected, if one is present in the statement.</span></span> <span data-ttu-id="55570-121">最初に配置する `catch` ブロックでは、最も具体的な (つまり、最終派生の) 例外の種類を指定することが重要です。</span><span class="sxs-lookup"><span data-stu-id="55570-121">It is important to position `catch` blocks with the most specific (that is, the most derived) exception types first.</span></span>  
  
 <span data-ttu-id="55570-122">次の条件に該当する場合は、例外をキャッチする必要があります。</span><span class="sxs-lookup"><span data-stu-id="55570-122">You should catch exceptions when the following conditions are true:</span></span>  
  
-   <span data-ttu-id="55570-123">例外がスローされる理由を十分に理解していて、かつ特定の回復手段を実装できる (<xref:System.IO.FileNotFoundException> オブジェクトをキャッチした場合に、ユーザーに新しいファイル名を入力するよう求めるなど)。</span><span class="sxs-lookup"><span data-stu-id="55570-123">You have a good understanding of why the exception might be thrown, and you can implement a specific recovery, such as prompting the user to enter a new file name when you catch a <xref:System.IO.FileNotFoundException> object.</span></span>  
  
-   <span data-ttu-id="55570-124">より具体的な例外を新規に作成し、スローできる。</span><span class="sxs-lookup"><span data-stu-id="55570-124">You can create and throw a new, more specific exception.</span></span>  
  
     <span data-ttu-id="55570-125">[!code-cs[csProgGuideExceptions#9](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="55570-125">[!code-cs[csProgGuideExceptions#9](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_4.cs)]</span></span>  
  
-   <span data-ttu-id="55570-126">例外を追加処理に渡す前に、その例外を部分的に処理する必要がある。</span><span class="sxs-lookup"><span data-stu-id="55570-126">You want to partially handle an exception before passing it on for additional handling.</span></span> <span data-ttu-id="55570-127">次の例では、例外を再スローする前に、エラー ログにエントリを追加する目的で `catch` ブロックが使用されています。</span><span class="sxs-lookup"><span data-stu-id="55570-127">In the following example, a `catch` block is used to add an entry to an error log before re-throwing the exception.</span></span>  
  
     <span data-ttu-id="55570-128">[!code-cs[csProgGuideExceptions#10](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="55570-128">[!code-cs[csProgGuideExceptions#10](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_5.cs)]</span></span>  
  
## <a name="finally-blocks"></a><span data-ttu-id="55570-129">Finally ブロック</span><span class="sxs-lookup"><span data-stu-id="55570-129">Finally Blocks</span></span>  
 <span data-ttu-id="55570-130">`finally` ブロックでは、`try` ブロックで実行されるアクションをクリーンアップすることができます。</span><span class="sxs-lookup"><span data-stu-id="55570-130">A `finally` block enables you to clean up actions that are performed in a `try` block.</span></span> <span data-ttu-id="55570-131">`finally` ブロック (存在する場合) は、最後 (`try` ブロックおよび一致する `catch` ブロックの後) に実行されます。</span><span class="sxs-lookup"><span data-stu-id="55570-131">If present, the `finally` block executes last, after the `try` block and any matched `catch` block.</span></span> <span data-ttu-id="55570-132">`finally` ブロックは、例外がスローされたかどうかや、例外の種類に一致する `catch` ブロックが見つかったかどうかにかかわらず、常に実行されます。</span><span class="sxs-lookup"><span data-stu-id="55570-132">A `finally` block always runs, regardless of whether an exception is thrown or a `catch` block matching the exception type is found.</span></span>  
  
 <span data-ttu-id="55570-133">`finally` ブロックは、ランタイム内のガベージ コレクターによってオブジェクトがファイナライズされるのを待つことなく、ファイル ストリーム、データベース接続、グラフィックス ハンドルなどのリソースを解放するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="55570-133">The `finally` block can be used to release resources such as file streams, database connections, and graphics handles without waiting for the garbage collector in the runtime to finalize the objects.</span></span> <span data-ttu-id="55570-134">詳しくは、「[using ステートメント](../../../csharp/language-reference/keywords/using-statement.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="55570-134">See [using Statement](../../../csharp/language-reference/keywords/using-statement.md) for more information.</span></span>  
  
 <span data-ttu-id="55570-135">次の例では、`try` ブロックで開かれたファイルを閉じるために `finally` ブロックが使用されています。</span><span class="sxs-lookup"><span data-stu-id="55570-135">In the following example, the `finally` block is used to close a file that is opened in the `try` block.</span></span> <span data-ttu-id="55570-136">ファイルを閉じる前に、ファイル ハンドルの状態が確認されています。</span><span class="sxs-lookup"><span data-stu-id="55570-136">Notice that the state of the file handle is checked before the file is closed.</span></span> <span data-ttu-id="55570-137">`try` ブロックがファイルを開けなかった場合は、ファイル ハンドルの値が `null` のままになり、`finally` ブロックはファイルを閉じようとしません。</span><span class="sxs-lookup"><span data-stu-id="55570-137">If the `try` block cannot open the file, the file handle still has the value `null` and the `finally` block does not try to close it.</span></span> <span data-ttu-id="55570-138">`try` ブロックでファイルが正常に開かれた場合は、開かれたファイルを `finally` ブロックが閉じます。</span><span class="sxs-lookup"><span data-stu-id="55570-138">Alternatively, if the file is opened successfully in the `try` block, the `finally` block closes the open file.</span></span>  
  
 <span data-ttu-id="55570-139">[!code-cs[csProgGuideExceptions#11](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="55570-139">[!code-cs[csProgGuideExceptions#11](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_6.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="55570-140">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="55570-140">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="55570-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="55570-141">See Also</span></span>  
 <span data-ttu-id="55570-142">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="55570-142">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="55570-143">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="55570-143">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="55570-144">[例外と例外処理](../../../csharp/programming-guide/exceptions/index.md) </span><span class="sxs-lookup"><span data-stu-id="55570-144">[Exceptions and Exception Handling](../../../csharp/programming-guide/exceptions/index.md) </span></span>  
 <span data-ttu-id="55570-145">[try-catch](../../../csharp/language-reference/keywords/try-catch.md) </span><span class="sxs-lookup"><span data-stu-id="55570-145">[try-catch](../../../csharp/language-reference/keywords/try-catch.md) </span></span>  
 <span data-ttu-id="55570-146">[try-finally](../../../csharp/language-reference/keywords/try-finally.md) </span><span class="sxs-lookup"><span data-stu-id="55570-146">[try-finally](../../../csharp/language-reference/keywords/try-finally.md) </span></span>  
 <span data-ttu-id="55570-147">[try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md) </span><span class="sxs-lookup"><span data-stu-id="55570-147">[try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md) </span></span>  
 [<span data-ttu-id="55570-148">using ステートメント</span><span class="sxs-lookup"><span data-stu-id="55570-148">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)

