---
title: "方法: finally を使用してクリーンアップ コードを実行する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
caps.latest.revision: 21
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
ms.openlocfilehash: b1f7bccacf20a9322f4de75740cdc34b4a97fa4c
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a><span data-ttu-id="48a16-102">方法: finally を使用してクリーンアップ コードを実行する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="48a16-102">How to: Execute Cleanup Code Using finally (C# Programming Guide)</span></span>
<span data-ttu-id="48a16-103">`finally` ステートメントの目的は、例外がスローされた場合でも、オブジェクト (一般に外部リソースを保持しているオブジェクト) に対して必要なクリーンアップをすぐに実行できるようにすることです。</span><span class="sxs-lookup"><span data-stu-id="48a16-103">The purpose of a `finally` statement is to ensure that the necessary cleanup of objects, usually objects that are holding external resources, occurs immediately, even if an exception is thrown.</span></span> <span data-ttu-id="48a16-104">次のように、共通言語ランタイムによってオブジェクトがガベージ コレクションされるまで待機するのではなく、オブジェクトを使用した後すぐに <xref:System.IO.FileStream> で <xref:System.IO.Stream.Close%2A> を呼び出すというのも、このようなクリーンアップの一例です。</span><span class="sxs-lookup"><span data-stu-id="48a16-104">One example of such cleanup is calling <xref:System.IO.Stream.Close%2A> on a <xref:System.IO.FileStream> immediately after use instead of waiting for the object to be garbage collected by the common language runtime, as follows:</span></span>  
  
 <span data-ttu-id="48a16-105">[!code-cs[csProgGuideExceptions#16](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="48a16-105">[!code-cs[csProgGuideExceptions#16](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="48a16-106">例</span><span class="sxs-lookup"><span data-stu-id="48a16-106">Example</span></span>  
 <span data-ttu-id="48a16-107">上のコードを `try-catch-finally` ステートメントに変えるには、次のようにクリーンアップ コードを作業コードから切り離します。</span><span class="sxs-lookup"><span data-stu-id="48a16-107">To turn the previous code into a `try-catch-finally` statement, the cleanup code is separated from the working code, as follows.</span></span>  
  
 <span data-ttu-id="48a16-108">[!code-cs[csProgGuideExceptions#17](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="48a16-108">[!code-cs[csProgGuideExceptions#17](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_2.cs)]</span></span>  
  
 <span data-ttu-id="48a16-109">`try` ブロック内では `OpenWrite()` 呼び出しの前のどの時点でも例外が発生する可能性があります。また、`OpenWrite()` 呼び出し自体が失敗する可能性もあります。そのため、ファイルを閉じようとしたときに、そのファイルが開いているという保証はありません。</span><span class="sxs-lookup"><span data-stu-id="48a16-109">Because an exception can occur at any time within the `try` block before the `OpenWrite()` call, or the `OpenWrite()` call itself could fail, we are not guaranteed that the file is open when we try to close it.</span></span> <span data-ttu-id="48a16-110">`finally` ブロックでは、<xref:System.IO.Stream.Close%2A> メソッドを呼び出す前に、<xref:System.IO.FileStream> オブジェクトが `null` でないことを確認するチェックが追加されます。</span><span class="sxs-lookup"><span data-stu-id="48a16-110">The `finally` block adds a check to make sure that the <xref:System.IO.FileStream> object is not `null` before you call the <xref:System.IO.Stream.Close%2A> method.</span></span> <span data-ttu-id="48a16-111">この `null` チェックがないと、`finally` ブロックからその <xref:System.NullReferenceException> がスローされる可能性がありますが、`finally` ブロックにおける例外のスローはできるだけ回避する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48a16-111">Without the `null` check, the `finally` block could throw its own <xref:System.NullReferenceException>, but throwing exceptions in `finally` blocks should be avoided if it is possible.</span></span>  
  
 <span data-ttu-id="48a16-112">データベース接続も、`finally` ブロックで閉じられる対象になります。</span><span class="sxs-lookup"><span data-stu-id="48a16-112">A database connection is another good candidate for being closed in a `finally` block.</span></span> <span data-ttu-id="48a16-113">データベース サーバーで許可される接続数は限られていることがあるため、データベース接続はできるだけ早く閉じる必要があります。</span><span class="sxs-lookup"><span data-stu-id="48a16-113">Because the number of connections allowed to a database server is sometimes limited, you should close database connections as quickly as possible.</span></span> <span data-ttu-id="48a16-114">接続を閉じる前に例外がスローされる場合も、ガベージ コレクションを待機するより、`finally` ブロックを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="48a16-114">If an exception is thrown before you can close your connection, this is another case where using the `finally` block is better than waiting for garbage collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48a16-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="48a16-115">See Also</span></span>  
 <span data-ttu-id="48a16-116">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="48a16-116">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="48a16-117">[例外と例外処理](../../../csharp/programming-guide/exceptions/index.md) </span><span class="sxs-lookup"><span data-stu-id="48a16-117">[Exceptions and Exception Handling](../../../csharp/programming-guide/exceptions/index.md) </span></span>  
 <span data-ttu-id="48a16-118">[例外処理](../../../csharp/programming-guide/exceptions/exception-handling.md) </span><span class="sxs-lookup"><span data-stu-id="48a16-118">[Exception Handling](../../../csharp/programming-guide/exceptions/exception-handling.md) </span></span>  
 <span data-ttu-id="48a16-119">[using ステートメント](../../../csharp/language-reference/keywords/using-statement.md) </span><span class="sxs-lookup"><span data-stu-id="48a16-119">[using Statement](../../../csharp/language-reference/keywords/using-statement.md) </span></span>  
 <span data-ttu-id="48a16-120">[try-catch](../../../csharp/language-reference/keywords/try-catch.md) </span><span class="sxs-lookup"><span data-stu-id="48a16-120">[try-catch](../../../csharp/language-reference/keywords/try-catch.md) </span></span>  
 <span data-ttu-id="48a16-121">[try-finally](../../../csharp/language-reference/keywords/try-finally.md) </span><span class="sxs-lookup"><span data-stu-id="48a16-121">[try-finally](../../../csharp/language-reference/keywords/try-finally.md) </span></span>  
 [<span data-ttu-id="48a16-122">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="48a16-122">try-catch-finally</span></span>](../../../csharp/language-reference/keywords/try-catch-finally.md)

