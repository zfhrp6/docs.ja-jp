---
title: "explicit (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- explicit_CSharpKeyword
- explicit
dev_langs:
- CSharp
helpviewer_keywords:
- explicit keyword [C#]
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f11a930f0be5d504c92271b66009613de5d68579
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="explicit-c-reference"></a><span data-ttu-id="f3f71-102">explicit (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="f3f71-102">explicit (C# Reference)</span></span>
<span data-ttu-id="f3f71-103">`explicit` キーワードは、キャストを使用して呼び出す必要があるユーザー定義型変換演算子を宣言します。</span><span class="sxs-lookup"><span data-stu-id="f3f71-103">The `explicit` keyword declares a user-defined type conversion operator that must be invoked with a cast.</span></span> <span data-ttu-id="f3f71-104">たとえば、次の演算子は摂氏というクラスを華氏というクラスに変換します。</span><span class="sxs-lookup"><span data-stu-id="f3f71-104">For example, this operator converts from a class called Fahrenheit to a class called Celsius:</span></span>  
  
 <span data-ttu-id="f3f71-105">[!code-cs[csrefKeywordsConversion#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f3f71-105">[!code-cs[csrefKeywordsConversion#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_1.cs)]</span></span>  
  
 <span data-ttu-id="f3f71-106">この変換演算子は、次のように呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="f3f71-106">This conversion operator can be invoked like this:</span></span>  
  
 <span data-ttu-id="f3f71-107">[!code-cs[csrefKeywordsConversion#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="f3f71-107">[!code-cs[csrefKeywordsConversion#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_2.cs)]</span></span>  
  
 <span data-ttu-id="f3f71-108">変換演算子は、ソースの型をターゲットの型に変換します。</span><span class="sxs-lookup"><span data-stu-id="f3f71-108">The conversion operator converts from a source type to a target type.</span></span> <span data-ttu-id="f3f71-109">変換演算子はソースの型によって提供されます。</span><span class="sxs-lookup"><span data-stu-id="f3f71-109">The source type provides the conversion operator.</span></span> <span data-ttu-id="f3f71-110">暗黙的な変換とは異なり、変換演算子はキャストを使用して明示的に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3f71-110">Unlike implicit conversion, explicit conversion operators must be invoked by means of a cast.</span></span> <span data-ttu-id="f3f71-111">変換操作によって例外が発生したり、情報が失われる可能性がある場合は、その操作を `explicit` としてマークする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3f71-111">If a conversion operation can cause exceptions or lose information, you should mark it `explicit`.</span></span> <span data-ttu-id="f3f71-112">これにより、予期しない結果をもたらす可能性がある変換操作がコンパイラによって暗黙的に呼び出されるのを防止できます。</span><span class="sxs-lookup"><span data-stu-id="f3f71-112">This prevents the compiler from silently invoking the conversion operation with possibly unforeseen consequences.</span></span>  
  
 <span data-ttu-id="f3f71-113">キャストを省略すると、コンパイル時エラー CS0266 が返されます。</span><span class="sxs-lookup"><span data-stu-id="f3f71-113">Omitting the cast results in compile-time error CS0266.</span></span>  
  
 <span data-ttu-id="f3f71-114">詳しくは、「[変換演算子の使用](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f3f71-114">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3f71-115">例</span><span class="sxs-lookup"><span data-stu-id="f3f71-115">Example</span></span>  
 <span data-ttu-id="f3f71-116">次のコードは、`Fahrenheit` クラスと `Celsius` クラスを提供する場合の例です。これらの各クラスは、他方のクラスへの明示的な変換演算子を提供します。</span><span class="sxs-lookup"><span data-stu-id="f3f71-116">The following example provides a `Fahrenheit` and a `Celsius` class, each of which provides an explicit conversion operator to the other class.</span></span>  
  
 <span data-ttu-id="f3f71-117">[!code-cs[csrefKeywordsConversion#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="f3f71-117">[!code-cs[csrefKeywordsConversion#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_3.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3f71-118">例</span><span class="sxs-lookup"><span data-stu-id="f3f71-118">Example</span></span>  
 <span data-ttu-id="f3f71-119">次のコードは、単一の 10 進数を表す構造体 (`Digit`) を定義する場合の例です。</span><span class="sxs-lookup"><span data-stu-id="f3f71-119">The following example defines a struct, `Digit`, that represents a single decimal digit.</span></span> <span data-ttu-id="f3f71-120">`byte` を `Digit` に変換するための演算子が定義されていますが、すべてのバイトを `Digit` に変換できるとは限らないため、変換を explicit にしています。</span><span class="sxs-lookup"><span data-stu-id="f3f71-120">An operator is defined for conversions from `byte` to `Digit`, but because not all bytes can be converted to a `Digit`, the conversion is explicit.</span></span>  
  
 <span data-ttu-id="f3f71-121">[!code-cs[csrefKeywordsConversion#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="f3f71-121">[!code-cs[csrefKeywordsConversion#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_4.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="f3f71-122">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="f3f71-122">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f3f71-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="f3f71-123">See Also</span></span>  
 <span data-ttu-id="f3f71-124">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="f3f71-124">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="f3f71-125">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f3f71-125">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="f3f71-126">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="f3f71-126">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="f3f71-127">[implicit](../../../csharp/language-reference/keywords/implicit.md) </span><span class="sxs-lookup"><span data-stu-id="f3f71-127">[implicit](../../../csharp/language-reference/keywords/implicit.md) </span></span>  
 <span data-ttu-id="f3f71-128">[演算子 (C# リファレンス)](../../../csharp/language-reference/keywords/operator.md) </span><span class="sxs-lookup"><span data-stu-id="f3f71-128">[operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md) </span></span>  
 <span data-ttu-id="f3f71-129">[方法: 構造体間にユーザー定義の変換を実装する](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md) </span><span class="sxs-lookup"><span data-stu-id="f3f71-129">[How to: Implement User-Defined Conversions Between Structs](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md) </span></span>  
 <span data-ttu-id="f3f71-130">[Chained user-defined explicit conversions in C#](http://go.microsoft.com/fwlink/?LinkId=112384) (C# でのユーザー定義の明示的変換の連結)</span><span class="sxs-lookup"><span data-stu-id="f3f71-130">[Chained user-defined explicit conversions in C#](http://go.microsoft.com/fwlink/?LinkId=112384)</span></span>

