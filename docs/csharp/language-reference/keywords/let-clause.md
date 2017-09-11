---
title: "let 句 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- let_CSharpKeyword
- let
dev_langs:
- CSharp
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
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
ms.openlocfilehash: 37ec0cb0c8c374a0b5250d82e880c96696b5584a
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="let-clause-c-reference"></a><span data-ttu-id="e097a-102">let 句 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="e097a-102">let clause (C# Reference)</span></span>
<span data-ttu-id="e097a-103">クエリ式では、後続の句で使用するために、サブ式の結果を保存すると便利な場合があります。</span><span class="sxs-lookup"><span data-stu-id="e097a-103">In a query expression, it is sometimes useful to store the result of a sub-expression in order to use it in subsequent clauses.</span></span> <span data-ttu-id="e097a-104">`let` キーワードを使用してこれを行うことができます。これにより新しい範囲変数を作成し、指定した式の結果でそれを初期化します。</span><span class="sxs-lookup"><span data-stu-id="e097a-104">You can do this with the `let` keyword, which creates a new range variable and initializes it with the result of the expression you supply.</span></span> <span data-ttu-id="e097a-105">値で初期化されると、範囲変数を使用して別の値を格納することはできません。</span><span class="sxs-lookup"><span data-stu-id="e097a-105">Once initialized with a value, the range variable cannot be used to store another value.</span></span> <span data-ttu-id="e097a-106">ただし、範囲変数がクエリ可能型を保持している場合、クエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="e097a-106">However, if the range variable holds a queryable type, it can be queried.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e097a-107">例</span><span class="sxs-lookup"><span data-stu-id="e097a-107">Example</span></span>  
 <span data-ttu-id="e097a-108">次の例で、`let` は 2 つの方法で使用されます。</span><span class="sxs-lookup"><span data-stu-id="e097a-108">In the following example `let` is used in two ways:</span></span>  
  
1.  <span data-ttu-id="e097a-109">それ自体を照会できる列挙可能な型を作成します。</span><span class="sxs-lookup"><span data-stu-id="e097a-109">To create an enumerable type that can itself be queried.</span></span>  
  
2.  <span data-ttu-id="e097a-110">クエリが値変数 `word` に対して `ToLower` を 1 回のみ呼び出すことができるようにします。</span><span class="sxs-lookup"><span data-stu-id="e097a-110">To enable the query to call `ToLower` only one time on the range variable `word`.</span></span> <span data-ttu-id="e097a-111">`let` を使用しない場合、`where` 句の各述語内で、`ToLower` を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="e097a-111">Without using `let`, you would have to call `ToLower` in each predicate in the `where` clause.</span></span>  
  
 <span data-ttu-id="e097a-112">[!code-cs[cscsrefQueryKeywords#28](../../../csharp/language-reference/keywords/codesnippet/CSharp/let-clause_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="e097a-112">[!code-cs[cscsrefQueryKeywords#28](../../../csharp/language-reference/keywords/codesnippet/CSharp/let-clause_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e097a-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="e097a-113">See Also</span></span>  
 <span data-ttu-id="e097a-114">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="e097a-114">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="e097a-115">[クエリ キーワード (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="e097a-115">[Query Keywords (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md) </span></span>  
 <span data-ttu-id="e097a-116">[LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="e097a-116">[LINQ Query Expressions](../../../csharp/programming-guide/linq-query-expressions/index.md) </span></span>  
 <span data-ttu-id="e097a-117">[C# の LINQ の概要](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md) </span><span class="sxs-lookup"><span data-stu-id="e097a-117">[Getting Started with LINQ in C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md) </span></span>  
 [<span data-ttu-id="e097a-118">方法: クエリ式の例外を処理する</span><span class="sxs-lookup"><span data-stu-id="e097a-118">How to: Handle Exceptions in Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md)

