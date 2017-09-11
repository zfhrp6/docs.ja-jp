---
title: "方法 : クエリ式で暗黙的に型指定されるローカル変数および配列を使用する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- implicitly-typed local variables [C#], how to use
ms.assetid: 6b7354d2-af79-427a-b6a8-f74eb8fd0b91
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
ms.openlocfilehash: 60e22aacef05ae2fe1b5e7127396cc66f24661d3
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression-c-programming-guide"></a><span data-ttu-id="6249d-102">方法 : クエリ式で暗黙的に型指定されるローカル変数および配列を使用する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="6249d-102">How to: Use Implicitly Typed Local Variables and Arrays in a Query Expression (C# Programming Guide)</span></span>
<span data-ttu-id="6249d-103">コンパイラによってローカル変数の型が決定されるようにする場合は、暗黙的に型指定されたローカル変数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="6249d-103">You can use implicitly typed local variables whenever you want the compiler to determine the type of a local variable.</span></span> <span data-ttu-id="6249d-104">クエリ式でよく使用する匿名型を格納するには、暗黙的に型指定されたローカル変数を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6249d-104">You must use implicitly typed local variables to store anonymous types, which are often used in query expressions.</span></span> <span data-ttu-id="6249d-105">以下の例では、クエリで暗黙的に型指定されたローカル変数を省略できる場合と、使用しなければならない場合の両方を示します。</span><span class="sxs-lookup"><span data-stu-id="6249d-105">The following examples illustrate both optional and required uses of implicitly typed local variables in queries.</span></span>  
  
 <span data-ttu-id="6249d-106">暗黙的に型指定されたローカル変数は、[var](../../../csharp/language-reference/keywords/var.md) コンテキスト キーワードを使用して宣言します。</span><span class="sxs-lookup"><span data-stu-id="6249d-106">Implicitly typed local variables are declared by using the [var](../../../csharp/language-reference/keywords/var.md) contextual keyword.</span></span> <span data-ttu-id="6249d-107">詳細については、「[暗黙的に型指定されるローカル変数](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)」と「[暗黙的に型指定される配列](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6249d-107">For more information, see [Implicitly Typed Local Variables](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) and [Implicitly Typed Arrays](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6249d-108">例</span><span class="sxs-lookup"><span data-stu-id="6249d-108">Example</span></span>  
 <span data-ttu-id="6249d-109">次の例は、`var` キーワードが必須である一般的なシナリオ (匿名型のシーケンスを生成するクエリ) を示しています。</span><span class="sxs-lookup"><span data-stu-id="6249d-109">The following example shows a common scenario in which the `var` keyword is required: a query expression that produces a sequence of anonymous types.</span></span> <span data-ttu-id="6249d-110">このシナリオでは、匿名型の型名にアクセスできないため、`var`を使用して `foreach` ステートメントのクエリ変数と反復変数の両方を暗黙的に型指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6249d-110">In this scenario, both the query variable and the iteration variable in the `foreach` statement must be implicitly typed by using `var` because you do not have access to a type name for the anonymous type.</span></span> <span data-ttu-id="6249d-111">匿名型の詳細については、「[匿名型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6249d-111">For more information about anonymous types, see [Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
 <span data-ttu-id="6249d-112">[!code-cs[csProgGuideLINQ#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="6249d-112">[!code-cs[csProgGuideLINQ#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="6249d-113">例</span><span class="sxs-lookup"><span data-stu-id="6249d-113">Example</span></span>  
 <span data-ttu-id="6249d-114">次の例では、同様の状況で `var` キーワードを使用しています。ただし、この場合、`var` の使用はオプションです。</span><span class="sxs-lookup"><span data-stu-id="6249d-114">The following example uses the `var` keyword in a situation that is similar, but in which the use of `var` is optional.</span></span> <span data-ttu-id="6249d-115">`student.LastName` は文字列であるため、クエリを実行すると文字列のシーケンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="6249d-115">Because `student.LastName` is a string, execution of the query returns a sequence of strings.</span></span> <span data-ttu-id="6249d-116">したがって、`queryID` の型は、`var` ではなく `System.Collections.Generic.IEnumerable<string>` として宣言できます。</span><span class="sxs-lookup"><span data-stu-id="6249d-116">Therefore, the type of `queryID` could be declared as `System.Collections.Generic.IEnumerable<string>` instead of `var`.</span></span> <span data-ttu-id="6249d-117">`var` キーワードは利便性のために使用されます。</span><span class="sxs-lookup"><span data-stu-id="6249d-117">Keyword `var` is used for convenience.</span></span> <span data-ttu-id="6249d-118">この例では、`foreach` ステートメントの反復変数は文字列として明示的に型指定されていますが、代わりに `var` を使用して宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="6249d-118">In the example, the iteration variable in the `foreach` statement is explicitly typed as a string, but it could instead be declared by using `var`.</span></span> <span data-ttu-id="6249d-119">反復変数の型は匿名型ではないため、`var` の使用はオプションであり、必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="6249d-119">Because the type of the iteration variable is not an anonymous type, the use of `var` is an option, not a requirement.</span></span> <span data-ttu-id="6249d-120">`var` 自体は型ではなく、型を推論して割り当てるようコンパイラに指示する命令です。</span><span class="sxs-lookup"><span data-stu-id="6249d-120">Remember, `var` itself is not a type, but an instruction to the compiler to infer and assign the type.</span></span>  
  
 <span data-ttu-id="6249d-121">[!code-cs[csProgGuideLINQ#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="6249d-121">[!code-cs[csProgGuideLINQ#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6249d-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="6249d-122">See Also</span></span>  
 <span data-ttu-id="6249d-123">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="6249d-123">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="6249d-124">[拡張メソッド](../../../csharp/programming-guide/classes-and-structs/extension-methods.md) </span><span class="sxs-lookup"><span data-stu-id="6249d-124">[Extension Methods](../../../csharp/programming-guide/classes-and-structs/extension-methods.md) </span></span>  
 <span data-ttu-id="6249d-125">[LINQ (統合言語クエリ)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) </span><span class="sxs-lookup"><span data-stu-id="6249d-125">[LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) </span></span>  
 <span data-ttu-id="6249d-126">[var](../../../csharp/language-reference/keywords/var.md) </span><span class="sxs-lookup"><span data-stu-id="6249d-126">[var](../../../csharp/language-reference/keywords/var.md) </span></span>  
 [<span data-ttu-id="6249d-127">LINQ クエリ式</span><span class="sxs-lookup"><span data-stu-id="6249d-127">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)

