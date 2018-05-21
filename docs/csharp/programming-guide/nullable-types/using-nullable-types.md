---
title: Null 許容型の使用 (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: d2fe0f34c45d3de0516a71ca5ed4dc807df4bf93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="using-nullable-types-c-programming-guide"></a><span data-ttu-id="f398c-102">Null 許容型の使用 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="f398c-102">Using Nullable Types (C# Programming Guide)</span></span>
<span data-ttu-id="f398c-103">Null 許容型は、基底の型のすべての値と、追加の [null](../../../csharp/language-reference/keywords/null.md) 値を表すことができます。</span><span class="sxs-lookup"><span data-stu-id="f398c-103">Nullable types can represent all the values of an underlying type, and an additional [null](../../../csharp/language-reference/keywords/null.md) value.</span></span> <span data-ttu-id="f398c-104">Null 許容型は、次のいずれかの形式で宣言します。</span><span class="sxs-lookup"><span data-stu-id="f398c-104">Nullable types are declared in one of two ways:</span></span>  
  
 `System.Nullable<T> variable`  
  
 <span data-ttu-id="f398c-105">- または -</span><span class="sxs-lookup"><span data-stu-id="f398c-105">-or-</span></span>  
  
 `T? variable`  
  
 <span data-ttu-id="f398c-106">`T` は、Null 許容型の基底の型です。</span><span class="sxs-lookup"><span data-stu-id="f398c-106">`T` is the underlying type of the nullable type.</span></span> <span data-ttu-id="f398c-107">`T` には、`struct` を含む任意の値型を指定できますが、参照型は指定できません。</span><span class="sxs-lookup"><span data-stu-id="f398c-107">`T` can be any value type including `struct`; it cannot be a reference type.</span></span>  
  
 <span data-ttu-id="f398c-108">Null 許容型を使用するときの例として、通常のブール値変数が、true と false の 2 つの値をどのように持つことができるかを考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="f398c-108">For an example of when you might use a nullable type, consider how an ordinary Boolean variable can have two values: true and false.</span></span> <span data-ttu-id="f398c-109">この変数には、"未定義" を示す値はありません。</span><span class="sxs-lookup"><span data-stu-id="f398c-109">There is no value that signifies "undefined".</span></span> <span data-ttu-id="f398c-110">多くのプログラミング アプリケーションの中でも特にデータベース操作では、変数が未定義の状態で現れることがあります。</span><span class="sxs-lookup"><span data-stu-id="f398c-110">In many programming applications, most notably database interactions, variables can occur in an undefined state.</span></span> <span data-ttu-id="f398c-111">たとえば、データベース フィールドには、true や false の値が入力されている場合がありますが、値がまったく入力されていない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="f398c-111">For example, a field in a database may contain the values true or false, but it may also contain no value at all.</span></span> <span data-ttu-id="f398c-112">また、参照型に `null` を設定すると、その型が初期化されていないことを示すことができます。</span><span class="sxs-lookup"><span data-stu-id="f398c-112">Similarly, reference types can be set to `null` to indicate that they are not initialized.</span></span>  
  
 <span data-ttu-id="f398c-113">このような違いから、状態情報を格納する変数を追加したり、特別な値を使用したりするような余分なプログラミング作業が生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="f398c-113">This disparity can create extra programming work, with additional variables used to store state information, the use of special values, and so on.</span></span> <span data-ttu-id="f398c-114">C# では、Null 許容型修飾子により、未定義の値を示す値型変数を作成できます。</span><span class="sxs-lookup"><span data-stu-id="f398c-114">The nullable type modifier enables C# to create value-type variables that indicate an undefined value.</span></span>  
  
## <a name="examples-of-nullable-types"></a><span data-ttu-id="f398c-115">Null 許容型の例</span><span class="sxs-lookup"><span data-stu-id="f398c-115">Examples of Nullable Types</span></span>  
 <span data-ttu-id="f398c-116">Null 許容型の基底の型には、任意の値型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f398c-116">Any value type may be used as the basis for a nullable type.</span></span> <span data-ttu-id="f398c-117">例:</span><span class="sxs-lookup"><span data-stu-id="f398c-117">For example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#4](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_1.cs)]  
  
## <a name="the-members-of-nullable-types"></a><span data-ttu-id="f398c-118">Null 許容型のメンバー</span><span class="sxs-lookup"><span data-stu-id="f398c-118">The Members of Nullable Types</span></span>  
 <span data-ttu-id="f398c-119">Null 許容型の各インスタンスには、次のような 2 つのパブリックな読み取り専用プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="f398c-119">Each instance of a nullable type has two public read-only properties:</span></span>  
  
-   `HasValue`  
  
     <span data-ttu-id="f398c-120">`HasValue` は `bool` 型です。</span><span class="sxs-lookup"><span data-stu-id="f398c-120">`HasValue` is of type `bool`.</span></span> <span data-ttu-id="f398c-121">変数が null 以外の値を格納している場合、このプロパティには `true` が設定されます。</span><span class="sxs-lookup"><span data-stu-id="f398c-121">It is set to `true` when the variable contains a non-null value.</span></span>  
  
-   `Value`  
  
     <span data-ttu-id="f398c-122">`Value` は、基になっている型と同じ型です。</span><span class="sxs-lookup"><span data-stu-id="f398c-122">`Value` is of the same type as the underlying type.</span></span> <span data-ttu-id="f398c-123">`HasValue` が `true` の場合、`Value` には意味のある値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f398c-123">If `HasValue` is `true`, `Value` contains a meaningful value.</span></span> <span data-ttu-id="f398c-124">`HasValue` が `false` の場合、`Value` にアクセスすると、<xref:System.InvalidOperationException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="f398c-124">If `HasValue` is `false`, accessing `Value` will throw a <xref:System.InvalidOperationException>.</span></span>  
  
 <span data-ttu-id="f398c-125">次の例では、`HasValue` メンバーを使用して、値を表示する前に、変数に値が格納されているかどうかをテストします。</span><span class="sxs-lookup"><span data-stu-id="f398c-125">In this example, the `HasValue` member is used to test whether the variable contains a value before it tries to display it.</span></span>  
  
 [!code-csharp[csProgGuideTypes#5](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_2.cs)]  
  
 <span data-ttu-id="f398c-126">値のテストは、次の例のように行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="f398c-126">Testing for a value can also be done as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#6](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_3.cs)]  
  
## <a name="explicit-conversions"></a><span data-ttu-id="f398c-127">明示的変換</span><span class="sxs-lookup"><span data-stu-id="f398c-127">Explicit Conversions</span></span>  
 <span data-ttu-id="f398c-128">Null 許容型は、キャストを明示的に使用するか、または `Value` プロパティを使用して通常の型にキャストできます。</span><span class="sxs-lookup"><span data-stu-id="f398c-128">A nullable type can be cast to a regular type, either explicitly with a cast, or by using the `Value` property.</span></span> <span data-ttu-id="f398c-129">例:</span><span class="sxs-lookup"><span data-stu-id="f398c-129">For example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#7](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_4.cs)]  
  
 <span data-ttu-id="f398c-130">2 つのデータ型の間でユーザー定義の変換を定義している場合は、これらのデータ型の Null 許容バージョンを使用して、同じユーザー定義変換を実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="f398c-130">If a user-defined conversion is defined between two data types, the same conversion can also be used with the nullable versions of these data types.</span></span>  
  
## <a name="implicit-conversions"></a><span data-ttu-id="f398c-131">暗黙の型変換</span><span class="sxs-lookup"><span data-stu-id="f398c-131">Implicit Conversions</span></span>  
 <span data-ttu-id="f398c-132">Null 許容型の変数には、次の例のように `null` キーワードを使用して null に設定できます。</span><span class="sxs-lookup"><span data-stu-id="f398c-132">A variable of nullable type can be set to null with the `null` keyword, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#8](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_5.cs)]  
  
 <span data-ttu-id="f398c-133">通常の型から null 許容型への変換は暗黙的です。</span><span class="sxs-lookup"><span data-stu-id="f398c-133">The conversion from an ordinary type to a nullable type, is implicit.</span></span>  
  
 [!code-csharp[csProgGuideTypes#9](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_6.cs)]  
  
## <a name="operators"></a><span data-ttu-id="f398c-134">演算子</span><span class="sxs-lookup"><span data-stu-id="f398c-134">Operators</span></span>  
 <span data-ttu-id="f398c-135">値型向けに存在している定義済みの単項演算子、2 項演算子およびすべてのユーザー定義演算子は、Null 許容型でも使用できます。</span><span class="sxs-lookup"><span data-stu-id="f398c-135">The predefined unary and binary operators and any user-defined operators that exist for value types may also be used by nullable types.</span></span> <span data-ttu-id="f398c-136">これらの演算子は、オペランドが null の場合は null 値を生成し、null 以外の場合は、含まれている値に基づいて結果を算出します。</span><span class="sxs-lookup"><span data-stu-id="f398c-136">These operators produce a null value if the operands are null; otherwise, the operator uses the contained value to calculate the result.</span></span> <span data-ttu-id="f398c-137">例:</span><span class="sxs-lookup"><span data-stu-id="f398c-137">For example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#10](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_7.cs)]  
  
 <span data-ttu-id="f398c-138">2 つの null 許容型を比較したときに、一方の null 許容型の値が null でもう一方がそれ以外の場合は、`!=` (等しくない) を除くすべての比較が `false` と評価されます。</span><span class="sxs-lookup"><span data-stu-id="f398c-138">When you perform comparisons with nullable types, if the value of one of the nullable types is null and the other is not, all comparisons evaluate to `false` except for `!=` (not equal).</span></span> <span data-ttu-id="f398c-139">ある比較から返される結果が `false` であっても、逆のケースから返される結果が `true` とは限らない点が重要です。</span><span class="sxs-lookup"><span data-stu-id="f398c-139">It is important not to assume that because a particular comparison returns `false`, the opposite case returns `true`.</span></span> <span data-ttu-id="f398c-140">次の例では、10 は null より大きくも小さくも等しくもありません。</span><span class="sxs-lookup"><span data-stu-id="f398c-140">In the following example, 10 is not greater than, less than, nor equal to null.</span></span> <span data-ttu-id="f398c-141">`num1 != num2` のみが `true` と評価されます。</span><span class="sxs-lookup"><span data-stu-id="f398c-141">Only `num1 != num2` evaluates to `true`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#11](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_8.cs)]  
  
 <span data-ttu-id="f398c-142">どちらも null である 2 つの null 許容型を等価比較すると、結果は `true` と評価されます。</span><span class="sxs-lookup"><span data-stu-id="f398c-142">An equality comparison of two nullable types that are both null evaluates to `true`.</span></span>  
  
## <a name="the--operator"></a><span data-ttu-id="f398c-143">??</span><span class="sxs-lookup"><span data-stu-id="f398c-143">The ??</span></span> <span data-ttu-id="f398c-144">演算子</span><span class="sxs-lookup"><span data-stu-id="f398c-144">Operator</span></span>  
 <span data-ttu-id="f398c-145">`??` 演算子は、Null 許容型が Null 許容型以外の型に割り当てられているときに返す既定値を定義します。</span><span class="sxs-lookup"><span data-stu-id="f398c-145">The `??` operator defines a default value that is returned when a nullable type is assigned to a non-nullable type.</span></span>  
  
 [!code-csharp[csProgGuideTypes#12](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_9.cs)]  
  
 <span data-ttu-id="f398c-146">この演算子は、複数の Null 許容型で使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="f398c-146">This operator can also be used with multiple nullable types.</span></span> <span data-ttu-id="f398c-147">例:</span><span class="sxs-lookup"><span data-stu-id="f398c-147">For example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#13](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_10.cs)]  
  
## <a name="the-bool-type"></a><span data-ttu-id="f398c-148">bool? 型</span><span class="sxs-lookup"><span data-stu-id="f398c-148">The bool? type</span></span>  
 <span data-ttu-id="f398c-149">Null 許容 `bool?` 型は、[true](../../../csharp/language-reference/keywords/true.md)、[false](../../../csharp/language-reference/keywords/false.md)、[null](../../../csharp/language-reference/keywords/null.md) の 3 つの異なる値を格納できます。</span><span class="sxs-lookup"><span data-stu-id="f398c-149">The `bool?` nullable type can contain three different values: [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md) and [null](../../../csharp/language-reference/keywords/null.md).</span></span> <span data-ttu-id="f398c-150">bool? から bool にキャストする方法については、「[方法: bool? から bool に安全にキャストする](../../../csharp/programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f398c-150">For information about how to cast from a bool? to a bool, see [How to: Safely Cast from bool? to bool](../../../csharp/programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md).</span></span>  
  
 <span data-ttu-id="f398c-151">Null 許容ブール値は、SQL で使用するブール値変数型と似ています。</span><span class="sxs-lookup"><span data-stu-id="f398c-151">Nullable Booleans are like the Boolean variable type that is used in SQL.</span></span> <span data-ttu-id="f398c-152">`&` 演算子と `|` 演算子によって生成される結果が SQL の 3 値のブール型と一致するようにするには、次の定義済みの演算子を指定します。</span><span class="sxs-lookup"><span data-stu-id="f398c-152">To ensure that the results produced by the `&` and `|` operators are consistent with the three-valued Boolean type in SQL, the following predefined operators are provided:</span></span>  
  
 `bool? operator &(bool? x, bool? y)`  
  
 `bool? operator |(bool? x, bool? y)`  
  
 <span data-ttu-id="f398c-153">これらの演算子の結果を以下の表に示します。</span><span class="sxs-lookup"><span data-stu-id="f398c-153">The results of these operators are listed in the following table:</span></span>  
  
|<span data-ttu-id="f398c-154">x</span><span class="sxs-lookup"><span data-stu-id="f398c-154">X</span></span>|<span data-ttu-id="f398c-155">y</span><span class="sxs-lookup"><span data-stu-id="f398c-155">y</span></span>|<span data-ttu-id="f398c-156">x&y</span><span class="sxs-lookup"><span data-stu-id="f398c-156">x&y</span></span>|<span data-ttu-id="f398c-157">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="f398c-157">x&#124;y</span></span>|  
|-------|-------|---------|--------------|  
|<span data-ttu-id="f398c-158">true</span><span class="sxs-lookup"><span data-stu-id="f398c-158">true</span></span>|<span data-ttu-id="f398c-159">true</span><span class="sxs-lookup"><span data-stu-id="f398c-159">true</span></span>|<span data-ttu-id="f398c-160">true</span><span class="sxs-lookup"><span data-stu-id="f398c-160">true</span></span>|<span data-ttu-id="f398c-161">true</span><span class="sxs-lookup"><span data-stu-id="f398c-161">true</span></span>|  
|<span data-ttu-id="f398c-162">TRUE</span><span class="sxs-lookup"><span data-stu-id="f398c-162">true</span></span>|<span data-ttu-id="f398c-163">False</span><span class="sxs-lookup"><span data-stu-id="f398c-163">false</span></span>|<span data-ttu-id="f398c-164">false</span><span class="sxs-lookup"><span data-stu-id="f398c-164">false</span></span>|<span data-ttu-id="f398c-165">true</span><span class="sxs-lookup"><span data-stu-id="f398c-165">true</span></span>|  
|<span data-ttu-id="f398c-166">true</span><span class="sxs-lookup"><span data-stu-id="f398c-166">true</span></span>|<span data-ttu-id="f398c-167">null</span><span class="sxs-lookup"><span data-stu-id="f398c-167">null</span></span>|<span data-ttu-id="f398c-168">null</span><span class="sxs-lookup"><span data-stu-id="f398c-168">null</span></span>|<span data-ttu-id="f398c-169">true</span><span class="sxs-lookup"><span data-stu-id="f398c-169">true</span></span>|  
|<span data-ttu-id="f398c-170">False</span><span class="sxs-lookup"><span data-stu-id="f398c-170">false</span></span>|<span data-ttu-id="f398c-171">true</span><span class="sxs-lookup"><span data-stu-id="f398c-171">true</span></span>|<span data-ttu-id="f398c-172">False</span><span class="sxs-lookup"><span data-stu-id="f398c-172">false</span></span>|<span data-ttu-id="f398c-173">true</span><span class="sxs-lookup"><span data-stu-id="f398c-173">true</span></span>|  
|<span data-ttu-id="f398c-174">False</span><span class="sxs-lookup"><span data-stu-id="f398c-174">false</span></span>|<span data-ttu-id="f398c-175">False</span><span class="sxs-lookup"><span data-stu-id="f398c-175">false</span></span>|<span data-ttu-id="f398c-176">False</span><span class="sxs-lookup"><span data-stu-id="f398c-176">false</span></span>|<span data-ttu-id="f398c-177">False</span><span class="sxs-lookup"><span data-stu-id="f398c-177">false</span></span>|  
|<span data-ttu-id="f398c-178">False</span><span class="sxs-lookup"><span data-stu-id="f398c-178">false</span></span>|<span data-ttu-id="f398c-179">null</span><span class="sxs-lookup"><span data-stu-id="f398c-179">null</span></span>|<span data-ttu-id="f398c-180">False</span><span class="sxs-lookup"><span data-stu-id="f398c-180">false</span></span>|<span data-ttu-id="f398c-181">null</span><span class="sxs-lookup"><span data-stu-id="f398c-181">null</span></span>|  
|<span data-ttu-id="f398c-182">null</span><span class="sxs-lookup"><span data-stu-id="f398c-182">null</span></span>|<span data-ttu-id="f398c-183">true</span><span class="sxs-lookup"><span data-stu-id="f398c-183">true</span></span>|<span data-ttu-id="f398c-184">null</span><span class="sxs-lookup"><span data-stu-id="f398c-184">null</span></span>|<span data-ttu-id="f398c-185">true</span><span class="sxs-lookup"><span data-stu-id="f398c-185">true</span></span>|  
|<span data-ttu-id="f398c-186">null</span><span class="sxs-lookup"><span data-stu-id="f398c-186">null</span></span>|<span data-ttu-id="f398c-187">False</span><span class="sxs-lookup"><span data-stu-id="f398c-187">false</span></span>|<span data-ttu-id="f398c-188">False</span><span class="sxs-lookup"><span data-stu-id="f398c-188">false</span></span>|<span data-ttu-id="f398c-189">null</span><span class="sxs-lookup"><span data-stu-id="f398c-189">null</span></span>|  
|<span data-ttu-id="f398c-190">null</span><span class="sxs-lookup"><span data-stu-id="f398c-190">null</span></span>|<span data-ttu-id="f398c-191">null</span><span class="sxs-lookup"><span data-stu-id="f398c-191">null</span></span>|<span data-ttu-id="f398c-192">null</span><span class="sxs-lookup"><span data-stu-id="f398c-192">null</span></span>|<span data-ttu-id="f398c-193">null</span><span class="sxs-lookup"><span data-stu-id="f398c-193">null</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f398c-194">参照</span><span class="sxs-lookup"><span data-stu-id="f398c-194">See Also</span></span>  
 [<span data-ttu-id="f398c-195">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="f398c-195">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f398c-196">Null 許容型</span><span class="sxs-lookup"><span data-stu-id="f398c-196">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="f398c-197">Null 許容型のボックス化</span><span class="sxs-lookup"><span data-stu-id="f398c-197">Boxing Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)  
 [<span data-ttu-id="f398c-198">null 許容値型</span><span class="sxs-lookup"><span data-stu-id="f398c-198">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
