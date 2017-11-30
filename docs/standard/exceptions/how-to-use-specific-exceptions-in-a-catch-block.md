---
title: "方法 : catch ブロックで特定の例外を使用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- try/catch blocks
- catch blocks
ms.assetid: 12af9ff3-8587-4f31-90cf-6c2244e0fdae
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 94e5840ca4bb5f871a0ae91f53404de6a60d749d
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2017
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a><span data-ttu-id="8e8cd-102">特定の例外を catch ブロックで使用する方法</span><span class="sxs-lookup"><span data-stu-id="8e8cd-102">How to use specific exceptions in a catch block</span></span>

<span data-ttu-id="8e8cd-103">一般に、適切なプログラミング、basic を使用するのではなく、特定の種類の例外をキャッチする方法は`catch`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="8e8cd-103">In general, it's good programming practice to catch a specific type of exception rather than use a basic `catch` statement.</span></span>

<span data-ttu-id="8e8cd-104">例外が発生すると、スタックに渡され、各 catch ブロックが処理する機会を与えられます。</span><span class="sxs-lookup"><span data-stu-id="8e8cd-104">When an exception occurs, it is passed up the stack and each catch block is given the opportunity to handle it.</span></span> <span data-ttu-id="8e8cd-105">catch ステートメントの順序が重要です。</span><span class="sxs-lookup"><span data-stu-id="8e8cd-105">The order of catch statements is important.</span></span> <span data-ttu-id="8e8cd-106">一般的な例外 catch ブロックまたはコンパイラがエラーを発行する前に、特定の例外を対象とした catch ブロックを配置します。</span><span class="sxs-lookup"><span data-stu-id="8e8cd-106">Put catch blocks targeted to specific exceptions before a general exception catch block or the compiler might issue an error.</span></span> <span data-ttu-id="8e8cd-107">適切な catch ブロックは、例外の種類を catch ブロックで指定された例外の名前に一致させることで決まります。</span><span class="sxs-lookup"><span data-stu-id="8e8cd-107">The proper catch block is determined by matching the type of the exception to the name of the exception specified in the catch block.</span></span> <span data-ttu-id="8e8cd-108">特定の catch ブロックがない場合は、汎用 catch ブロック (ある場合) によってキャッチされます。</span><span class="sxs-lookup"><span data-stu-id="8e8cd-108">If there is no specific catch block, the exception is caught by a general catch block, if one exists.</span></span>

<span data-ttu-id="8e8cd-109">次のコード例では、`try`/`catch` ブロックを使用して <xref:System.InvalidCastException> をキャッチします。</span><span class="sxs-lookup"><span data-stu-id="8e8cd-109">The following code example uses a `try`/`catch` block to catch an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="8e8cd-110">サンプルでは、1 つのプロパティ、従業員レベル (`Emlevel`) を使用して、`Employee` と呼ばれるクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="8e8cd-110">The sample creates a class called `Employee` with a single property, employee level (`Emlevel`).</span></span> <span data-ttu-id="8e8cd-111">メソッド `PromoteEmployee` は、オブジェクトを受け取って、従業員レベルをインクリメントします。</span><span class="sxs-lookup"><span data-stu-id="8e8cd-111">A method, `PromoteEmployee`, takes an object and increments the employee level.</span></span> <span data-ttu-id="8e8cd-112"><xref:System.DateTime> インスタンスが `PromoteEmployee` メソッドに渡されたとき、<xref:System.InvalidCastException> が発生します。</span><span class="sxs-lookup"><span data-stu-id="8e8cd-112">An <xref:System.InvalidCastException> occurs when a <xref:System.DateTime> instance is passed to the `PromoteEmployee` method.</span></span>

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)] 

## <a name="see-also"></a><span data-ttu-id="8e8cd-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="8e8cd-113">See Also</span></span>  
[<span data-ttu-id="8e8cd-114">例外</span><span class="sxs-lookup"><span data-stu-id="8e8cd-114">Exceptions</span></span>](index.md)
