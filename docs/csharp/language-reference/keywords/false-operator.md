---
title: false 演算子 (C# リファレンス)
ms.date: 07/20/2015
helpviewer_keywords:
- false operator keyword [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: e1c6da604f35031dd9d712125356243e1735f452
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027838"
---
# <a name="false-operator-c-reference"></a><span data-ttu-id="d889b-102">false 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="d889b-102">false operator (C# Reference)</span></span>

<span data-ttu-id="d889b-103">オペランドが `false` であることを示す[ブール](bool.md)値 `true` を返します。それ以外の場合は `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="d889b-103">Returns the [bool](bool.md) value `true` to indicate that an operand is `false` and returns `false` otherwise.</span></span>

<span data-ttu-id="d889b-104">C# 2.0 より前のバージョンでは、`true` および `false` 演算子は、`SqlBool` などの型と互換性のあるユーザー定義の null 非許容の値型を作成するために使用されていました。</span><span class="sxs-lookup"><span data-stu-id="d889b-104">Prior to C# 2.0, the `true` and `false` operators were used to create user-defined nullable value types that were compatible with types such as `SqlBool`.</span></span> <span data-ttu-id="d889b-105">ただし、現在は null 許容の値型が組み込まれているため、可能な場合には、`true` 演算子と `false` 演算子のオーバーロードではなく、null 許容の値型を使用してください。</span><span class="sxs-lookup"><span data-stu-id="d889b-105">However, the language now provides built-in support for nullable value types, and whenever possible you should use those instead of overloading the `true` and `false` operators.</span></span> <span data-ttu-id="d889b-106">詳細については、「[null 許容型](../../programming-guide/nullable-types/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d889b-106">For more information, see [Nullable Types](../../programming-guide/nullable-types/index.md).</span></span>

<span data-ttu-id="d889b-107">null 許容のブール値では、必ずしも式 `a != b` が `!(a == b)` にならないことがあります。これは、いずれかの値が null の場合があるためです。</span><span class="sxs-lookup"><span data-stu-id="d889b-107">With nullable Booleans, the expression `a != b` is not necessarily equal to `!(a == b)` because one or both of the values might be null.</span></span> <span data-ttu-id="d889b-108">式内の null 値を適切に処理するには、`true` および `false` 演算子の両方を別にオーバーロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d889b-108">You have to overload both the `true` and `false` operators separately to correctly handle the null values in the expression.</span></span> <span data-ttu-id="d889b-109">次の例は、`true` 演算子と `false` 演算子をオーバーロードして使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d889b-109">The following example shows how to overload and use the `true` and `false` operators.</span></span>

[!code-csharp[csrefKeywordsOperator#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#16)]

<span data-ttu-id="d889b-110">`true` 演算子と `false` 演算子をオーバーロードする型は、[if](if-else.md)、[do](do.md)、[while](while.md)、[for](for.md) ステートメント内の制御式と、[条件式](../operators/conditional-operator.md)で使用できます。</span><span class="sxs-lookup"><span data-stu-id="d889b-110">A type that overloads the `true` and `false` operators can be used for the controlling expression in [if](if-else.md), [do](do.md), [while](while.md), and [for](for.md) statements and in [conditional expressions](../operators/conditional-operator.md).</span></span>

<span data-ttu-id="d889b-111">型で演算子 `false` を定義する場合は、演算子の [true](true.md) も定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d889b-111">If a type defines operator `false`, it must also define operator [true](true.md).</span></span>

<span data-ttu-id="d889b-112">型では、条件付き論理演算子 [&&](../operators/conditional-and-operator.md) と [&#124;&#124;](../operators/conditional-or-operator.md) を直接オーバーロードできませんが、通常の論理演算子と演算子 `true` および `false` をオーバーロードすることで同等の効果を実現できます。</span><span class="sxs-lookup"><span data-stu-id="d889b-112">A type cannot directly overload the conditional logical operators [&&](../operators/conditional-and-operator.md) and [&#124;&#124;](../operators/conditional-or-operator.md), but an equivalent effect can be achieved by overloading the regular logical operators and operators `true` and `false`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d889b-113">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="d889b-113">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="d889b-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="d889b-114">See also</span></span>

[<span data-ttu-id="d889b-115">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="d889b-115">C# Reference</span></span>](../index.md)  
[<span data-ttu-id="d889b-116">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="d889b-116">C# Programming Guide</span></span>](../../programming-guide/index.md)  
[<span data-ttu-id="d889b-117">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="d889b-117">C# Keywords</span></span>](index.md)  
[<span data-ttu-id="d889b-118">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="d889b-118">C# Operators</span></span>](../operators/index.md)  
[<span data-ttu-id="d889b-119">true</span><span class="sxs-lookup"><span data-stu-id="d889b-119">true</span></span>](true.md)  