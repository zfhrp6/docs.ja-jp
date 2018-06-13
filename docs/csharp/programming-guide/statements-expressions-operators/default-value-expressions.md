---
title: 既定の値式 (C# プログラミング ガイド)
description: 既定の値式は、あらゆる参照型または値型の既定値を生成します
ms.date: 04/25/2018
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
ms.openlocfilehash: be51ad253a2939f538144caf4500f39e144c1664
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33336802"
---
# <a name="default-value-expressions-c-programming-guide"></a><span data-ttu-id="aa83e-103">既定の値式 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="aa83e-103">default value expressions (C# programming guide)</span></span>

<span data-ttu-id="aa83e-104">既定の値式 `default(T)` では、型 `T` の既定値が生成されます。</span><span class="sxs-lookup"><span data-stu-id="aa83e-104">A default value expression `default(T)` produces the default value of a type `T`.</span></span> <span data-ttu-id="aa83e-105">次の表は、さまざまな型に対して生成される値の一覧です。</span><span class="sxs-lookup"><span data-stu-id="aa83e-105">The following table shows which values are produced for various types:</span></span>

|<span data-ttu-id="aa83e-106">型</span><span class="sxs-lookup"><span data-stu-id="aa83e-106">Type</span></span>|<span data-ttu-id="aa83e-107">既定値</span><span class="sxs-lookup"><span data-stu-id="aa83e-107">Default value</span></span>|
|---------|---------|
|<span data-ttu-id="aa83e-108">すべての参照型</span><span class="sxs-lookup"><span data-stu-id="aa83e-108">Any reference type</span></span>|`null`|
|<span data-ttu-id="aa83e-109">数値型</span><span class="sxs-lookup"><span data-stu-id="aa83e-109">Numeric value type</span></span>|<span data-ttu-id="aa83e-110">0</span><span class="sxs-lookup"><span data-stu-id="aa83e-110">Zero</span></span>|
|[<span data-ttu-id="aa83e-111">bool</span><span class="sxs-lookup"><span data-stu-id="aa83e-111">bool</span></span>](../../language-reference/keywords/bool.md)|`false`|
|[<span data-ttu-id="aa83e-112">char</span><span class="sxs-lookup"><span data-stu-id="aa83e-112">char</span></span>](../../language-reference/keywords/char.md)|`'\0'`|
|[<span data-ttu-id="aa83e-113">enum</span><span class="sxs-lookup"><span data-stu-id="aa83e-113">enum</span></span>](../../language-reference/keywords/enum.md)|<span data-ttu-id="aa83e-114">式 `(E)0` によって生成される値。`E` は列挙型識別子です。</span><span class="sxs-lookup"><span data-stu-id="aa83e-114">The value produced by the expression `(E)0`, where `E` is the enum identifier.</span></span>|
|[<span data-ttu-id="aa83e-115">struct</span><span class="sxs-lookup"><span data-stu-id="aa83e-115">struct</span></span>](../../language-reference/keywords/struct.md)|<span data-ttu-id="aa83e-116">すべての値型フィールドが既定値に設定され、すべての参照型フィールドが `null` に設定された値。</span><span class="sxs-lookup"><span data-stu-id="aa83e-116">The value produced by setting all value type fields to their default value and all reference type fields to `null`.</span></span>|
|<span data-ttu-id="aa83e-117">null 許容型</span><span class="sxs-lookup"><span data-stu-id="aa83e-117">Nullable type</span></span>|<span data-ttu-id="aa83e-118"><xref:System.Nullable%601.HasValue%2A> プロパティが `false` で、<xref:System.Nullable%601.Value%2A> プロパティが未定義のインスタンス。</span><span class="sxs-lookup"><span data-stu-id="aa83e-118">An instance for which the <xref:System.Nullable%601.HasValue%2A> property is `false` and the <xref:System.Nullable%601.Value%2A> property is undefined.</span></span>|

<span data-ttu-id="aa83e-119">既定の値式は、ジェネリック クラスおよびメソッドで特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="aa83e-119">Default value expressions are particularly useful in generic classes and methods.</span></span> <span data-ttu-id="aa83e-120">ジェネリックの使用で発生する問題の 1 つは、次のことがあらかじめわかっていない場合に、パラメーター化された型 `T` に既定値を割り当てる方法です。</span><span class="sxs-lookup"><span data-stu-id="aa83e-120">One issue that arises using generics is how to assign a default value of a parameterized type `T` when you don't know the following in advance:</span></span>

- <span data-ttu-id="aa83e-121">`T` が参照型または値型のどちらか。</span><span class="sxs-lookup"><span data-stu-id="aa83e-121">Whether `T` is a reference type or a value type.</span></span>
- <span data-ttu-id="aa83e-122">`T` が値型の場合、数値か構造体か。</span><span class="sxs-lookup"><span data-stu-id="aa83e-122">If `T` is a value type, whether it's a numeric value or a struct.</span></span>

 <span data-ttu-id="aa83e-123">パラメーター化された型 `T` の変数 `t` が指定されている場合、ステートメント `t = null` は `T` が参照型の場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="aa83e-123">Given a variable `t` of a parameterized type `T`, the statement `t = null` is only valid if `T` is a reference type.</span></span> <span data-ttu-id="aa83e-124">割り当て `t = 0` は数値型でのみ機能し、構造体では機能しません。</span><span class="sxs-lookup"><span data-stu-id="aa83e-124">The assignment `t = 0` only works for numeric value types but not for structs.</span></span> <span data-ttu-id="aa83e-125">これを解決するには、既定の値式を使用します。</span><span class="sxs-lookup"><span data-stu-id="aa83e-125">To solve that, use a default value expression:</span></span>

```csharp
T t = default(T);
```

<span data-ttu-id="aa83e-126">`default(T)` 式は、ジェネリック クラスやメソッドに制限されません。</span><span class="sxs-lookup"><span data-stu-id="aa83e-126">The `default(T)` expression is not limited to generic classes and methods.</span></span> <span data-ttu-id="aa83e-127">既定の値式は、任意のマネージ型で使用できます。</span><span class="sxs-lookup"><span data-stu-id="aa83e-127">Default value expressions can be used with any managed type.</span></span> <span data-ttu-id="aa83e-128">次の式のいずれかが有効です。</span><span class="sxs-lookup"><span data-stu-id="aa83e-128">Any of these expressions are valid:</span></span>

 [!code-csharp[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]

 <span data-ttu-id="aa83e-129">`GenericList<T>` クラスの次の例は、ジェネリック クラスに `default(T)` 演算子を使う方法を示します。</span><span class="sxs-lookup"><span data-stu-id="aa83e-129">The following example from the `GenericList<T>` class shows how to use the `default(T)` operator in a generic class.</span></span> <span data-ttu-id="aa83e-130">詳細については、「[ジェネリックの概要](../generics/introduction-to-generics.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa83e-130">For more information, see [Introduction to Generics](../generics/introduction-to-generics.md).</span></span>

 [!code-csharp[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]

## <a name="default-literal-and-type-inference"></a><span data-ttu-id="aa83e-131">既定のリテラルと型推論</span><span class="sxs-lookup"><span data-stu-id="aa83e-131">default literal and type inference</span></span>

<span data-ttu-id="aa83e-132">C# 7.1 より、コンパイラが式の型を推定できる場合、`default` リテラルを既定の値式に使用することができます。</span><span class="sxs-lookup"><span data-stu-id="aa83e-132">Beginning with C# 7.1, the `default` literal can be used for default value expressions when the compiler can infer the type of the expression.</span></span> <span data-ttu-id="aa83e-133">`default` リテラルは同等の `default(T)` (`T` は推定型) と同じ値を生成します。</span><span class="sxs-lookup"><span data-stu-id="aa83e-133">The `default` literal produces the same value as the equivalent `default(T)` where `T` is the inferred type.</span></span> <span data-ttu-id="aa83e-134">これにより、型を複数回宣言する冗長さが低減され、コードが簡潔になります。</span><span class="sxs-lookup"><span data-stu-id="aa83e-134">This can make code more concise by reducing the redundancy of declaring a type more than once.</span></span> <span data-ttu-id="aa83e-135">`default` リテラルは、次の場所のいずれかで使用できます。</span><span class="sxs-lookup"><span data-stu-id="aa83e-135">The `default` literal can be used in any of the following locations:</span></span>

- <span data-ttu-id="aa83e-136">変数初期化子</span><span class="sxs-lookup"><span data-stu-id="aa83e-136">variable initializer</span></span>
- <span data-ttu-id="aa83e-137">変数の代入</span><span class="sxs-lookup"><span data-stu-id="aa83e-137">variable assignment</span></span>
- <span data-ttu-id="aa83e-138">オプションのパラメーターの既定値の宣言</span><span class="sxs-lookup"><span data-stu-id="aa83e-138">declaring the default value for an optional parameter</span></span>
- <span data-ttu-id="aa83e-139">メソッド呼び出しの引数の値の提供</span><span class="sxs-lookup"><span data-stu-id="aa83e-139">providing the value for a method call argument</span></span>
- <span data-ttu-id="aa83e-140">return ステートメント (または式のようなメンバー内の式)</span><span class="sxs-lookup"><span data-stu-id="aa83e-140">return statement (or expression in an expression bodied member)</span></span>

<span data-ttu-id="aa83e-141">次の例は、既定の値式の `default` リテラルの多くの使用法を示しています。</span><span class="sxs-lookup"><span data-stu-id="aa83e-141">The following example shows many usages of the `default` literal in a default value expression:</span></span>

[!code-csharp[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]

## <a name="see-also"></a><span data-ttu-id="aa83e-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="aa83e-142">See also</span></span>

 <xref:System.Collections.Generic>  
 [<span data-ttu-id="aa83e-143">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="aa83e-143">C# Programming Guide</span></span>](../index.md)  
 [<span data-ttu-id="aa83e-144">ジェネリック (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="aa83e-144">Generics (C# Programming Guide)</span></span>](../generics/index.md)  
 [<span data-ttu-id="aa83e-145">ジェネリック メソッド</span><span class="sxs-lookup"><span data-stu-id="aa83e-145">Generic Methods</span></span>](../generics/generic-methods.md)  
 [<span data-ttu-id="aa83e-146">.NET のジェネリック</span><span class="sxs-lookup"><span data-stu-id="aa83e-146">Generics in .NET</span></span>](~/docs/standard/generics/index.md)  
 [<span data-ttu-id="aa83e-147">既定値の一覧表</span><span class="sxs-lookup"><span data-stu-id="aa83e-147">Default values table</span></span>](../../language-reference/keywords/default-values-table.md)
