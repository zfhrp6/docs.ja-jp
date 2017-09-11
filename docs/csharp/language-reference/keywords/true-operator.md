---
title: "true 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- true operator [C#]
ms.assetid: acaba817-5da5-4364-b3b2-2e5c75ec1839
caps.latest.revision: 19
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
ms.openlocfilehash: c74fdc8091013ce7793c0591fc17ece80fd6d76d
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="true-operator-c-reference"></a><span data-ttu-id="1cd23-102">true 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="1cd23-102">true Operator (C# Reference)</span></span>
<span data-ttu-id="1cd23-103">オペランドが true である場合は [ブール](../../../csharp/language-reference/keywords/bool.md)値 `true` を返します。それ以外の場合は `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="1cd23-103">Returns the [bool](../../../csharp/language-reference/keywords/bool.md) value `true` to indicate that an operand is true and returns `false` otherwise.</span></span>  
  
 <span data-ttu-id="1cd23-104">C# 2.0 より前のバージョンでは、`true` 演算子と `false` 演算子は、`SqlBool` などの型と互換性のあるユーザー定義の null 非許容の値型を作成するために使用されていました。</span><span class="sxs-lookup"><span data-stu-id="1cd23-104">Prior to C# 2.0, the `true` and `false` operators were used to create user-defined nullable value types that were compatible with types such as `SqlBool`.</span></span> <span data-ttu-id="1cd23-105">ただし、現在は null 許容の値型が組み込まれているため、可能な場合には、`true` 演算子と `false` 演算子のオーバーロードではなく、null 許容の値型を使用してください。</span><span class="sxs-lookup"><span data-stu-id="1cd23-105">However, the language now provides built-in support for nullable value types, and whenever possible you should use those instead of overloading the `true` and `false` operators.</span></span> <span data-ttu-id="1cd23-106">詳細については、「[null 許容型](../../../csharp/programming-guide/nullable-types/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1cd23-106">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
 <span data-ttu-id="1cd23-107">null 許容のブール値では、必ずしも式 `a != b` と `!(a == b)` は同じではありません。これは、一方または両方の値が null になる可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="1cd23-107">With nullable Booleans, the expression `a != b` is not necessarily equal to `!(a == b)` because one or both of the values might be null.</span></span> <span data-ttu-id="1cd23-108">式内の null 値を正しく識別するには、`true` 演算子と `false` 演算子の両方を個別にオーバーロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1cd23-108">You need to overload both the `true` and `false` operators separately to correctly identify the null values in the expression.</span></span> <span data-ttu-id="1cd23-109">次の例は、`true` 演算子と `false` 演算子をオーバーロードして使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="1cd23-109">The following example shows how to overload and use the `true` and `false` operators.</span></span>  
  
 <span data-ttu-id="1cd23-110">[!code-cs[csrefKeywordsOperator#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/true-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="1cd23-110">[!code-cs[csrefKeywordsOperator#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/true-operator_1.cs)]</span></span>  
  
 <span data-ttu-id="1cd23-111">`true` 演算子と `false` 演算子をオーバーロードする型は、[if](../../../csharp/language-reference/keywords/if-else.md)、[do](../../../csharp/language-reference/keywords/do.md)、[while](../../../csharp/language-reference/keywords/while.md)、[for](../../../csharp/language-reference/keywords/for.md) ステートメント内の制御式と、[条件式](../../../csharp/language-reference/operators/conditional-operator.md)で使用できます。</span><span class="sxs-lookup"><span data-stu-id="1cd23-111">A type that overloads the `true` and `false` operators can be used for the controlling expression in [if](../../../csharp/language-reference/keywords/if-else.md), [do](../../../csharp/language-reference/keywords/do.md), [while](../../../csharp/language-reference/keywords/while.md), and [for](../../../csharp/language-reference/keywords/for.md) statements and in [conditional expressions](../../../csharp/language-reference/operators/conditional-operator.md).</span></span>  
  
 <span data-ttu-id="1cd23-112">型で `true` 演算子を定義する場合は [false](../../../csharp/language-reference/keywords/false.md) 演算子も定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1cd23-112">If a type defines operator `true`, it must also define operator [false](../../../csharp/language-reference/keywords/false.md).</span></span>  
  
 <span data-ttu-id="1cd23-113">型では、条件付き論理演算子 ([&&](../../../csharp/language-reference/operators/conditional-and-operator.md) と [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md)) を直接オーバーロードすることはできませんが、通常の論理演算子と演算子 `true` および `false` をオーバーロードすることで同等の効果を実現できます。</span><span class="sxs-lookup"><span data-stu-id="1cd23-113">A type cannot directly overload the conditional logical operators ([&&](../../../csharp/language-reference/operators/conditional-and-operator.md) and [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md)), but an equivalent effect can be achieved by overloading the regular logical operators and operators `true` and `false`.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="1cd23-114">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="1cd23-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1cd23-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="1cd23-115">See Also</span></span>  
 <span data-ttu-id="1cd23-116">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="1cd23-116">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="1cd23-117">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="1cd23-117">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="1cd23-118">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="1cd23-118">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="1cd23-119">[C# 演算子](../../../csharp/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="1cd23-119">[C# Operators](../../../csharp/language-reference/operators/index.md) </span></span>  
 [<span data-ttu-id="1cd23-120">false</span><span class="sxs-lookup"><span data-stu-id="1cd23-120">false</span></span>](../../../csharp/language-reference/keywords/false.md)

