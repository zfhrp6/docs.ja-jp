---
title: "when (C# リファレンス)"
ms.date: 2017-03-07
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- when_CSharpKeyword
- when
dev_langs:
- CSharp
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
caps.latest.revision: 30
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
ms.sourcegitcommit: 9ad2eff6eb527f00ce23f463e811aa748def62d0
ms.openlocfilehash: c391c6de51d41577d61278f43d58fade5b7c139f
ms.contentlocale: ja-jp
ms.lasthandoff: 08/11/2017

---
 # <a name="when-c-reference"></a><span data-ttu-id="b7f68-102">when (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="b7f68-102">when (C# Reference)</span></span>

<span data-ttu-id="b7f68-103">コンテキスト キーワード `when` は、次の 2 つのコンテキストでフィルター条件を指定するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="b7f68-103">You can use the `when` contextual keyword to specify a filter condition in two contexts:</span></span>

- <span data-ttu-id="b7f68-104">[try/catch](try-catch.md) または [try/catch/finally](try-catch-finally.md) ブロックの `catch` ステートメント。</span><span class="sxs-lookup"><span data-stu-id="b7f68-104">In the `catch` statement of a [try/catch](try-catch.md) or [try/catch/finally](try-catch-finally.md) block.</span></span>
- <span data-ttu-id="b7f68-105">[switch](switch.md) ステートメントの `case` ラベル。</span><span class="sxs-lookup"><span data-stu-id="b7f68-105">In the `case` label of a [switch](switch.md) statement.</span></span>

## <a name="when-in-a-catch-statement"></a><span data-ttu-id="b7f68-106">`catch` ステートメントでの `when`</span><span class="sxs-lookup"><span data-stu-id="b7f68-106">`when` in a `catch` statement</span></span>

<span data-ttu-id="b7f68-107">C# 6 から、`When` を `catch` ステートメントで使用して、特定の例外のハンドラーを実行するために true になる必要がある条件を指定できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="b7f68-107">Starting with C# 6, `When` can be used in a `catch` statement to specify a condition that must be true for the handler for a specific exception to execute.</span></span> <span data-ttu-id="b7f68-108">構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b7f68-108">Its syntax is:</span></span>

```csharp
catch ExceptionType [e] when (expr)
```
<span data-ttu-id="b7f68-109">*expr* の箇所には、ブール値に評価される式を指定します。</span><span class="sxs-lookup"><span data-stu-id="b7f68-109">where *expr* is an expression that evaluates to a Boolean value.</span></span> <span data-ttu-id="b7f68-110">`true` が返された場合は、例外ハンドラーが実行されます。`false` の場合は実行されません。</span><span class="sxs-lookup"><span data-stu-id="b7f68-110">If it returns `true`, the exception handler executes; if `false`, it does not.</span></span> 

<span data-ttu-id="b7f68-111">次の例では、`when` キーワードを使用し、例外メッセージのテキストに応じて、@System.Net.HttpRequestException のハンドラーが条件付きで実行されるようにしています。</span><span class="sxs-lookup"><span data-stu-id="b7f68-111">The following example uses the `when` keyword to conditionally execute handlers for an @System.Net.HttpRequestException depending on the text of the exception message.</span></span>

 <span data-ttu-id="b7f68-112">[!code-cs[when-with-catch](../../../../samples/snippets/csharp/language-reference/keywords/when/catch.cs)]</span><span class="sxs-lookup"><span data-stu-id="b7f68-112">[!code-cs[when-with-catch](../../../../samples/snippets/csharp/language-reference/keywords/when/catch.cs)]</span></span>  
  
## <a name="when-in-a-switch-statement"></a><span data-ttu-id="b7f68-113">`switch` ステートメントでの `when`</span><span class="sxs-lookup"><span data-stu-id="b7f68-113">`when` in a `switch` statement</span></span>

<span data-ttu-id="b7f68-114">7 以降では、`case` ラベルが相互に排他的である必要がなくなり、`switch` ステートメントでの `case` ラベルの表示順序によって、実行される switch ブロックを決定できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="b7f68-114">Starting with 7, `case` labels no longer need be mutually exclusive, and the order in which `case` labels appear in a `switch` statement can determine which switch block executes.</span></span> <span data-ttu-id="b7f68-115">`when` キーワードを使用すると、フィルター条件が true である場合にのみ、関連付けられた case ラベルも true になるフィルター条件を指定できます。</span><span class="sxs-lookup"><span data-stu-id="b7f68-115">The `when` keyword can be used to specify a filter condition that causes its associated case label to be true only if the filter condition is also true.</span></span> <span data-ttu-id="b7f68-116">構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b7f68-116">Its syntax is:</span></span>

```csharp
case (expr) when (when-condition):
```
<span data-ttu-id="b7f68-117">*expr* の箇所には、match 式と比較される定数パターンまたは型パターンを指定し、*when-condition* の箇所には、任意のブール式を指定します。</span><span class="sxs-lookup"><span data-stu-id="b7f68-117">where *expr* is a constant pattern or type pattern that is compared to the match expression, and *when-condition* is any Boolean expression.</span></span> 

<span data-ttu-id="b7f68-118">次の例では、`when` キーワードを使用して、面積が 0 の `Shape` オブジェクトに対するテストと、面積が 0 より大きい各種の `Shape` オブジェクトに対するテストを実行しています。</span><span class="sxs-lookup"><span data-stu-id="b7f68-118">The following example uses the `when` keyword to test for `Shape` objects that have an area of zero, as well as to test for a variety of `Shape` objects that have an area greater than zero.</span></span> 

 <span data-ttu-id="b7f68-119">[!code-cs[when-with-case#1](../../../../samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="b7f68-119">[!code-cs[when-with-case#1](../../../../samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="b7f68-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7f68-120">See also</span></span> 
  [<span data-ttu-id="b7f68-121">switch ステートメント</span><span class="sxs-lookup"><span data-stu-id="b7f68-121">switch statement</span></span>](switch.md)  
  [<span data-ttu-id="b7f68-122">try/catch ステートメント</span><span class="sxs-lookup"><span data-stu-id="b7f68-122">try/catch statement</span></span>](try-catch.md)  
  [<span data-ttu-id="b7f68-123">try/catch/finally ステートメント</span><span class="sxs-lookup"><span data-stu-id="b7f68-123">try/catch/finally statement</span></span>](try-catch-finally.md) 


