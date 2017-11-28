---
title: "C# のデリゲート - C# 言語のツアー"
description: "C# のデリゲートと遅延バインディングについて"
keywords: ".NET、C#、デリゲート、ラムダ、遅延バインディング"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: bb304b2e5c762a44aab931b5e8f7fe9c99805eba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="delegates"></a><span data-ttu-id="111ea-104">デリゲート</span><span class="sxs-lookup"><span data-stu-id="111ea-104">Delegates</span></span>

<span data-ttu-id="111ea-105">***デリゲート型***は、特定のパラメーター リストおよび戻り値を使用してメソッドへの参照を表します。</span><span class="sxs-lookup"><span data-stu-id="111ea-105">A ***delegate type*** represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="111ea-106">デリゲートを使用すれば、変数に割り当ててパラメーターとして渡すことのできるエンティティとして、メソッドを処理できます。</span><span class="sxs-lookup"><span data-stu-id="111ea-106">Delegates make it possible to treat methods as entities that can be assigned to variables and passed as parameters.</span></span> <span data-ttu-id="111ea-107">デリゲートはまた、他のいくつかの言語にみられる関数ポインターの概念に似ていますが、関数ポインターとは異なり、デリゲートはオブジェクト指向でタイプ セーフです。</span><span class="sxs-lookup"><span data-stu-id="111ea-107">Delegates are similar to the concept of function pointers found in some other languages, but unlike function pointers, delegates are object-oriented and type-safe.</span></span>

<span data-ttu-id="111ea-108">次の例では、`Function` という名前のデリゲート型を宣言して使用します。</span><span class="sxs-lookup"><span data-stu-id="111ea-108">The following example declares and uses a delegate type named `Function`.</span></span>

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

<span data-ttu-id="111ea-109">`Function` デリゲート型のインスタンスは、`double` 引数を取得して `double` 値を返す任意のメソッドを参照できます。</span><span class="sxs-lookup"><span data-stu-id="111ea-109">An instance of the `Function` delegate type can reference any method that takes a `double` argument and returns a `double` value.</span></span> <span data-ttu-id="111ea-110">`Apply` メソッドは、指定された関数を `double[]` の要素に適用し、`double[]` を結果とともに返します。</span><span class="sxs-lookup"><span data-stu-id="111ea-110">The `Apply` method applies a given Function to the elements of a `double[]`, returning a `double[]` with the results.</span></span> <span data-ttu-id="111ea-111">`Main` メソッドでは、`Apply` は `double[]` に 3 つの異なる関数を適用するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="111ea-111">In the `Main` method, `Apply` is used to apply three different functions to a `double[]`.</span></span>

<span data-ttu-id="111ea-112">デリゲートは、静的メソッド (前述の例の `Square` や `Math.Sin` など) またはインスタンス メソッド (前述の例の `m.Multiply` など) のいずれかを参照できます。</span><span class="sxs-lookup"><span data-stu-id="111ea-112">A delegate can reference either a static method (such as `Square` or `Math.Sin` in the previous example) or an instance method (such as `m.Multiply` in the previous example).</span></span> <span data-ttu-id="111ea-113">インスタンス メソッドを参照するデリゲートはまた、特定のオブジェクトを参照し、インスタンス メソッドがデリゲートから呼び出されると、そのオブジェクトは呼び出しで `this` になります。</span><span class="sxs-lookup"><span data-stu-id="111ea-113">A delegate that references an instance method also references a particular object, and when the instance method is invoked through the delegate, that object becomes `this` in the invocation.</span></span>

<span data-ttu-id="111ea-114">その場で作成される「インライン メソッド」である匿名関数を使用してデリゲートを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="111ea-114">Delegates can also be created using anonymous functions, which are "inline methods" that are created on the fly.</span></span> <span data-ttu-id="111ea-115">匿名関数では、周囲のメソッドのローカル変数を確認できます。</span><span class="sxs-lookup"><span data-stu-id="111ea-115">Anonymous functions can see the local variables of the surrounding methods.</span></span> <span data-ttu-id="111ea-116">したがって、上記の乗数の例は、乗数クラスを使用せずもっと簡単に記述できます。</span><span class="sxs-lookup"><span data-stu-id="111ea-116">Thus, the multiplier example above can be written more easily without using a Multiplier class:</span></span>

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

<span data-ttu-id="111ea-117">デリゲートの興味深く有用な点は、参照するメソッドのクラスを把握せず必要ともしないことです。重要なのは、参照されるメソッドは同じパラメーターを持ち、デリゲートとして型を返すということです。</span><span class="sxs-lookup"><span data-stu-id="111ea-117">An interesting and useful property of a delegate is that it does not know or care about the class of the method it references; all that matters is that the referenced method has the same parameters and return type as the delegate.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="111ea-118">[前へ](enums.md)
[次へ](attributes.md)</span><span class="sxs-lookup"><span data-stu-id="111ea-118">[Previous](enums.md)
[Next](attributes.md)</span></span>
