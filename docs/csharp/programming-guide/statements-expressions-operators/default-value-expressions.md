---
title: "既定の値式 (C# プログラミング ガイド)"
description: "既定の値式は、あらゆる参照型または値型の既定値を生成します"
ms.date: 2017-08-23
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
ms.assetid: b9daf449-4e64-496e-8592-6ed2c8875a98
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 1e548df4de2c07934313311a7ffcfae82be76000
ms.openlocfilehash: 7b5b53d7ed92c6f6377a3e494daf1d02a4cf0934
ms.contentlocale: ja-jp
ms.lasthandoff: 08/28/2017

---
# <a name="default-value-expressions-c-programming-guide"></a><span data-ttu-id="4ab97-103">既定の値式 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="4ab97-103">default value expressions (C# programming guide)</span></span>

<span data-ttu-id="4ab97-104">既定の値式は、型の既定値を生成します。</span><span class="sxs-lookup"><span data-stu-id="4ab97-104">A default value expression produces the default value for a type.</span></span> <span data-ttu-id="4ab97-105">既定の値式は、ジェネリック クラスおよびメソッドで特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="4ab97-105">Default value expressions are particularly useful in generic classes and methods.</span></span> <span data-ttu-id="4ab97-106">ジェネリックの使用で発生する問題の 1 つは、次のことがあらかじめわかっていない場合に、パラメーター化された型 `T` に既定値を割り当てる方法です。</span><span class="sxs-lookup"><span data-stu-id="4ab97-106">One issue that arises using generics is how to assign a default value to a parameterized type `T` when you do not know the following in advance:</span></span>

- <span data-ttu-id="4ab97-107">`T` が参照型または値型のどちらか。</span><span class="sxs-lookup"><span data-stu-id="4ab97-107">Whether `T` is a reference type or a value type.</span></span>
- <span data-ttu-id="4ab97-108">`T` が値型の場合、T は数値かユーザー定義の構造体か。</span><span class="sxs-lookup"><span data-stu-id="4ab97-108">If `T` is a value type, whether is a numeric value or a user-defined struct.</span></span>

 <span data-ttu-id="4ab97-109">パラメーター化された型 `T` の変数 `t` が指定されている場合、ステートメント `t = null` は `T` が参照型の場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="4ab97-109">Given a variable `t` of a parameterized type `T`, the statement `t = null` is only valid if `T` is a reference type.</span></span> <span data-ttu-id="4ab97-110">割り当て `t = 0` は数値型でのみ機能し、構造体では機能しません。</span><span class="sxs-lookup"><span data-stu-id="4ab97-110">The assignment `t = 0` only works for numeric value types but not for structs.</span></span> <span data-ttu-id="4ab97-111">これは、参照型 (クラスの型およびインターフェイスの型) に対して `null` を、数値型に対しては 0 を返す既定の値式を使用すると解決します。</span><span class="sxs-lookup"><span data-stu-id="4ab97-111">The solution is to use a default value expression, which returns `null` for reference types (class types and interface types) and zero for numeric value types.</span></span> <span data-ttu-id="4ab97-112">ユーザー定義の構造体の場合は、0 ビット パターンに初期化された構造体を返します。これにより、そのメンバーが値型か参照型に応じて、各メンバーに 0 または `null` が生成されます。</span><span class="sxs-lookup"><span data-stu-id="4ab97-112">For user-defined structs, it returns the struct initialized to the zero bit pattern, which produces 0 or `null` for each member depending on whether that member is a value or reference type.</span></span> <span data-ttu-id="4ab97-113">null 許容値型の場合は、`default` は構造体と同様に初期化される <xref:System.Nullable%601?displayProperty=fullName> を返します。</span><span class="sxs-lookup"><span data-stu-id="4ab97-113">For nullable value types, `default` returns a <xref:System.Nullable%601?displayProperty=fullName>, which is initialized like any struct.</span></span>

<span data-ttu-id="4ab97-114">`default(T)` 式は、ジェネリック クラスやメソッドに制限されません。</span><span class="sxs-lookup"><span data-stu-id="4ab97-114">The `default(T)` expression is not limited to generic classes and methods.</span></span> <span data-ttu-id="4ab97-115">既定の値式は、任意のマネージ型で使用できます。</span><span class="sxs-lookup"><span data-stu-id="4ab97-115">Default value expressions can be used with any managed type.</span></span> <span data-ttu-id="4ab97-116">次の式のいずれかが有効です。</span><span class="sxs-lookup"><span data-stu-id="4ab97-116">Any of these expressions are valid:</span></span>

 <span data-ttu-id="4ab97-117">[!code-cs[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]</span><span class="sxs-lookup"><span data-stu-id="4ab97-117">[!code-cs[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]</span></span>

 <span data-ttu-id="4ab97-118">`GenericList<T>` クラスの次の例は、ジェネリック クラスに `default(T)` 演算子を使う方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4ab97-118">The following example from the `GenericList<T>` class shows how to use the `default(T)` operator in a generic class.</span></span> <span data-ttu-id="4ab97-119">詳しくは、「[ジェネリックの概要](../generics/introduction-to-generics.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4ab97-119">For more information, see [Generics Overview](../generics/introduction-to-generics.md).</span></span>

 <span data-ttu-id="4ab97-120">[!code-cs[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]</span><span class="sxs-lookup"><span data-stu-id="4ab97-120">[!code-cs[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]</span></span>

## <a name="default-literal-and-type-inference"></a><span data-ttu-id="4ab97-121">既定のリテラルと型推論</span><span class="sxs-lookup"><span data-stu-id="4ab97-121">default literal and type inference</span></span>

<span data-ttu-id="4ab97-122">C# 7.1 より、コンパイラが式の型を推定できる場合、`default` リテラルを既定の値式に使用することができます。</span><span class="sxs-lookup"><span data-stu-id="4ab97-122">Beginning with C# 7.1, the `default` literal can be used for default value expressions when the compiler can infer the type of the expression.</span></span> <span data-ttu-id="4ab97-123">`default` リテラルは同等の `default(T)` (`T` は推定型) と同じ値を生成します。</span><span class="sxs-lookup"><span data-stu-id="4ab97-123">The `default` literal produces the same value as the equivalent `default(T)` where `T` is the inferred type.</span></span> <span data-ttu-id="4ab97-124">これにより、型を複数回宣言する冗長さが低減され、コードが簡潔になります。</span><span class="sxs-lookup"><span data-stu-id="4ab97-124">This can make code more concise by reducing the redundancy of declaring a type more than once.</span></span> <span data-ttu-id="4ab97-125">`default` リテラルは、次の場所のいずれかで使用できます。</span><span class="sxs-lookup"><span data-stu-id="4ab97-125">The `default` literal can be used in any of the following locations:</span></span>

- <span data-ttu-id="4ab97-126">変数初期化子</span><span class="sxs-lookup"><span data-stu-id="4ab97-126">variable initializer</span></span>
- <span data-ttu-id="4ab97-127">変数の代入</span><span class="sxs-lookup"><span data-stu-id="4ab97-127">variable assignment</span></span>
- <span data-ttu-id="4ab97-128">オプションのパラメーターの既定値の宣言</span><span class="sxs-lookup"><span data-stu-id="4ab97-128">declaring the default value for an optional parameter</span></span>
- <span data-ttu-id="4ab97-129">メソッド呼び出しの引数の値の提供</span><span class="sxs-lookup"><span data-stu-id="4ab97-129">providing the value for a method call argument</span></span>
- <span data-ttu-id="4ab97-130">return ステートメント (または式のようなメンバー内の式)</span><span class="sxs-lookup"><span data-stu-id="4ab97-130">return statement (or expression in an expression bodied member)</span></span>

<span data-ttu-id="4ab97-131">次の例は、既定の値式の `default` リテラルの多くの使用法を示しています。</span><span class="sxs-lookup"><span data-stu-id="4ab97-131">The following example shows many usages of the `default` literal in a default value expression:</span></span>

<span data-ttu-id="4ab97-132">[!code-cs[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]</span><span class="sxs-lookup"><span data-stu-id="4ab97-132">[!code-cs[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]</span></span>

## <a name="see-also"></a><span data-ttu-id="4ab97-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ab97-133">See also</span></span>

 <span data-ttu-id="4ab97-134"><xref:System.Collections.Generic> [C# プログラミング ガイド](../index.md) </span><span class="sxs-lookup"><span data-stu-id="4ab97-134"><xref:System.Collections.Generic> [C# Programming Guide](../index.md) </span></span>  
 <span data-ttu-id="4ab97-135">[ジェネリック](../generics/index.md) </span><span class="sxs-lookup"><span data-stu-id="4ab97-135">[Generics](../generics/index.md) </span></span>  
 <span data-ttu-id="4ab97-136">[ジェネリック メソッド](../generics/generic-methods.md) </span><span class="sxs-lookup"><span data-stu-id="4ab97-136">[Generic Methods](../generics/generic-methods.md) </span></span>  
 [<span data-ttu-id="4ab97-137">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="4ab97-137">Generics</span></span>](~/docs/standard/generics/index.md)   

