---
title: キャストと変換 (F#)
description: F# のプログラミング言語が提供する方法の変換演算子のさまざまなプリミティブ型間での算術変換について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: ba3cbed91bf6510a34bcb7ba89d34b0ea6b82711
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="casting-and-conversions-f"></a><span data-ttu-id="01be8-103">キャストと変換 (F#)</span><span class="sxs-lookup"><span data-stu-id="01be8-103">Casting and Conversions (F#)</span></span>

<span data-ttu-id="01be8-104">このトピックでは、f# の型変換のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="01be8-104">This topic describes support for type conversions in F#.</span></span>

## <a name="arithmetic-types"></a><span data-ttu-id="01be8-105">数値型</span><span class="sxs-lookup"><span data-stu-id="01be8-105">Arithmetic Types</span></span>
<span data-ttu-id="01be8-106">F# では、変換演算子さまざまなプリミティブ型の間での算術変換など、整数と浮動小数点型の間です。</span><span class="sxs-lookup"><span data-stu-id="01be8-106">F# provides conversion operators for arithmetic conversions between various primitive types, such as between integer and floating point types.</span></span> <span data-ttu-id="01be8-107">整数型および char 型の変換演算子がチェックとオンになっていないフォームです。浮動小数点演算の演算子と`enum`変換演算子がありません。</span><span class="sxs-lookup"><span data-stu-id="01be8-107">The integral and char conversion operators have checked and unchecked forms; the floating point operators and the `enum` conversion operator do not.</span></span> <span data-ttu-id="01be8-108">オンになっていないフォームが定義されている`Microsoft.FSharp.Core.Operators`でチェックされたフォームが定義されていると`Microsoft.FSharp.Core.Operators.Checked`です。</span><span class="sxs-lookup"><span data-stu-id="01be8-108">The unchecked forms are defined in `Microsoft.FSharp.Core.Operators` and the checked forms are defined in `Microsoft.FSharp.Core.Operators.Checked`.</span></span> <span data-ttu-id="01be8-109">チェックの形式では、オーバーフローをチェックし、結果の値が対象の型の制限を超える場合、ランタイム例外を生成します。</span><span class="sxs-lookup"><span data-stu-id="01be8-109">The checked forms check for overflow and generate a runtime exception if the resulting value exceeds the limits of the target type.</span></span>

<span data-ttu-id="01be8-110">これらの演算子は、変換先の型の名前と同じ名前です。</span><span class="sxs-lookup"><span data-stu-id="01be8-110">Each of these operators has the same name as the name of the destination type.</span></span> <span data-ttu-id="01be8-111">たとえば、次のコードを型に明示的に注釈を付ける、`byte`で 2 つの異なる意味が表示されます。</span><span class="sxs-lookup"><span data-stu-id="01be8-111">For example, in the following code, in which the types are explicitly annotated, `byte` appears with two different meanings.</span></span> <span data-ttu-id="01be8-112">最初に見つかった位置は、型であり、2 つ目は、変換演算子です。</span><span class="sxs-lookup"><span data-stu-id="01be8-112">The first occurrence is the type and the second is the conversion operator.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

<span data-ttu-id="01be8-113">次の表は、f# で定義された変換演算子を示します。</span><span class="sxs-lookup"><span data-stu-id="01be8-113">The following table shows conversion operators defined in F#.</span></span>

|<span data-ttu-id="01be8-114">演算子</span><span class="sxs-lookup"><span data-stu-id="01be8-114">Operator</span></span>|<span data-ttu-id="01be8-115">説明</span><span class="sxs-lookup"><span data-stu-id="01be8-115">Description</span></span>|
|--------|-----------|
|`byte`|<span data-ttu-id="01be8-116">バイト、8 ビット符号なしの型に変換します。</span><span class="sxs-lookup"><span data-stu-id="01be8-116">Convert to byte, an 8-bit unsigned type.</span></span>|
|`sbyte`|<span data-ttu-id="01be8-117">符号付きバイトに変換します。</span><span class="sxs-lookup"><span data-stu-id="01be8-117">Convert to signed byte.</span></span>|
|`int16`|<span data-ttu-id="01be8-118">16 ビット符号付き整数に変換します。</span><span class="sxs-lookup"><span data-stu-id="01be8-118">Convert to a 16-bit signed integer.</span></span>|
|`uint16`|<span data-ttu-id="01be8-119">16 ビット符号なし整数に変換します。</span><span class="sxs-lookup"><span data-stu-id="01be8-119">Convert to a 16-bit unsigned integer.</span></span>|
|`int32, int`|<span data-ttu-id="01be8-120">32 ビット符号付き整数に変換します。</span><span class="sxs-lookup"><span data-stu-id="01be8-120">Convert to a 32-bit signed integer.</span></span>|
|`uint32`|<span data-ttu-id="01be8-121">32 ビット符号なし整数に変換します。</span><span class="sxs-lookup"><span data-stu-id="01be8-121">Convert to a 32-bit unsigned integer.</span></span>|
|`int64`|<span data-ttu-id="01be8-122">64 ビット符号付き整数に変換します。</span><span class="sxs-lookup"><span data-stu-id="01be8-122">Convert to a 64-bit signed integer.</span></span>|
|`uint64`|<span data-ttu-id="01be8-123">64 ビット符号なし整数に変換します。</span><span class="sxs-lookup"><span data-stu-id="01be8-123">Convert to a 64-bit unsigned integer.</span></span>|
|`nativeint`|<span data-ttu-id="01be8-124">ネイティブ整数に変換します。</span><span class="sxs-lookup"><span data-stu-id="01be8-124">Convert to a native integer.</span></span>|
|`unativeint`|<span data-ttu-id="01be8-125">符号なしネイティブ整数に変換します。</span><span class="sxs-lookup"><span data-stu-id="01be8-125">Convert to an unsigned native integer.</span></span>|
|`float, double`|<span data-ttu-id="01be8-126">64 ビット IEEE 倍精度浮動小数点数に変換します。</span><span class="sxs-lookup"><span data-stu-id="01be8-126">Convert to a 64-bit double-precision IEEE floating point number.</span></span>|
|`float32, single`|<span data-ttu-id="01be8-127">32 ビット IEEE 単精度浮動小数点数に変換します。</span><span class="sxs-lookup"><span data-stu-id="01be8-127">Convert to a 32-bit single-precision IEEE floating point number.</span></span>|
|`decimal`|<span data-ttu-id="01be8-128">変換`System.Decimal`です。</span><span class="sxs-lookup"><span data-stu-id="01be8-128">Convert to `System.Decimal`.</span></span>|
|`char`|<span data-ttu-id="01be8-129">変換`System.Char`、Unicode 文字。</span><span class="sxs-lookup"><span data-stu-id="01be8-129">Convert to `System.Char`, a Unicode character.</span></span>|
|`enum`|<span data-ttu-id="01be8-130">列挙型に変換します。</span><span class="sxs-lookup"><span data-stu-id="01be8-130">Convert to an enumerated type.</span></span>|
<span data-ttu-id="01be8-131">実装する型をこれらの演算子を使用する組み込みのプリミティブ型に加えて`op_Explicit`または`op_Implicit`適切なシグネチャを持つメソッドです。</span><span class="sxs-lookup"><span data-stu-id="01be8-131">In addition to built-in primitive types, you can use these operators with types that implement `op_Explicit` or `op_Implicit` methods with appropriate signatures.</span></span> <span data-ttu-id="01be8-132">たとえば、`int`変換演算子は静的メソッドを提供する任意の型と連携`op_Explicit`をパラメーターとして型を受け取り、返します`int`です。</span><span class="sxs-lookup"><span data-stu-id="01be8-132">For example, the `int` conversion operator works with any type that provides a static method `op_Explicit` that takes the type as a parameter and returns `int`.</span></span> <span data-ttu-id="01be8-133">戻り値の型でメソッドをオーバー ロードできません、一般的な規則に特殊な例外としてこれを行う`op_Explicit`と`op_Implicit`です。</span><span class="sxs-lookup"><span data-stu-id="01be8-133">As a special exception to the general rule that methods cannot be overloaded by return type, you can do this for `op_Explicit` and `op_Implicit`.</span></span>

## <a name="enumerated-types"></a><span data-ttu-id="01be8-134">列挙型</span><span class="sxs-lookup"><span data-stu-id="01be8-134">Enumerated Types</span></span>
<span data-ttu-id="01be8-135">`enum`演算子は、一般的な演算子の型を表す 1 つの型パラメーターを受け取る、`enum`に変換します。</span><span class="sxs-lookup"><span data-stu-id="01be8-135">The `enum` operator is a generic operator that takes one type parameter that represents the type of the `enum` to convert to.</span></span> <span data-ttu-id="01be8-136">列挙型に変換するときの入力の種類を決定しようと推論、`enum`に変換します。</span><span class="sxs-lookup"><span data-stu-id="01be8-136">When it converts to an enumerated type, type inference attempts to determine the type of the `enum` that you want to convert to.</span></span> <span data-ttu-id="01be8-137">次の例では、変数`col1`明示的に注釈がありませんが、それ以降の等値テストから型を推論します。</span><span class="sxs-lookup"><span data-stu-id="01be8-137">In the following example, the variable `col1` is not explicitly annotated, but its type is inferred from the later equality test.</span></span> <span data-ttu-id="01be8-138">そのため、コンパイラに変換することを推測することができます、`Color`列挙します。</span><span class="sxs-lookup"><span data-stu-id="01be8-138">Therefore, the compiler can deduce that you are converting to a `Color` enumeration.</span></span> <span data-ttu-id="01be8-139">型の注釈を指定する代わりと同様に`col2`次の例です。</span><span class="sxs-lookup"><span data-stu-id="01be8-139">Alternatively, you can supply a type annotation, as with `col2` in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]
    
<span data-ttu-id="01be8-140">次のコードのように、型パラメーターとして明示的にターゲットの列挙型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="01be8-140">You can also specify the target enumeration type explicitly as a type parameter, as in the following code:</span></span>

```fsharp
let col3 = enum<Color> 3
```

<span data-ttu-id="01be8-141">列挙体の基になる型が変換対象の型に互換性がある場合にのみ、列挙体で作業をキャストすることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="01be8-141">Note that the enumeration casts work only if the underlying type of the enumeration is compatible with the type being converted.</span></span> <span data-ttu-id="01be8-142">次のコードでは、変換の間の不一致によりコンパイルは失敗`int32`と`uint32`です。</span><span class="sxs-lookup"><span data-stu-id="01be8-142">In the following code, the conversion fails to compile because of the mismatch between `int32` and `uint32`.</span></span>

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

<span data-ttu-id="01be8-143">詳細については、次を参照してください。[列挙](enumerations.md)です。</span><span class="sxs-lookup"><span data-stu-id="01be8-143">For more information, see [Enumerations](enumerations.md).</span></span>

## <a name="casting-object-types"></a><span data-ttu-id="01be8-144">オブジェクト型のキャスト</span><span class="sxs-lookup"><span data-stu-id="01be8-144">Casting Object Types</span></span>
<span data-ttu-id="01be8-145">オブジェクト階層内の型の間の変換は、オブジェクト指向プログラミングに不可欠です。</span><span class="sxs-lookup"><span data-stu-id="01be8-145">Conversion between types in an object hierarchy is fundamental to object-oriented programming.</span></span> <span data-ttu-id="01be8-146">変換の 2 つの基本的な種類があります: (キャスト) をキャストして、(ダウン キャスト)。</span><span class="sxs-lookup"><span data-stu-id="01be8-146">There are two basic types of conversions: casting up (upcasting) and casting down (downcasting).</span></span> <span data-ttu-id="01be8-147">階層へのキャストは、ベース オブジェクトの参照に、派生オブジェクト参照からキャストを意味します。</span><span class="sxs-lookup"><span data-stu-id="01be8-147">Casting up a hierarchy means casting from a derived object reference to a base object reference.</span></span> <span data-ttu-id="01be8-148">このようなキャストが派生クラスの継承階層内の基本クラスは時間どおりに動作する保証されます。</span><span class="sxs-lookup"><span data-stu-id="01be8-148">Such a cast is guaranteed to work as long as the base class is in the inheritance hierarchy of the derived class.</span></span> <span data-ttu-id="01be8-149">オブジェクトが実際には、適切な送信先 (派生) 型または変換先の型から派生した型のインスタンスが場合にのみ、派生オブジェクトの参照にベース オブジェクトの参照から、階層の下位へのキャストが成功します。</span><span class="sxs-lookup"><span data-stu-id="01be8-149">Casting down a hierarchy, from a base object reference to a derived object reference, succeeds only if the object actually is an instance of the correct destination (derived) type or a type derived from the destination type.</span></span>

<span data-ttu-id="01be8-150">F# の型変換演算子を提供します。</span><span class="sxs-lookup"><span data-stu-id="01be8-150">F# provides operators for these types of conversions.</span></span> <span data-ttu-id="01be8-151">`:>`まで、階層はキャスト演算子および`:?>`演算子が、階層の下位にキャストします。</span><span class="sxs-lookup"><span data-stu-id="01be8-151">The `:>` operator casts up the hierarchy, and the `:?>` operator casts down the hierarchy.</span></span>

### <a name="upcasting"></a><span data-ttu-id="01be8-152">アップ キャスト</span><span class="sxs-lookup"><span data-stu-id="01be8-152">Upcasting</span></span>
<span data-ttu-id="01be8-153">多くのオブジェクト指向言語をアップ キャストは暗黙の型です。f# では、規則は若干異なります。</span><span class="sxs-lookup"><span data-stu-id="01be8-153">In many object-oriented languages, upcasting is implicit; in F#, the rules are slightly different.</span></span> <span data-ttu-id="01be8-154">キャストは、型のオブジェクト、メソッドに引数を渡すときに自動的に適用されます。</span><span class="sxs-lookup"><span data-stu-id="01be8-154">Upcasting is applied automatically when you pass arguments to methods on an object type.</span></span> <span data-ttu-id="01be8-155">ただし、モジュール内の let-bound 関数でパラメーターの型は柔軟な型として宣言されていない限り アップ キャストは自動にされません。</span><span class="sxs-lookup"><span data-stu-id="01be8-155">However, for let-bound functions in a module, upcasting is not automatic, unless the parameter type is declared as a flexible type.</span></span> <span data-ttu-id="01be8-156">詳細については、次を参照してください。[フレキシブル型](flexible-Types.md)です。</span><span class="sxs-lookup"><span data-stu-id="01be8-156">For more information, see [Flexible Types](flexible-Types.md).</span></span>

<span data-ttu-id="01be8-157">`:>`演算子は、静的なキャスト、キャストが成功したがコンパイル時に決定されることを意味するを実行します。</span><span class="sxs-lookup"><span data-stu-id="01be8-157">The `:>` operator performs a static cast, which means that the success of the cast is determined at compile time.</span></span> <span data-ttu-id="01be8-158">キャストを使用する場合、`:>`が正常には、コンパイルが有効なキャストは、実行時に障害の可能性を持たない。</span><span class="sxs-lookup"><span data-stu-id="01be8-158">If a cast that uses `:>` compiles successfully, it is a valid cast and has no chance of failure at run time.</span></span>

<span data-ttu-id="01be8-159">使用することも、`upcast`オペレーターへの変換を実行します。</span><span class="sxs-lookup"><span data-stu-id="01be8-159">You can also use the `upcast` operator to perform such a conversion.</span></span> <span data-ttu-id="01be8-160">次の式は、階層内の上位変換を指定します。</span><span class="sxs-lookup"><span data-stu-id="01be8-160">The following expression specifies a conversion up the hierarchy:</span></span>

```fsharp
upcast expression
```

<span data-ttu-id="01be8-161">Upcast 演算子を使用する場合、コンパイラは、コンテキストからに変換する型を推論しようとします。</span><span class="sxs-lookup"><span data-stu-id="01be8-161">When you use the upcast operator, the compiler attempts to infer the type you are converting to from the context.</span></span> <span data-ttu-id="01be8-162">コンパイラがターゲットの種類を特定できない場合は、コンパイラはエラーを報告します。</span><span class="sxs-lookup"><span data-stu-id="01be8-162">If the compiler is unable to determine the target type, the compiler reports an error.</span></span>

### <a name="downcasting"></a><span data-ttu-id="01be8-163">ダウン キャスト</span><span class="sxs-lookup"><span data-stu-id="01be8-163">Downcasting</span></span>
<span data-ttu-id="01be8-164">`:?>`演算子は動的なキャスト、キャストが成功したが実行時に決定されることを意味するを実行します。</span><span class="sxs-lookup"><span data-stu-id="01be8-164">The `:?>` operator performs a dynamic cast, which means that the success of the cast is determined at run time.</span></span> <span data-ttu-id="01be8-165">使用するキャスト、`:?>`演算子は、コンパイル時にチェックされませんが、実行時にしようとしましたが、指定した型にキャストします。</span><span class="sxs-lookup"><span data-stu-id="01be8-165">A cast that uses the `:?>` operator is not checked at compile time; but at run time, an attempt is made to cast to the specified type.</span></span> <span data-ttu-id="01be8-166">オブジェクトは、対象の型と互換性が、キャストが成功します。</span><span class="sxs-lookup"><span data-stu-id="01be8-166">If the object is compatible with the target type, the cast succeeds.</span></span> <span data-ttu-id="01be8-167">ランタイムを発生させる場合は、オブジェクトは、対象の型と互換性がありません、`InvalidCastException`です。</span><span class="sxs-lookup"><span data-stu-id="01be8-167">If the object is not compatible with the target type, the runtime raises an `InvalidCastException`.</span></span>

<span data-ttu-id="01be8-168">使用することも、`downcast`演算子の動的な型変換を実行します。</span><span class="sxs-lookup"><span data-stu-id="01be8-168">You can also use the `downcast` operator to perform a dynamic type conversion.</span></span> <span data-ttu-id="01be8-169">次の式は、階層内の下位プログラム コンテキストから推論される型への変換を指定します。</span><span class="sxs-lookup"><span data-stu-id="01be8-169">The following expression specifies a conversion down the hierarchy to a type that is inferred from program context:</span></span>

```fsharp
downcast expression
```

<span data-ttu-id="01be8-170">場合と同様、`upcast`演算子、コンパイラは、コンテキストから特定のターゲット型を推論できない場合、エラーが報告されます。</span><span class="sxs-lookup"><span data-stu-id="01be8-170">As for the `upcast` operator, if the compiler cannot infer a specific target type from the context, it reports an error.</span></span>

<span data-ttu-id="01be8-171">次のコードの使用例、`:>`と`:?>`演算子。</span><span class="sxs-lookup"><span data-stu-id="01be8-171">The following code illustrates the use of the `:>` and `:?>` operators.</span></span> <span data-ttu-id="01be8-172">コードに示す、`:?>`わかっている場合に、変換が成功することをスローするため、演算子が使用される最適な`InvalidCastException`場合は、変換は失敗します。</span><span class="sxs-lookup"><span data-stu-id="01be8-172">The code illustrates that the `:?>` operator is best used when you know that conversion will succeed, because it throws `InvalidCastException` if the conversion fails.</span></span> <span data-ttu-id="01be8-173">変換が成功する、型を使用するテストがわからない場合、`match`の例外を生成によるオーバーヘッドを回避しているので、式が向上します。</span><span class="sxs-lookup"><span data-stu-id="01be8-173">If you do not know that a conversion will succeed, a type test that uses a `match` expression is better because it avoids the overhead of generating an exception.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

<span data-ttu-id="01be8-174">ジェネリック演算子`downcast`と`upcast`上記のコードで、引数と戻り値の種類を特定の型の推定に依存して、置き換えることができます</span><span class="sxs-lookup"><span data-stu-id="01be8-174">Because generic operators `downcast` and `upcast` rely on type inference to determine the argument and return type, in the above code, you can replace</span></span>

```fsharp
let base1 = d1 :> Base1
```

<span data-ttu-id="01be8-175">代入</span><span class="sxs-lookup"><span data-stu-id="01be8-175">with</span></span>

```fsharp
let base1 = upcast d1
```

<span data-ttu-id="01be8-176">前のコードで引数の型と戻り値の型が`Derived1`と`Base1`、それぞれします。</span><span class="sxs-lookup"><span data-stu-id="01be8-176">In the previous code, the argument type and return types are `Derived1` and `Base1`, respectively.</span></span>

<span data-ttu-id="01be8-177">型のテストの詳細については、次を参照してください。 [Match 式](match-Expressions.md)です。</span><span class="sxs-lookup"><span data-stu-id="01be8-177">For more information about type tests, see [Match Expressions](match-Expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="01be8-178">関連項目</span><span class="sxs-lookup"><span data-stu-id="01be8-178">See Also</span></span>
[<span data-ttu-id="01be8-179">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="01be8-179">F# Language Reference</span></span>](index.md)
