---
title: "() 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ()_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
caps.latest.revision: 22
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
ms.openlocfilehash: 1b0a683880f0791ee69ea5971756d104323b4303
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="f1bb5-102">() 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="f1bb5-102">() Operator (C# Reference)</span></span>
<span data-ttu-id="f1bb5-103">かっこは式内での演算の順序を指定することに加え、以下のタスクを実行するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="f1bb5-103">In addition to being used to specify the order of operations in an expression, parentheses are used to perform the following tasks:</span></span>  
  
1.  <span data-ttu-id="f1bb5-104">キャストまたは型変換を指定する。</span><span class="sxs-lookup"><span data-stu-id="f1bb5-104">Specify casts, or type conversions.</span></span>  
  
     <span data-ttu-id="f1bb5-105">[!code-cs[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f1bb5-105">[!code-cs[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]</span></span>  
  
2.  <span data-ttu-id="f1bb5-106">メソッドまたはデリゲートを呼び出す。</span><span class="sxs-lookup"><span data-stu-id="f1bb5-106">Invoke methods or delegates.</span></span>  
  
     <span data-ttu-id="f1bb5-107">[!code-cs[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="f1bb5-107">[!code-cs[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1bb5-108">コメント</span><span class="sxs-lookup"><span data-stu-id="f1bb5-108">Remarks</span></span>  
 <span data-ttu-id="f1bb5-109">キャストによってある型から別の型への変換演算子が明示的に呼び出されます。その変換演算子が定義されていない場合、キャストは失敗します。</span><span class="sxs-lookup"><span data-stu-id="f1bb5-109">A cast explicitly invokes the conversion operator from one type to another; the cast fails if no such conversion operator is defined.</span></span> <span data-ttu-id="f1bb5-110">変換演算子を定義するには、「[explicit](../../../csharp/language-reference/keywords/explicit.md)」および「[implicit](../../../csharp/language-reference/keywords/implicit.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1bb5-110">To define a conversion operator, see [explicit](../../../csharp/language-reference/keywords/explicit.md) and [implicit](../../../csharp/language-reference/keywords/implicit.md).</span></span>  
  
 <span data-ttu-id="f1bb5-111">`()` 演算子はオーバーロードできません。</span><span class="sxs-lookup"><span data-stu-id="f1bb5-111">The `()` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="f1bb5-112">詳細については、「[キャストと型変換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1bb5-112">For more information, see [Casting and Type Conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span></span>  
  
 <span data-ttu-id="f1bb5-113">キャスト式では、構文があいまいになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f1bb5-113">A cast expression could lead to ambiguous syntax.</span></span> <span data-ttu-id="f1bb5-114">たとえば式 `(x)–y` は、キャスト式 (型 x への –y のキャスト) とも、かっこで囲まれた式と組み合わせた x – y の値を計算する加法式とも解釈できます。</span><span class="sxs-lookup"><span data-stu-id="f1bb5-114">For example, the expression `(x)–y` could be either interpreted as a cast expression (a cast of –y to type x) or as an additive expression combined with a parenthesized expression, which computes the value x – y.</span></span>  
  
 <span data-ttu-id="f1bb5-115">メソッド呼び出しの詳細については、「[メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1bb5-115">For more information about method invocation, see [Methods](../../../csharp/programming-guide/classes-and-structs/methods.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="f1bb5-116">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="f1bb5-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f1bb5-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="f1bb5-117">See Also</span></span>  
 <span data-ttu-id="f1bb5-118">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="f1bb5-118">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="f1bb5-119">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f1bb5-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="f1bb5-120">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="f1bb5-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

