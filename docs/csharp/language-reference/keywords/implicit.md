---
title: "implicit (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- implicit
- implicit_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- implicit keyword [C#]
ms.assetid: 34db590e-eb3a-4f11-88d0-ffb3cd753dab
caps.latest.revision: 19
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
ms.openlocfilehash: e4452a3bb6da2d0d294ca26d6b957f2c1c4402fd
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="implicit-c-reference"></a><span data-ttu-id="99970-102">implicit (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="99970-102">implicit (C# Reference)</span></span>
<span data-ttu-id="99970-103">`implicit` キーワードを使用して、暗黙のユーザー定義型変換演算子を宣言します。</span><span class="sxs-lookup"><span data-stu-id="99970-103">The `implicit` keyword is used to declare an implicit user-defined type conversion operator.</span></span> <span data-ttu-id="99970-104">変換を実行してもデータ損失が発生しないことが保証されている場合に、ユーザー定義型とその他の型との間の暗黙の変換を有効にするために使用します。</span><span class="sxs-lookup"><span data-stu-id="99970-104">Use it to enable implicit conversions between a user-defined type and another type, if the conversion is guaranteed not to cause a loss of data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99970-105">例</span><span class="sxs-lookup"><span data-stu-id="99970-105">Example</span></span>  
 <span data-ttu-id="99970-106">[!code-cs[csrefKeywordsConversion#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicit_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="99970-106">[!code-cs[csrefKeywordsConversion#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicit_1.cs)]</span></span>  
  
 <span data-ttu-id="99970-107">暗黙の変換では不要なキャストを省略できるため、ソース コードが読みやすくなります。</span><span class="sxs-lookup"><span data-stu-id="99970-107">By eliminating unnecessary casts, implicit conversions can improve source code readability.</span></span> <span data-ttu-id="99970-108">ただし、暗黙の変換では、一方の型からもう一方の型に明示的にキャストする必要がないため、予期しない結果が生じないように注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="99970-108">However, because implicit conversions do not require programmers to explicitly cast from one type to the other, care must be taken to prevent unexpected results.</span></span> <span data-ttu-id="99970-109">プログラマーが意識しなくても安全に使用できるように、通常、暗黙の変換演算子は、例外をスローしたり情報を失ったりしてはなりません。</span><span class="sxs-lookup"><span data-stu-id="99970-109">In general, implicit conversion operators should never throw exceptions and never lose information so that they can be used safely without the programmer's awareness.</span></span> <span data-ttu-id="99970-110">このような条件を満たすことができない変換演算子は、`explicit` でマークする必要があります。</span><span class="sxs-lookup"><span data-stu-id="99970-110">If a conversion operator cannot meet those criteria, it should be marked `explicit`.</span></span> <span data-ttu-id="99970-111">詳細については、「[変換演算子の使用](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99970-111">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="99970-112">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="99970-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="99970-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="99970-113">See Also</span></span>  
 <span data-ttu-id="99970-114">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="99970-114">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="99970-115">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="99970-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="99970-116">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="99970-116">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="99970-117">[explicit](../../../csharp/language-reference/keywords/explicit.md) </span><span class="sxs-lookup"><span data-stu-id="99970-117">[explicit](../../../csharp/language-reference/keywords/explicit.md) </span></span>  
 <span data-ttu-id="99970-118">[operator (C# リファレンス)](../../../csharp/language-reference/keywords/operator.md) </span><span class="sxs-lookup"><span data-stu-id="99970-118">[operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md) </span></span>  
 [<span data-ttu-id="99970-119">方法: 構造体間にユーザー定義の変換を実装する</span><span class="sxs-lookup"><span data-stu-id="99970-119">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)

