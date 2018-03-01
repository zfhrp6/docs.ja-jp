---
title: "implicit (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- implicit
- implicit_CSharpKeyword
helpviewer_keywords:
- implicit keyword [C#]
ms.assetid: 34db590e-eb3a-4f11-88d0-ffb3cd753dab
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c893c7a9afbdc6f715010d537e9ccaf66c5785c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="implicit-c-reference"></a><span data-ttu-id="7f715-102">implicit (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="7f715-102">implicit (C# Reference)</span></span>
<span data-ttu-id="7f715-103">`implicit` キーワードを使用して、暗黙のユーザー定義型変換演算子を宣言します。</span><span class="sxs-lookup"><span data-stu-id="7f715-103">The `implicit` keyword is used to declare an implicit user-defined type conversion operator.</span></span> <span data-ttu-id="7f715-104">変換を実行してもデータ損失が発生しないことが保証されている場合に、ユーザー定義型とその他の型との間の暗黙の変換を有効にするために使用します。</span><span class="sxs-lookup"><span data-stu-id="7f715-104">Use it to enable implicit conversions between a user-defined type and another type, if the conversion is guaranteed not to cause a loss of data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f715-105">例</span><span class="sxs-lookup"><span data-stu-id="7f715-105">Example</span></span>  
 [!code-csharp[csrefKeywordsConversion#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicit_1.cs)]  
  
 <span data-ttu-id="7f715-106">暗黙の変換では不要なキャストを省略できるため、ソース コードが読みやすくなります。</span><span class="sxs-lookup"><span data-stu-id="7f715-106">By eliminating unnecessary casts, implicit conversions can improve source code readability.</span></span> <span data-ttu-id="7f715-107">ただし、暗黙の変換では、一方の型からもう一方の型に明示的にキャストする必要がないため、予期しない結果が生じないように注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f715-107">However, because implicit conversions do not require programmers to explicitly cast from one type to the other, care must be taken to prevent unexpected results.</span></span> <span data-ttu-id="7f715-108">プログラマーが意識しなくても安全に使用できるように、通常、暗黙の変換演算子は、例外をスローしたり情報を失ったりしてはなりません。</span><span class="sxs-lookup"><span data-stu-id="7f715-108">In general, implicit conversion operators should never throw exceptions and never lose information so that they can be used safely without the programmer's awareness.</span></span> <span data-ttu-id="7f715-109">このような条件を満たすことができない変換演算子は、`explicit` でマークする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f715-109">If a conversion operator cannot meet those criteria, it should be marked `explicit`.</span></span> <span data-ttu-id="7f715-110">詳細については、「[変換演算子の使用](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f715-110">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="7f715-111">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="7f715-111">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7f715-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="7f715-112">See Also</span></span>  
 [<span data-ttu-id="7f715-113">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="7f715-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="7f715-114">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="7f715-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7f715-115">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="7f715-115">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="7f715-116">explicit</span><span class="sxs-lookup"><span data-stu-id="7f715-116">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
 [<span data-ttu-id="7f715-117">演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="7f715-117">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)  
 [<span data-ttu-id="7f715-118">方法: 構造体間にユーザー定義の変換を実装する</span><span class="sxs-lookup"><span data-stu-id="7f715-118">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
