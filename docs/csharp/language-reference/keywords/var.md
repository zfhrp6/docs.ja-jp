---
title: "var (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- var
- var_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
caps.latest.revision: 13
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
ms.openlocfilehash: 2a96d1c8869edd96cec913f1a868bcc3253dd14f
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="var-c-reference"></a><span data-ttu-id="32cd4-102">var (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="32cd4-102">var (C# Reference)</span></span>
<span data-ttu-id="32cd4-103">Visual C# 3.0 以降、メソッド スコープで宣言された変数には暗黙的な "型" `var` を与えることができます。</span><span class="sxs-lookup"><span data-stu-id="32cd4-103">Beginning in Visual C# 3.0, variables that are declared at method scope can have an implicit "type" `var`.</span></span> <span data-ttu-id="32cd4-104">暗黙的に型指定されたローカル変数では、型を自分で宣言した場合と同様に厳密に型指定されますが、コンパイラが型を決定します。</span><span class="sxs-lookup"><span data-stu-id="32cd4-104">An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type.</span></span> <span data-ttu-id="32cd4-105">次の 2 つの `i` の宣言は機能的に等しくなります。</span><span class="sxs-lookup"><span data-stu-id="32cd4-105">The following two declarations of `i` are functionally equivalent:</span></span>  
  
```  
var i = 10; // implicitly typed  
int i = 10; //explicitly typed  
```  
  
 <span data-ttu-id="32cd4-106">詳しくは、「[暗黙的に型指定されるローカル変数](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)」および「[LINQ クエリ操作での型の関係](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="32cd4-106">For more information, see [Implicitly Typed Local Variables](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) and [Type Relationships in LINQ Query Operations](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="32cd4-107">例</span><span class="sxs-lookup"><span data-stu-id="32cd4-107">Example</span></span>  
 <span data-ttu-id="32cd4-108">次の例は、2 つのクエリ式を示しています。</span><span class="sxs-lookup"><span data-stu-id="32cd4-108">The following example shows two query expressions.</span></span> <span data-ttu-id="32cd4-109">最初の式では、`var` の使用が許可されますが、必須ではありません。クエリ結果の型を `IEnumerable<string>` として明示的に指定できるためです。</span><span class="sxs-lookup"><span data-stu-id="32cd4-109">In the first expression, the use of `var` is permitted but is not required, because the type of the query result can be stated explicitly as an `IEnumerable<string>`.</span></span> <span data-ttu-id="32cd4-110">しかしながら、2 つ目の式では、`var` を使用する必要があります。結果が匿名型の集まりであり、その型の名前にはコンパイラ自体以外はアクセスできないためです。</span><span class="sxs-lookup"><span data-stu-id="32cd4-110">However, in the second expression, `var` must be used because the result is a collection of anonymous types, and the name of that type is not accessible except to the compiler itself.</span></span> <span data-ttu-id="32cd4-111">例 #2 では、`foreach` 繰り返し変数 `item` も暗黙的に型指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="32cd4-111">Note that in Example #2, the `foreach` iteration variable `item` must also be implicitly typed.</span></span>  
  
 <span data-ttu-id="32cd4-112">[!code-cs[csrefKeywordsTypes#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/var_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="32cd4-112">[!code-cs[csrefKeywordsTypes#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/var_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32cd4-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="32cd4-113">See Also</span></span>  
 <span data-ttu-id="32cd4-114">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="32cd4-114">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="32cd4-115">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="32cd4-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="32cd4-116">暗黙的に型指定されるローカル変数</span><span class="sxs-lookup"><span data-stu-id="32cd4-116">Implicitly Typed Local Variables</span></span>](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)

