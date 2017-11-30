---
title: "既定の値式 (C# プログラミング ガイド)"
description: "既定の値式は、あらゆる参照型または値型の既定値を生成します"
ms.date: 08/23/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
ms.assetid: b9daf449-4e64-496e-8592-6ed2c8875a98
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c2bb1c269e5347d615c47ab828506aef538c4761
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="default-value-expressions-c-programming-guide"></a><span data-ttu-id="06a8b-103">既定の値式 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="06a8b-103">default value expressions (C# programming guide)</span></span>

<span data-ttu-id="06a8b-104">既定の値式は、型の既定値を生成します。</span><span class="sxs-lookup"><span data-stu-id="06a8b-104">A default value expression produces the default value for a type.</span></span> <span data-ttu-id="06a8b-105">既定の値式は、ジェネリック クラスおよびメソッドで特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="06a8b-105">Default value expressions are particularly useful in generic classes and methods.</span></span> <span data-ttu-id="06a8b-106">ジェネリックの使用で発生する問題の 1 つは、次のことがあらかじめわかっていない場合に、パラメーター化された型 `T` に既定値を割り当てる方法です。</span><span class="sxs-lookup"><span data-stu-id="06a8b-106">One issue that arises using generics is how to assign a default value to a parameterized type `T` when you do not know the following in advance:</span></span>

- <span data-ttu-id="06a8b-107">`T` が参照型または値型のどちらか。</span><span class="sxs-lookup"><span data-stu-id="06a8b-107">Whether `T` is a reference type or a value type.</span></span>
- <span data-ttu-id="06a8b-108">`T` が値型の場合、T は数値かユーザー定義の構造体か。</span><span class="sxs-lookup"><span data-stu-id="06a8b-108">If `T` is a value type, whether is a numeric value or a user-defined struct.</span></span>

 <span data-ttu-id="06a8b-109">パラメーター化された型 `T` の変数 `t` が指定されている場合、ステートメント `t = null` は `T` が参照型の場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="06a8b-109">Given a variable `t` of a parameterized type `T`, the statement `t = null` is only valid if `T` is a reference type.</span></span> <span data-ttu-id="06a8b-110">割り当て `t = 0` は数値型でのみ機能し、構造体では機能しません。</span><span class="sxs-lookup"><span data-stu-id="06a8b-110">The assignment `t = 0` only works for numeric value types but not for structs.</span></span> <span data-ttu-id="06a8b-111">これは、参照型 (クラスの型およびインターフェイスの型) に対して `null` を、数値型に対しては 0 を返す既定の値式を使用すると解決します。</span><span class="sxs-lookup"><span data-stu-id="06a8b-111">The solution is to use a default value expression, which returns `null` for reference types (class types and interface types) and zero for numeric value types.</span></span> <span data-ttu-id="06a8b-112">ユーザー定義の構造体の場合は、0 ビット パターンに初期化された構造体を返します。これにより、そのメンバーが値型か参照型に応じて、各メンバーに 0 または `null` が生成されます。</span><span class="sxs-lookup"><span data-stu-id="06a8b-112">For user-defined structs, it returns the struct initialized to the zero bit pattern, which produces 0 or `null` for each member depending on whether that member is a value or reference type.</span></span> <span data-ttu-id="06a8b-113">null 許容値型の場合は、`default` は構造体と同様に初期化される <xref:System.Nullable%601?displayProperty=nameWithType> を返します。</span><span class="sxs-lookup"><span data-stu-id="06a8b-113">For nullable value types, `default` returns a <xref:System.Nullable%601?displayProperty=nameWithType>, which is initialized like any struct.</span></span>

<span data-ttu-id="06a8b-114">`default(T)` 式は、ジェネリック クラスやメソッドに制限されません。</span><span class="sxs-lookup"><span data-stu-id="06a8b-114">The `default(T)` expression is not limited to generic classes and methods.</span></span> <span data-ttu-id="06a8b-115">既定の値式は、任意のマネージ型で使用できます。</span><span class="sxs-lookup"><span data-stu-id="06a8b-115">Default value expressions can be used with any managed type.</span></span> <span data-ttu-id="06a8b-116">次の式のいずれかが有効です。</span><span class="sxs-lookup"><span data-stu-id="06a8b-116">Any of these expressions are valid:</span></span>

 [!code-csharp[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]

 <span data-ttu-id="06a8b-117">`GenericList<T>` クラスの次の例は、ジェネリック クラスに `default(T)` 演算子を使う方法を示します。</span><span class="sxs-lookup"><span data-stu-id="06a8b-117">The following example from the `GenericList<T>` class shows how to use the `default(T)` operator in a generic class.</span></span> <span data-ttu-id="06a8b-118">詳しくは、「[ジェネリックの概要](../generics/introduction-to-generics.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="06a8b-118">For more information, see [Generics Overview](../generics/introduction-to-generics.md).</span></span>

 [!code-csharp[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]

## <a name="default-literal-and-type-inference"></a><span data-ttu-id="06a8b-119">既定のリテラルと型推論</span><span class="sxs-lookup"><span data-stu-id="06a8b-119">default literal and type inference</span></span>

<span data-ttu-id="06a8b-120">C# 7.1 より、コンパイラが式の型を推定できる場合、`default` リテラルを既定の値式に使用することができます。</span><span class="sxs-lookup"><span data-stu-id="06a8b-120">Beginning with C# 7.1, the `default` literal can be used for default value expressions when the compiler can infer the type of the expression.</span></span> <span data-ttu-id="06a8b-121">`default` リテラルは同等の `default(T)` (`T` は推定型) と同じ値を生成します。</span><span class="sxs-lookup"><span data-stu-id="06a8b-121">The `default` literal produces the same value as the equivalent `default(T)` where `T` is the inferred type.</span></span> <span data-ttu-id="06a8b-122">これにより、型を複数回宣言する冗長さが低減され、コードが簡潔になります。</span><span class="sxs-lookup"><span data-stu-id="06a8b-122">This can make code more concise by reducing the redundancy of declaring a type more than once.</span></span> <span data-ttu-id="06a8b-123">`default` リテラルは、次の場所のいずれかで使用できます。</span><span class="sxs-lookup"><span data-stu-id="06a8b-123">The `default` literal can be used in any of the following locations:</span></span>

- <span data-ttu-id="06a8b-124">変数初期化子</span><span class="sxs-lookup"><span data-stu-id="06a8b-124">variable initializer</span></span>
- <span data-ttu-id="06a8b-125">変数の代入</span><span class="sxs-lookup"><span data-stu-id="06a8b-125">variable assignment</span></span>
- <span data-ttu-id="06a8b-126">オプションのパラメーターの既定値の宣言</span><span class="sxs-lookup"><span data-stu-id="06a8b-126">declaring the default value for an optional parameter</span></span>
- <span data-ttu-id="06a8b-127">メソッド呼び出しの引数の値の提供</span><span class="sxs-lookup"><span data-stu-id="06a8b-127">providing the value for a method call argument</span></span>
- <span data-ttu-id="06a8b-128">return ステートメント (または式のようなメンバー内の式)</span><span class="sxs-lookup"><span data-stu-id="06a8b-128">return statement (or expression in an expression bodied member)</span></span>

<span data-ttu-id="06a8b-129">次の例は、既定の値式の `default` リテラルの多くの使用法を示しています。</span><span class="sxs-lookup"><span data-stu-id="06a8b-129">The following example shows many usages of the `default` literal in a default value expression:</span></span>

[!code-csharp[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]

## <a name="see-also"></a><span data-ttu-id="06a8b-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="06a8b-130">See also</span></span>

 <span data-ttu-id="06a8b-131"><xref:System.Collections.Generic>[C# プログラミング ガイド](../index.md)</span><span class="sxs-lookup"><span data-stu-id="06a8b-131"><xref:System.Collections.Generic> [C# Programming Guide](../index.md)</span></span>  
 [<span data-ttu-id="06a8b-132">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="06a8b-132">Generics</span></span>](../generics/index.md)  
 [<span data-ttu-id="06a8b-133">ジェネリック メソッド</span><span class="sxs-lookup"><span data-stu-id="06a8b-133">Generic Methods</span></span>](../generics/generic-methods.md)  
 [<span data-ttu-id="06a8b-134">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="06a8b-134">Generics</span></span>](~/docs/standard/generics/index.md)  
