---
title: "var (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d2be56243f9c4ddafb3903d14fa6d6f9cb0e2f84
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="var-c-reference"></a><span data-ttu-id="63208-102">var (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="63208-102">var (C# Reference)</span></span>
<span data-ttu-id="63208-103">Visual C# 3.0 以降、メソッド スコープで宣言された変数には暗黙的な "型" `var` を与えることができます。</span><span class="sxs-lookup"><span data-stu-id="63208-103">Beginning in Visual C# 3.0, variables that are declared at method scope can have an implicit "type" `var`.</span></span> <span data-ttu-id="63208-104">暗黙的に型指定されたローカル変数では、型を自分で宣言した場合と同様に厳密に型指定されますが、コンパイラが型を決定します。</span><span class="sxs-lookup"><span data-stu-id="63208-104">An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type.</span></span> <span data-ttu-id="63208-105">次の 2 つの `i` の宣言は機能的に等しくなります。</span><span class="sxs-lookup"><span data-stu-id="63208-105">The following two declarations of `i` are functionally equivalent:</span></span>  
  
```  
var i = 10; // implicitly typed  
int i = 10; //explicitly typed  
```  
  
 <span data-ttu-id="63208-106">詳しくは、「[暗黙的に型指定されるローカル変数](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)」および「[LINQ クエリ操作での型の関係](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="63208-106">For more information, see [Implicitly Typed Local Variables](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) and [Type Relationships in LINQ Query Operations](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="63208-107">例</span><span class="sxs-lookup"><span data-stu-id="63208-107">Example</span></span>  
 <span data-ttu-id="63208-108">次の例は、2 つのクエリ式を示しています。</span><span class="sxs-lookup"><span data-stu-id="63208-108">The following example shows two query expressions.</span></span> <span data-ttu-id="63208-109">最初の式では、`var` の使用が許可されますが、必須ではありません。クエリ結果の型を `IEnumerable<string>` として明示的に指定できるためです。</span><span class="sxs-lookup"><span data-stu-id="63208-109">In the first expression, the use of `var` is permitted but is not required, because the type of the query result can be stated explicitly as an `IEnumerable<string>`.</span></span> <span data-ttu-id="63208-110">しかしながら、2 つ目の式では、`var` を使用する必要があります。結果が匿名型の集まりであり、その型の名前にはコンパイラ自体以外はアクセスできないためです。</span><span class="sxs-lookup"><span data-stu-id="63208-110">However, in the second expression, `var` must be used because the result is a collection of anonymous types, and the name of that type is not accessible except to the compiler itself.</span></span> <span data-ttu-id="63208-111">例 #2 では、`foreach` 繰り返し変数 `item` も暗黙的に型指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="63208-111">Note that in Example #2, the `foreach` iteration variable `item` must also be implicitly typed.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/var_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="63208-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="63208-112">See Also</span></span>  
 [<span data-ttu-id="63208-113">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="63208-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="63208-114">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="63208-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="63208-115">暗黙的に型指定されるローカル変数</span><span class="sxs-lookup"><span data-stu-id="63208-115">Implicitly Typed Local Variables</span></span>](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
