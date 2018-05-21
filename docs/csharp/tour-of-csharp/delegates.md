---
title: C# のデリゲート - C# 言語のツアー
description: C# のデリゲートと遅延バインディングについて
ms.date: 08/10/2016
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: 1dcd078b275d951b049b0c5bb6e084a4083d042d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="delegates"></a><span data-ttu-id="82a3c-103">デリゲート</span><span class="sxs-lookup"><span data-stu-id="82a3c-103">Delegates</span></span>

<span data-ttu-id="82a3c-104">***デリゲート型***は、特定のパラメーター リストおよび戻り値を使用してメソッドへの参照を表します。</span><span class="sxs-lookup"><span data-stu-id="82a3c-104">A ***delegate type*** represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="82a3c-105">デリゲートを使用すれば、変数に割り当ててパラメーターとして渡すことのできるエンティティとして、メソッドを処理できます。</span><span class="sxs-lookup"><span data-stu-id="82a3c-105">Delegates make it possible to treat methods as entities that can be assigned to variables and passed as parameters.</span></span> <span data-ttu-id="82a3c-106">デリゲートはまた、他のいくつかの言語にみられる関数ポインターの概念に似ていますが、関数ポインターとは異なり、デリゲートはオブジェクト指向でタイプ セーフです。</span><span class="sxs-lookup"><span data-stu-id="82a3c-106">Delegates are similar to the concept of function pointers found in some other languages, but unlike function pointers, delegates are object-oriented and type-safe.</span></span>

<span data-ttu-id="82a3c-107">次の例では、`Function` という名前のデリゲート型を宣言して使用します。</span><span class="sxs-lookup"><span data-stu-id="82a3c-107">The following example declares and uses a delegate type named `Function`.</span></span>

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

<span data-ttu-id="82a3c-108">`Function` デリゲート型のインスタンスは、`double` 引数を取得して `double` 値を返す任意のメソッドを参照できます。</span><span class="sxs-lookup"><span data-stu-id="82a3c-108">An instance of the `Function` delegate type can reference any method that takes a `double` argument and returns a `double` value.</span></span> <span data-ttu-id="82a3c-109">`Apply` メソッドは、指定された関数を `double[]` の要素に適用し、`double[]` を結果とともに返します。</span><span class="sxs-lookup"><span data-stu-id="82a3c-109">The `Apply` method applies a given Function to the elements of a `double[]`, returning a `double[]` with the results.</span></span> <span data-ttu-id="82a3c-110">`Main` メソッドでは、`Apply` は `double[]` に 3 つの異なる関数を適用するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="82a3c-110">In the `Main` method, `Apply` is used to apply three different functions to a `double[]`.</span></span>

<span data-ttu-id="82a3c-111">デリゲートは、静的メソッド (前述の例の `Square` や `Math.Sin` など) またはインスタンス メソッド (前述の例の `m.Multiply` など) のいずれかを参照できます。</span><span class="sxs-lookup"><span data-stu-id="82a3c-111">A delegate can reference either a static method (such as `Square` or `Math.Sin` in the previous example) or an instance method (such as `m.Multiply` in the previous example).</span></span> <span data-ttu-id="82a3c-112">インスタンス メソッドを参照するデリゲートはまた、特定のオブジェクトを参照し、インスタンス メソッドがデリゲートから呼び出されると、そのオブジェクトは呼び出しで `this` になります。</span><span class="sxs-lookup"><span data-stu-id="82a3c-112">A delegate that references an instance method also references a particular object, and when the instance method is invoked through the delegate, that object becomes `this` in the invocation.</span></span>

<span data-ttu-id="82a3c-113">その場で作成される「インライン メソッド」である匿名関数を使用してデリゲートを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="82a3c-113">Delegates can also be created using anonymous functions, which are "inline methods" that are created on the fly.</span></span> <span data-ttu-id="82a3c-114">匿名関数では、周囲のメソッドのローカル変数を確認できます。</span><span class="sxs-lookup"><span data-stu-id="82a3c-114">Anonymous functions can see the local variables of the surrounding methods.</span></span> <span data-ttu-id="82a3c-115">したがって、上記の乗数の例は、乗数クラスを使用せずもっと簡単に記述できます。</span><span class="sxs-lookup"><span data-stu-id="82a3c-115">Thus, the multiplier example above can be written more easily without using a Multiplier class:</span></span>

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

<span data-ttu-id="82a3c-116">デリゲートの興味深く有用な点は、参照するメソッドのクラスを把握せず必要ともしないことです。重要なのは、参照されるメソッドは同じパラメーターを持ち、デリゲートとして型を返すということです。</span><span class="sxs-lookup"><span data-stu-id="82a3c-116">An interesting and useful property of a delegate is that it does not know or care about the class of the method it references; all that matters is that the referenced method has the same parameters and return type as the delegate.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="82a3c-117">[前へ](enums.md)
[次へ](attributes.md)</span><span class="sxs-lookup"><span data-stu-id="82a3c-117">[Previous](enums.md)
[Next](attributes.md)</span></span>
