---
title: "クエリ式の例外の処理"
description: "クエリ式の例外を処理する方法。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 2bf0c397-13fb-4f68-bc2b-531c6c88a167
ms.openlocfilehash: 376bd461bfeb51653471fd374a2215aa15872976
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="handle-exceptions-in-query-expressions"></a><span data-ttu-id="52908-104">クエリ式の例外の処理</span><span class="sxs-lookup"><span data-stu-id="52908-104">Handle exceptions in query expressions</span></span>

<span data-ttu-id="52908-105">クエリ式のコンテキストで任意のメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="52908-105">It is possible to call any method in the context of a query expression.</span></span> <span data-ttu-id="52908-106">ただし、データ ソースのコンテンツが変更されたり例外がスローされたりするなどの副作用が生じる可能性のあるクエリ式では、メソッドを呼び出さないようにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="52908-106">However, we recommend that you avoid calling any method in a query expression that can create a side effect such as modifying the contents of the data source or throwing an exception.</span></span> <span data-ttu-id="52908-107">この例では、クエリ式でメソッドを呼び出すときに、例外処理に関する .NET Framework の全般的なガイドラインに違反することなく例外の発生を避ける方法を示します。</span><span class="sxs-lookup"><span data-stu-id="52908-107">This example shows how to avoid raising exceptions when you call methods in a query expression without violating the general .NET Framework guidelines on exception handling.</span></span> <span data-ttu-id="52908-108">ガイドラインでは、特定のコンテキストで特定の例外がスローされる理由がわかっているときにその例外をキャッチすることは認められています。</span><span class="sxs-lookup"><span data-stu-id="52908-108">Those guidelines state that it is acceptable to catch a specific exception when you understand why it will be thrown in a given context.</span></span> <span data-ttu-id="52908-109">詳細については、「[例外の推奨事項](../../standard/exceptions/best-practices-for-exceptions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52908-109">For more information, see [Best Practices for Exceptions](../../standard/exceptions/best-practices-for-exceptions.md).</span></span>  
  
 <span data-ttu-id="52908-110">最後の例では、クエリの実行中に例外をスローする必要がある場合の処理方法を示します。</span><span class="sxs-lookup"><span data-stu-id="52908-110">The final example shows how to handle those cases when you must throw an exception during execution of a query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52908-111">例</span><span class="sxs-lookup"><span data-stu-id="52908-111">Example</span></span>  

 <span data-ttu-id="52908-112">次の例では、例外処理コードをクエリ式の外側に移動する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="52908-112">The following example shows how to move exception handling code outside a query expression.</span></span> <span data-ttu-id="52908-113">この方法は、メソッドがクエリのローカル変数に依存しない場合にのみ可能です。</span><span class="sxs-lookup"><span data-stu-id="52908-113">This is only possible when the method does not depend on any variables local to the query.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#10](../../../samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="52908-114">例</span><span class="sxs-lookup"><span data-stu-id="52908-114">Example</span></span> 

 <span data-ttu-id="52908-115">場合によっては、クエリ内からスローされる例外に対する最適な応答は、クエリの実行をすぐに停止することです。</span><span class="sxs-lookup"><span data-stu-id="52908-115">In some cases, the best response to an exception that is thrown from within a query might be to stop the query execution immediately.</span></span> <span data-ttu-id="52908-116">次の例では、クエリ本体の内部からスローされる例外を処理する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="52908-116">The following example shows how to handle exceptions that might be thrown from inside a query body.</span></span> <span data-ttu-id="52908-117">`SomeMethodThatMightThrow` で、クエリの実行を停止することが必要な例外が発生する可能性があるとします。</span><span class="sxs-lookup"><span data-stu-id="52908-117">Assume that `SomeMethodThatMightThrow` can potentially cause an exception that requires the query execution to stop.</span></span>  
  
 <span data-ttu-id="52908-118">`try` ブロックは `foreach` ループを囲み、クエリ自体を囲むのではありません。</span><span class="sxs-lookup"><span data-stu-id="52908-118">Note that the `try` block encloses the `foreach` loop, and not the query itself.</span></span> <span data-ttu-id="52908-119">その理由は、`foreach` ループがクエリの実際の実行ポイントであるためです。</span><span class="sxs-lookup"><span data-stu-id="52908-119">This is because the `foreach` loop is the point at which the query is actually executed.</span></span> <span data-ttu-id="52908-120">詳細については、「[LINQ クエリの概要](../programming-guide/concepts/linq/introduction-to-linq-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52908-120">For more information, see [Introduction to LINQ queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!code-csharp[csProgGuideLINQ#12](../../../samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_2.cs)]  
  

## <a name="see-also"></a><span data-ttu-id="52908-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="52908-121">See Also</span></span>  
 [<span data-ttu-id="52908-122">LINQ クエリ式</span><span class="sxs-lookup"><span data-stu-id="52908-122">LINQ query expressions</span></span>](index.md)
