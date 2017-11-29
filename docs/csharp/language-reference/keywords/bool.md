---
title: "bool (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords: bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
caps.latest.revision: "30"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1d52955d64a6c8063e4ea93ceb096459c1c5e984
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="bool-c-reference"></a><span data-ttu-id="cd618-102">bool (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="cd618-102">bool (C# Reference)</span></span>
<span data-ttu-id="cd618-103">`bool` キーワードは <xref:System.Boolean?displayProperty=nameWithType> の別名です。</span><span class="sxs-lookup"><span data-stu-id="cd618-103">The `bool` keyword is an alias of <xref:System.Boolean?displayProperty=nameWithType>.</span></span> <span data-ttu-id="cd618-104">ブール値 ([true](../../../csharp/language-reference/keywords/true.md) と [false](../../../csharp/language-reference/keywords/false.md)) を格納する変数を宣言するために使われます。</span><span class="sxs-lookup"><span data-stu-id="cd618-104">It is used to declare variables to store the Boolean values, [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cd618-105">値 `null` も格納できるブール変数が必要な場合は、`bool?` を使います。</span><span class="sxs-lookup"><span data-stu-id="cd618-105">If you require a Boolean variable that can also have a value of `null`, use `bool?`.</span></span> <span data-ttu-id="cd618-106">詳細については、「[null 許容型](../../../csharp/programming-guide/nullable-types/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd618-106">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
## <a name="literals"></a><span data-ttu-id="cd618-107">リテラル</span><span class="sxs-lookup"><span data-stu-id="cd618-107">Literals</span></span>  
 <span data-ttu-id="cd618-108">`bool` 変数にはブール値を代入できます。</span><span class="sxs-lookup"><span data-stu-id="cd618-108">You can assign a Boolean value to a `bool` variable.</span></span> <span data-ttu-id="cd618-109">また、`bool` として評価される式も `bool` 変数に代入できます。</span><span class="sxs-lookup"><span data-stu-id="cd618-109">You can also assign an expression that evaluates to `bool` to a `bool` variable.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_1.cs)]  
  
 <span data-ttu-id="cd618-110">`bool` 変数の既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="cd618-110">The default value of a `bool` variable is `false`.</span></span> <span data-ttu-id="cd618-111">`bool?` 変数の既定値は `null` です。</span><span class="sxs-lookup"><span data-stu-id="cd618-111">The default value of a `bool?` variable is `null`.</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="cd618-112">変換</span><span class="sxs-lookup"><span data-stu-id="cd618-112">Conversions</span></span>  
 <span data-ttu-id="cd618-113">C++ では、`bool` 型の値を `int` 型の値に変換できます。つまり、`false` はゼロと同等であり、`true` はゼロ以外の値と同等です。</span><span class="sxs-lookup"><span data-stu-id="cd618-113">In C++, a value of type `bool` can be converted to a value of type `int`; in other words, `false` is equivalent to zero and `true` is equivalent to nonzero values.</span></span> <span data-ttu-id="cd618-114">C# では、`bool` 型と他の型の間に変換はありません。</span><span class="sxs-lookup"><span data-stu-id="cd618-114">In C#, there is no conversion between the `bool` type and other types.</span></span> <span data-ttu-id="cd618-115">たとえば、次の `if` ステートメントは C# では無効です。</span><span class="sxs-lookup"><span data-stu-id="cd618-115">For example, the following `if` statement is invalid in C#:</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_2.cs)]  
  
 <span data-ttu-id="cd618-116">`int` 型の変数をテストするには、0 などの値と明示的に比較する必要があります。次はその例です。</span><span class="sxs-lookup"><span data-stu-id="cd618-116">To test a variable of the type `int`, you have to explicitly compare it to a value, such as zero, as follows:</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="cd618-117">例</span><span class="sxs-lookup"><span data-stu-id="cd618-117">Example</span></span>  
 <span data-ttu-id="cd618-118">この例のプログラムは、キーボードから文字された文字がアルファベットかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="cd618-118">In this example, you enter a character from the keyboard and the program checks if the input character is a letter.</span></span> <span data-ttu-id="cd618-119">アルファベットである場合は、小文字か大文字かを調べます。</span><span class="sxs-lookup"><span data-stu-id="cd618-119">If it is a letter, it checks if it is lowercase or uppercase.</span></span> <span data-ttu-id="cd618-120">こうしたチェックは <xref:System.Char.IsLetter%2A> と <xref:System.Char.IsLower%2A> で実行され、どちらも `bool` 型を返します。</span><span class="sxs-lookup"><span data-stu-id="cd618-120">These checks are performed with the <xref:System.Char.IsLetter%2A>, and <xref:System.Char.IsLower%2A>, both of which return the `bool` type:</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_4.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="cd618-121">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="cd618-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cd618-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd618-122">See Also</span></span>  
 [<span data-ttu-id="cd618-123">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="cd618-123">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="cd618-124">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="cd618-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="cd618-125">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="cd618-125">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="cd618-126">整数型の一覧表</span><span class="sxs-lookup"><span data-stu-id="cd618-126">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="cd618-127">組み込み型の一覧表</span><span class="sxs-lookup"><span data-stu-id="cd618-127">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="cd618-128">暗黙的な数値変換の一覧表</span><span class="sxs-lookup"><span data-stu-id="cd618-128">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="cd618-129">明示的な数値変換の一覧表</span><span class="sxs-lookup"><span data-stu-id="cd618-129">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
