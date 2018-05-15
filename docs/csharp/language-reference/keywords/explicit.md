---
title: explicit (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- explicit_CSharpKeyword
- explicit
helpviewer_keywords:
- explicit keyword [C#]
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
ms.openlocfilehash: c8a05aef3318eb34242ed1268ea26663592e4d1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="explicit-c-reference"></a><span data-ttu-id="dd700-102">explicit (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="dd700-102">explicit (C# Reference)</span></span>
<span data-ttu-id="dd700-103">`explicit` キーワードは、キャストを使用して呼び出す必要があるユーザー定義型変換演算子を宣言します。</span><span class="sxs-lookup"><span data-stu-id="dd700-103">The `explicit` keyword declares a user-defined type conversion operator that must be invoked with a cast.</span></span> <span data-ttu-id="dd700-104">たとえば、次の演算子は摂氏というクラスを華氏というクラスに変換します。</span><span class="sxs-lookup"><span data-stu-id="dd700-104">For example, this operator converts from a class called Fahrenheit to a class called Celsius:</span></span>  
  
 [!code-csharp[csrefKeywordsConversion#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_1.cs)]  
  
 <span data-ttu-id="dd700-105">この変換演算子は、次のように呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="dd700-105">This conversion operator can be invoked like this:</span></span>  
  
 [!code-csharp[csrefKeywordsConversion#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_2.cs)]  
  
 <span data-ttu-id="dd700-106">変換演算子は、ソースの型をターゲットの型に変換します。</span><span class="sxs-lookup"><span data-stu-id="dd700-106">The conversion operator converts from a source type to a target type.</span></span> <span data-ttu-id="dd700-107">変換演算子はソースの型によって提供されます。</span><span class="sxs-lookup"><span data-stu-id="dd700-107">The source type provides the conversion operator.</span></span> <span data-ttu-id="dd700-108">暗黙的な変換とは異なり、変換演算子はキャストを使用して明示的に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd700-108">Unlike implicit conversion, explicit conversion operators must be invoked by means of a cast.</span></span> <span data-ttu-id="dd700-109">変換操作によって例外が発生したり、情報が失われる可能性がある場合は、その操作を `explicit` としてマークする必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd700-109">If a conversion operation can cause exceptions or lose information, you should mark it `explicit`.</span></span> <span data-ttu-id="dd700-110">これにより、予期しない結果をもたらす可能性がある変換操作がコンパイラによって暗黙的に呼び出されるのを防止できます。</span><span class="sxs-lookup"><span data-stu-id="dd700-110">This prevents the compiler from silently invoking the conversion operation with possibly unforeseen consequences.</span></span>  
  
 <span data-ttu-id="dd700-111">キャストを省略すると、コンパイル時エラー CS0266 が返されます。</span><span class="sxs-lookup"><span data-stu-id="dd700-111">Omitting the cast results in compile-time error CS0266.</span></span>  
  
 <span data-ttu-id="dd700-112">詳しくは、「[変換演算子の使用](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="dd700-112">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd700-113">例</span><span class="sxs-lookup"><span data-stu-id="dd700-113">Example</span></span>  
 <span data-ttu-id="dd700-114">次のコードは、`Fahrenheit` クラスと `Celsius` クラスを提供する場合の例です。これらの各クラスは、他方のクラスへの明示的な変換演算子を提供します。</span><span class="sxs-lookup"><span data-stu-id="dd700-114">The following example provides a `Fahrenheit` and a `Celsius` class, each of which provides an explicit conversion operator to the other class.</span></span>  
  
 [!code-csharp[csrefKeywordsConversion#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="dd700-115">例</span><span class="sxs-lookup"><span data-stu-id="dd700-115">Example</span></span>  
 <span data-ttu-id="dd700-116">次のコードは、単一の 10 進数を表す構造体 (`Digit`) を定義する場合の例です。</span><span class="sxs-lookup"><span data-stu-id="dd700-116">The following example defines a struct, `Digit`, that represents a single decimal digit.</span></span> <span data-ttu-id="dd700-117">`byte` を `Digit` に変換するための演算子が定義されていますが、すべてのバイトを `Digit` に変換できるとは限らないため、変換を explicit にしています。</span><span class="sxs-lookup"><span data-stu-id="dd700-117">An operator is defined for conversions from `byte` to `Digit`, but because not all bytes can be converted to a `Digit`, the conversion is explicit.</span></span>  
  
 [!code-csharp[csrefKeywordsConversion#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_4.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="dd700-118">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="dd700-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dd700-119">参照</span><span class="sxs-lookup"><span data-stu-id="dd700-119">See Also</span></span>  
 [<span data-ttu-id="dd700-120">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="dd700-120">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="dd700-121">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="dd700-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="dd700-122">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="dd700-122">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="dd700-123">implicit</span><span class="sxs-lookup"><span data-stu-id="dd700-123">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
 [<span data-ttu-id="dd700-124">演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="dd700-124">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)  
 [<span data-ttu-id="dd700-125">方法: 構造体間にユーザー定義の変換を実装する</span><span class="sxs-lookup"><span data-stu-id="dd700-125">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
 <span data-ttu-id="dd700-126">[Chained user-defined explicit conversions in C#](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/) (C# でのユーザー定義の明示的変換の連結)</span><span class="sxs-lookup"><span data-stu-id="dd700-126">[Chained user-defined explicit conversions in C#](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)</span></span>
