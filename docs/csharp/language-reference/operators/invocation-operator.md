---
title: () 演算子 (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
ms.openlocfilehash: 82dfc2e11d6a8a025aa9b7557255a13b69ffa508
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208071"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="6e420-102">() 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="6e420-102">() Operator (C# Reference)</span></span>
<span data-ttu-id="6e420-103">かっこは式内での演算の順序を指定することに加え、以下のタスクを実行するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="6e420-103">In addition to being used to specify the order of operations in an expression, parentheses are used to perform the following tasks:</span></span>  
  
1.  <span data-ttu-id="6e420-104">キャストまたは型変換を指定する。</span><span class="sxs-lookup"><span data-stu-id="6e420-104">Specify casts, or type conversions.</span></span>  
  
     [!code-csharp[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]  
  
2.  <span data-ttu-id="6e420-105">メソッドまたはデリゲートを呼び出す。</span><span class="sxs-lookup"><span data-stu-id="6e420-105">Invoke methods or delegates.</span></span>  
  
     [!code-csharp[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="6e420-106">コメント</span><span class="sxs-lookup"><span data-stu-id="6e420-106">Remarks</span></span>  
 <span data-ttu-id="6e420-107">キャストによってある型から別の型への変換演算子が明示的に呼び出されます。その変換演算子が定義されていない場合、キャストは失敗します。</span><span class="sxs-lookup"><span data-stu-id="6e420-107">A cast explicitly invokes the conversion operator from one type to another; the cast fails if no such conversion operator is defined.</span></span> <span data-ttu-id="6e420-108">変換演算子を定義するには、「[explicit](../../../csharp/language-reference/keywords/explicit.md)」および「[implicit](../../../csharp/language-reference/keywords/implicit.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6e420-108">To define a conversion operator, see [explicit](../../../csharp/language-reference/keywords/explicit.md) and [implicit](../../../csharp/language-reference/keywords/implicit.md).</span></span>  
  
 <span data-ttu-id="6e420-109">`()` 演算子はオーバーロードできません。</span><span class="sxs-lookup"><span data-stu-id="6e420-109">The `()` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="6e420-110">詳細については、「[キャストと型変換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6e420-110">For more information, see [Casting and Type Conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span></span>  
  
 <span data-ttu-id="6e420-111">メソッド呼び出しの詳細については、「[メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6e420-111">For more information about method invocation, see [Methods](../../../csharp/programming-guide/classes-and-structs/methods.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="6e420-112">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="6e420-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6e420-113">参照</span><span class="sxs-lookup"><span data-stu-id="6e420-113">See Also</span></span>  
 [<span data-ttu-id="6e420-114">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="6e420-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6e420-115">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="6e420-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6e420-116">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="6e420-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
