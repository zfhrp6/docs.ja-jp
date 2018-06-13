---
title: C# の列挙型 - C# 言語のツアー
description: C# における列挙型、離散した名前付き定数について
ms.date: 08/10/2016
ms.assetid: 7faba1cc-6ea9-4a19-adb9-0335e4b132e5
ms.openlocfilehash: 7fe2626381cb90e55842e3be17dd450eb73d5a5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353355"
---
# <a name="enums"></a><span data-ttu-id="01af7-103">列挙体</span><span class="sxs-lookup"><span data-stu-id="01af7-103">Enums</span></span>

<span data-ttu-id="01af7-104">***列挙型***は、一連の名前付き定数を使用する固有の値の型です。</span><span class="sxs-lookup"><span data-stu-id="01af7-104">An ***enum type*** is a distinct value type with a set of named constants.</span></span> <span data-ttu-id="01af7-105">一連の離散値が使用される型を定義する必要がある場合に、列挙型を定義します。</span><span class="sxs-lookup"><span data-stu-id="01af7-105">You define enums when you need to define a type that can have a set of discrete values.</span></span> <span data-ttu-id="01af7-106">列挙型は、整数値の型のいずれかを基になる記憶域として使用します。</span><span class="sxs-lookup"><span data-stu-id="01af7-106">They use one of the integral value types as their underlying storage.</span></span> <span data-ttu-id="01af7-107">列挙型により、離散値にセマンティックな意味が付与されます。</span><span class="sxs-lookup"><span data-stu-id="01af7-107">They provide semantic meaning to the discrete values.</span></span>

<span data-ttu-id="01af7-108">次の例では `Red`、`Green`、および `Blue` の定数 3 つとともに、`Color` と名前付けられた `enum` 型を宣言して使用します。</span><span class="sxs-lookup"><span data-stu-id="01af7-108">The following example declares and uses an `enum` type named `Color` with three constant values, `Red`, `Green`, and `Blue`.</span></span>

[!code-csharp[EnumExample](../../../samples/snippets/csharp/tour/enums/Program.cs#L3-L36)]

<span data-ttu-id="01af7-109">`enum` 型はそれぞれ、`enum` 型の***基になる型***と呼ばれる整数型に対応しています。</span><span class="sxs-lookup"><span data-stu-id="01af7-109">Each `enum` type has a corresponding integral type called the ***underlying type*** of the `enum` type.</span></span> <span data-ttu-id="01af7-110">基になる型を明示的に宣言しない `enum` 型には `int` の基になる型を持っています。</span><span class="sxs-lookup"><span data-stu-id="01af7-110">An `enum` type that does not explicitly declare an underlying type has an underlying type of `int`.</span></span> <span data-ttu-id="01af7-111">`enum` 型の記憶域形式と使用可能な値の範囲は基になる方によって決まります。</span><span class="sxs-lookup"><span data-stu-id="01af7-111">An `enum` type’s storage format and range of possible values are determined by its underlying type.</span></span> <span data-ttu-id="01af7-112">`enum` 型が処理できる一連の値はその型の `enum` メンバーによって制限されません。</span><span class="sxs-lookup"><span data-stu-id="01af7-112">The set of values that an `enum` type can take on is not limited by its `enum` members.</span></span> <span data-ttu-id="01af7-113">特に、`enum` の基となる型の値はすべて、`enum` 型にキャストされる場合があり、`enum` 型の一意の有効な値です。</span><span class="sxs-lookup"><span data-stu-id="01af7-113">In particular, any value of the underlying type of an `enum` can be cast to the `enum` type and is a distinct valid value of that `enum` type.</span></span>

<span data-ttu-id="01af7-114">次の例では、`Alignment` と名前付けられた `enum` 型を、基となる型 `sbyte` とともに宣言します。</span><span class="sxs-lookup"><span data-stu-id="01af7-114">The following example declares an `enum` type named `Alignment` with an underlying type of `sbyte`.</span></span>

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L38-L43)]

<span data-ttu-id="01af7-115">前の例のとおり、`enum` メンバーの宣言にはメンバーの値を指定する定数式が含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="01af7-115">As shown by the previous example, an `enum` member declaration can include a constant expression that specifies the value of the member.</span></span> <span data-ttu-id="01af7-116">各 `enum` メンバーの定数値は `enum` の基となる型の範囲内にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="01af7-116">The constant value for each `enum` member must be in the range of the underlying type of the `enum`.</span></span> <span data-ttu-id="01af7-117">`enum` メンバーの宣言により値が明示的に指定されない場合、そのメンバーに 0 の値 (`enum` 型の最初のメンバーの場合)、またはテキスト上で先行する `enum` メンバーの値に 1 を足した値が与えられます。</span><span class="sxs-lookup"><span data-stu-id="01af7-117">When an `enum` member declaration does not explicitly specify a value, the member is given the value zero (if it is the first member in the `enum` type) or the value of the textually preceding `enum` member plus one.</span></span>

<span data-ttu-id="01af7-118">`Enum` の値は型キャストを使用して整数値に変換することができ、その逆方向の変換をすることもできます。</span><span class="sxs-lookup"><span data-stu-id="01af7-118">`Enum` values can be converted to integral values and vice versa using type casts.</span></span> <span data-ttu-id="01af7-119">例:</span><span class="sxs-lookup"><span data-stu-id="01af7-119">For example:</span></span>

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L49-L50)]

<span data-ttu-id="01af7-120">`enum` 型の既定値はすべて、`enum` 型に変換された 0 の整数値です。</span><span class="sxs-lookup"><span data-stu-id="01af7-120">The default value of any `enum` type is the integral value zero converted to the `enum` type.</span></span> <span data-ttu-id="01af7-121">変数が自動的に既定値に初期化された場合、これが `enum` 型の変数に与えられる値です。</span><span class="sxs-lookup"><span data-stu-id="01af7-121">In cases where variables are automatically initialized to a default value, this is the value given to variables of `enum` types.</span></span> <span data-ttu-id="01af7-122">`enum` 型の既定値を簡単に利用できるようにするために、リテラルの `0` が任意の `enum` 型に暗黙的に変換されます。</span><span class="sxs-lookup"><span data-stu-id="01af7-122">In order for the default value of an `enum` type to be easily available, the literal `0` implicitly converts to any `enum` type.</span></span> <span data-ttu-id="01af7-123">したがって、次の例も許可されます。</span><span class="sxs-lookup"><span data-stu-id="01af7-123">Thus, the following is permitted.</span></span>

[!code-csharp[EnumZero](../../../samples/snippets/csharp/tour/enums/Program.cs#L58-L58)]

>[!div class="step-by-step"]
<span data-ttu-id="01af7-124">[前へ](interfaces.md)
[次へ](delegates.md)</span><span class="sxs-lookup"><span data-stu-id="01af7-124">[Previous](interfaces.md)
[Next](delegates.md)</span></span>
