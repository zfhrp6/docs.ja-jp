---
title: "例外の使用 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], about exceptions
ms.assetid: 71472c62-320a-470a-97d2-67995180389d
caps.latest.revision: 15
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
ms.openlocfilehash: 96fc082d135d38f521429de7b4e9a668773982ea
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="using-exceptions-c-programming-guide"></a><span data-ttu-id="bdc00-102">例外の使用 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="bdc00-102">Using Exceptions (C# Programming Guide)</span></span>
<span data-ttu-id="bdc00-103">C# では、例外と呼ばれるメカニズムを使用して、プログラムの実行時に発生したエラーがプログラムに伝えられます。</span><span class="sxs-lookup"><span data-stu-id="bdc00-103">In C#, errors in the program at run time are propagated through the program by using a mechanism called exceptions.</span></span> <span data-ttu-id="bdc00-104">例外は、エラーが発生したコードによってスローされ、エラーを修正できるコードによってキャッチされます。</span><span class="sxs-lookup"><span data-stu-id="bdc00-104">Exceptions are thrown by code that encounters an error and caught by code that can correct the error.</span></span> <span data-ttu-id="bdc00-105">例外をスローできるのは、.NET Framework 共通言語ランタイム (CLR) か、プログラム内のコードです。</span><span class="sxs-lookup"><span data-stu-id="bdc00-105">Exceptions can be thrown by the .NET Framework common language runtime (CLR) or by code in a program.</span></span> <span data-ttu-id="bdc00-106">スローされた例外は、例外の `catch` ステートメントが見つかるまで呼び出し履歴をさかのぼります。</span><span class="sxs-lookup"><span data-stu-id="bdc00-106">Once an exception is thrown, it propagates up the call stack until a `catch` statement for the exception is found.</span></span> <span data-ttu-id="bdc00-107">キャッチされない例外は、システムが提供する汎用の例外ハンドラーによって処理されます。このとき、ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="bdc00-107">Uncaught exceptions are handled by a generic exception handler provided by the system that displays a dialog box.</span></span>  
  
 <span data-ttu-id="bdc00-108">例外は、<xref:System.Exception> から派生したクラスによって表されます。</span><span class="sxs-lookup"><span data-stu-id="bdc00-108">Exceptions are represented by classes derived from <xref:System.Exception>.</span></span> <span data-ttu-id="bdc00-109">このクラスは例外の型を識別し、例外に関する詳細情報が含まれたプロパティを保持します。</span><span class="sxs-lookup"><span data-stu-id="bdc00-109">This class identifies the type of exception and contains properties that have details about the exception.</span></span> <span data-ttu-id="bdc00-110">例外をスローするには、例外の派生クラスのインスタンスを作成し、必要に応じて例外のプロパティを設定してから、`throw` キーワードを使用してオブジェクトをスローする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bdc00-110">Throwing an exception involves creating an instance of an exception-derived class, optionally configuring properties of the exception, and then throwing the object by using the `throw` keyword.</span></span> <span data-ttu-id="bdc00-111">例:</span><span class="sxs-lookup"><span data-stu-id="bdc00-111">For example:</span></span>  
  
 <span data-ttu-id="bdc00-112">[!code-cs[csProgGuideExceptions#1](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="bdc00-112">[!code-cs[csProgGuideExceptions#1](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_1.cs)]</span></span>  
  
 <span data-ttu-id="bdc00-113">例外がスローされると、ランタイムは、現在のステートメントが `try` ブロック内に存在するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="bdc00-113">After an exception is thrown, the runtime checks the current statement to see whether it is within a `try` block.</span></span> <span data-ttu-id="bdc00-114">存在する場合は、`try` ブロックに関連付けられている `catch` ブロックをチェックして、例外をキャッチできるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="bdc00-114">If it is, any `catch` blocks associated with the `try` block are checked to see whether they can catch the exception.</span></span> <span data-ttu-id="bdc00-115">通常は、この `Catch` ブロックによって例外の型が指定されます。`catch` ブロックの型が、例外または例外の基底クラスの型と一致する場合、`catch` ブロックはメソッドを処理できます。</span><span class="sxs-lookup"><span data-stu-id="bdc00-115">`Catch` blocks typically specify exception types; if the type of the `catch` block is the same type as the exception, or a base class of the exception, the `catch` block can handle the method.</span></span> <span data-ttu-id="bdc00-116">例:</span><span class="sxs-lookup"><span data-stu-id="bdc00-116">For example:</span></span>  
  
 <span data-ttu-id="bdc00-117">[!code-cs[csProgGuideExceptions#2](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="bdc00-117">[!code-cs[csProgGuideExceptions#2](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_2.cs)]</span></span>  
  
 <span data-ttu-id="bdc00-118">例外をスローするステートメントが `try` ブロックにない場合、または `try` ブロックにそのステートメントが含まれていても、対応する `catch` ブロックが存在しない場合は、ランタイムが呼び出し側のメソッドで `try` ステートメントと `catch` ブロックを探します。</span><span class="sxs-lookup"><span data-stu-id="bdc00-118">If the statement that throws an exception is not within a `try` block or if the `try` block that encloses it has no matching `catch` block, the runtime checks the calling method for a `try` statement and `catch` blocks.</span></span> <span data-ttu-id="bdc00-119">続けて、呼び出し履歴で、対応する `catch` ブロックを探します。</span><span class="sxs-lookup"><span data-stu-id="bdc00-119">The runtime continues up the calling stack, searching for a compatible `catch` block.</span></span> <span data-ttu-id="bdc00-120">`catch` ブロックが見つかり実行されると、その `catch` ブロックの後にある次のステートメントに制御が渡されます。</span><span class="sxs-lookup"><span data-stu-id="bdc00-120">After the `catch` block is found and executed, control is passed to the next statement after that `catch` block.</span></span>  
  
 <span data-ttu-id="bdc00-121">`try` ステートメントには、複数の `catch` ブロックを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="bdc00-121">A `try` statement can contain more than one `catch` block.</span></span> <span data-ttu-id="bdc00-122">例外を処理できる最初の `catch` ステートメントが実行され、その後の `catch` ステートメントは、対応していても無視されます。</span><span class="sxs-lookup"><span data-stu-id="bdc00-122">The first `catch` statement that can handle the exception is executed; any following `catch` statements, even if they are compatible, are ignored.</span></span> <span data-ttu-id="bdc00-123">そのため、catch ブロックは必ず特殊性が高いもの (または最も派生されたもの) から順に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bdc00-123">Therefore, catch blocks should always be ordered from most specific (or most-derived) to least specific.</span></span> <span data-ttu-id="bdc00-124">例:</span><span class="sxs-lookup"><span data-stu-id="bdc00-124">For example:</span></span>  
  
 <span data-ttu-id="bdc00-125">[!code-cs[csProgGuideExceptions#3](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="bdc00-125">[!code-cs[csProgGuideExceptions#3](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_3.cs)]</span></span>  
  
 <span data-ttu-id="bdc00-126">`catch` ブロックが実行される前に、ランタイムにより `finally` ブロックがチェックされます。</span><span class="sxs-lookup"><span data-stu-id="bdc00-126">Before the `catch` block is executed, the runtime checks for `finally` blocks.</span></span> <span data-ttu-id="bdc00-127">`Finally` ブロックを使用すると、中止された `try` ブロックによって残ることがある、あいまいな状態をクリーンアップできます。また、ランタイムのガベージ コレクターがオブジェクトを終了させるのを待たずに外部リソース (グラフィック ハンドル、データベース接続、ファイル ストリームなど) を解放することもできます。</span><span class="sxs-lookup"><span data-stu-id="bdc00-127">`Finally` blocks enable the programmer to clean up any ambiguous state that could be left over from an aborted `try` block, or to release any external resources (such as graphics handles, database connections or file streams) without waiting for the garbage collector in the runtime to finalize the objects.</span></span> <span data-ttu-id="bdc00-128">例:</span><span class="sxs-lookup"><span data-stu-id="bdc00-128">For example:</span></span>  
  
 <span data-ttu-id="bdc00-129">[!code-cs[csProgGuideExceptions#4](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="bdc00-129">[!code-cs[csProgGuideExceptions#4](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_4.cs)]</span></span>  
  
 <span data-ttu-id="bdc00-130">`WriteByte()` が例外をスローした場合は、`file.Close()` を呼び出さないと、ファイルを再度開こうとする 2 番目の `try` ブロックのコードが失敗し、ファイルはロックされたままになります。</span><span class="sxs-lookup"><span data-stu-id="bdc00-130">If `WriteByte()` threw an exception, the code in the second `try` block that tries to reopen the file would fail if `file.Close()` is not called, and the file would remain locked.</span></span> <span data-ttu-id="bdc00-131">例外がスローされても `finally` ブロックは実行されるため、上の例の `finally` ブロックではファイルを適切に閉じて、エラーを回避できます。</span><span class="sxs-lookup"><span data-stu-id="bdc00-131">Because `finally` blocks are executed even if an exception is thrown, the `finally` block in the previous example allows for the file to be closed correctly and helps avoid an error.</span></span>  
  
 <span data-ttu-id="bdc00-132">例外がスローされた後、対応する `catch` ブロックが呼び出し履歴に見つからない場合は、次のいずれかが発生します。</span><span class="sxs-lookup"><span data-stu-id="bdc00-132">If no compatible `catch` block is found on the call stack after an exception is thrown, one of three things occurs:</span></span>  
  
-   <span data-ttu-id="bdc00-133">例外がファイナライザーの内部で発生した場合、ファイナライザーは中止され、基本ファイナライザー (存在する場合) が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="bdc00-133">If the exception is within a finalizer, the finalizer is aborted and the base finalizer, if any, is called.</span></span>  
  
-   <span data-ttu-id="bdc00-134">呼び出し履歴に静的コンストラクターまたは静的フィールド初期化子が含まれている場合は、<xref:System.TypeInitializationException> がスローされ、新しい例外の <xref:System.Exception.InnerException%2A> プロパティに元の例外が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="bdc00-134">If the call stack contains a static constructor, or a static field initializer, a <xref:System.TypeInitializationException> is thrown, with the original exception assigned to the <xref:System.Exception.InnerException%2A> property of the new exception.</span></span>  
  
-   <span data-ttu-id="bdc00-135">スレッドの開始位置に到達すると、スレッドは終了します。</span><span class="sxs-lookup"><span data-stu-id="bdc00-135">If the start of the thread is reached, the thread is terminated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdc00-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="bdc00-136">See Also</span></span>  
 <span data-ttu-id="bdc00-137">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="bdc00-137">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="bdc00-138">例外と例外処理</span><span class="sxs-lookup"><span data-stu-id="bdc00-138">Exceptions and Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/index.md)

