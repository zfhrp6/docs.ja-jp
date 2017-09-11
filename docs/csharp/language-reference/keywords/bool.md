---
title: "bool (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- bool_CSharpKeyword
- bool
dev_langs:
- CSharp
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
caps.latest.revision: 30
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
ms.openlocfilehash: f3b7455ab6b0ec780afe7d81b2ff990d47a31d20
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="bool-c-reference"></a><span data-ttu-id="56ef1-102">bool (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="56ef1-102">bool (C# Reference)</span></span>
<span data-ttu-id="56ef1-103">`bool` キーワードは <xref:System.Boolean?displayProperty=fullName> の別名です。</span><span class="sxs-lookup"><span data-stu-id="56ef1-103">The `bool` keyword is an alias of <xref:System.Boolean?displayProperty=fullName>.</span></span> <span data-ttu-id="56ef1-104">ブール値 ([true](../../../csharp/language-reference/keywords/true.md) と [false](../../../csharp/language-reference/keywords/false.md)) を格納する変数を宣言するために使われます。</span><span class="sxs-lookup"><span data-stu-id="56ef1-104">It is used to declare variables to store the Boolean values, [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56ef1-105">値 `null` も格納できるブール変数が必要な場合は、`bool?` を使います。</span><span class="sxs-lookup"><span data-stu-id="56ef1-105">If you require a Boolean variable that can also have a value of `null`, use `bool?`.</span></span> <span data-ttu-id="56ef1-106">詳細については、「[null 許容型](../../../csharp/programming-guide/nullable-types/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="56ef1-106">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
## <a name="literals"></a><span data-ttu-id="56ef1-107">リテラル</span><span class="sxs-lookup"><span data-stu-id="56ef1-107">Literals</span></span>  
 <span data-ttu-id="56ef1-108">`bool` 変数にはブール値を代入できます。</span><span class="sxs-lookup"><span data-stu-id="56ef1-108">You can assign a Boolean value to a `bool` variable.</span></span> <span data-ttu-id="56ef1-109">また、`bool` として評価される式も `bool` 変数に代入できます。</span><span class="sxs-lookup"><span data-stu-id="56ef1-109">You can also assign an expression that evaluates to `bool` to a `bool` variable.</span></span>  
  
 <span data-ttu-id="56ef1-110">[!code-cs[csrefKeywordsTypes#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="56ef1-110">[!code-cs[csrefKeywordsTypes#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_1.cs)]</span></span>  
  
 <span data-ttu-id="56ef1-111">`bool` 変数の既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="56ef1-111">The default value of a `bool` variable is `false`.</span></span> <span data-ttu-id="56ef1-112">`bool?` 変数の既定値は `null` です。</span><span class="sxs-lookup"><span data-stu-id="56ef1-112">The default value of a `bool?` variable is `null`.</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="56ef1-113">変換</span><span class="sxs-lookup"><span data-stu-id="56ef1-113">Conversions</span></span>  
 <span data-ttu-id="56ef1-114">C++ では、`bool` 型の値を `int` 型の値に変換できます。つまり、`false` はゼロと同等であり、`true` はゼロ以外の値と同等です。</span><span class="sxs-lookup"><span data-stu-id="56ef1-114">In C++, a value of type `bool` can be converted to a value of type `int`; in other words, `false` is equivalent to zero and `true` is equivalent to nonzero values.</span></span> <span data-ttu-id="56ef1-115">C# では、`bool` 型と他の型の間に変換はありません。</span><span class="sxs-lookup"><span data-stu-id="56ef1-115">In C#, there is no conversion between the `bool` type and other types.</span></span> <span data-ttu-id="56ef1-116">たとえば、次の `if` ステートメントは C# では無効です。</span><span class="sxs-lookup"><span data-stu-id="56ef1-116">For example, the following `if` statement is invalid in C#:</span></span>  
  
 <span data-ttu-id="56ef1-117">[!code-cs[csrefKeywordsTypes#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="56ef1-117">[!code-cs[csrefKeywordsTypes#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_2.cs)]</span></span>  
  
 <span data-ttu-id="56ef1-118">`int` 型の変数をテストするには、0 などの値と明示的に比較する必要があります。次はその例です。</span><span class="sxs-lookup"><span data-stu-id="56ef1-118">To test a variable of the type `int`, you have to explicitly compare it to a value, such as zero, as follows:</span></span>  
  
 <span data-ttu-id="56ef1-119">[!code-cs[csrefKeywordsTypes#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="56ef1-119">[!code-cs[csrefKeywordsTypes#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_3.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="56ef1-120">例</span><span class="sxs-lookup"><span data-stu-id="56ef1-120">Example</span></span>  
 <span data-ttu-id="56ef1-121">この例のプログラムは、キーボードから文字された文字がアルファベットかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="56ef1-121">In this example, you enter a character from the keyboard and the program checks if the input character is a letter.</span></span> <span data-ttu-id="56ef1-122">アルファベットである場合は、小文字か大文字かを調べます。</span><span class="sxs-lookup"><span data-stu-id="56ef1-122">If it is a letter, it checks if it is lowercase or uppercase.</span></span> <span data-ttu-id="56ef1-123">こうしたチェックは <xref:System.Char.IsLetter%2A> と <xref:System.Char.IsLower%2A> で実行され、どちらも `bool` 型を返します。</span><span class="sxs-lookup"><span data-stu-id="56ef1-123">These checks are performed with the <xref:System.Char.IsLetter%2A>, and <xref:System.Char.IsLower%2A>, both of which return the `bool` type:</span></span>  
  
 <span data-ttu-id="56ef1-124">[!code-cs[csrefKeywordsTypes#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="56ef1-124">[!code-cs[csrefKeywordsTypes#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_4.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="56ef1-125">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="56ef1-125">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="56ef1-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="56ef1-126">See Also</span></span>  
 <span data-ttu-id="56ef1-127">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="56ef1-127">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="56ef1-128">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="56ef1-128">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="56ef1-129">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="56ef1-129">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="56ef1-130">[整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="56ef1-130">[Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
 <span data-ttu-id="56ef1-131">[組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="56ef1-131">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 <span data-ttu-id="56ef1-132">[暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="56ef1-132">[Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
 [<span data-ttu-id="56ef1-133">明示的な数値変換の一覧表</span><span class="sxs-lookup"><span data-stu-id="56ef1-133">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

