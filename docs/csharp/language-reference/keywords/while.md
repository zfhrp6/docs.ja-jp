---
title: "while (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- while_CSharpKeyword
- while
dev_langs:
- CSharp
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
caps.latest.revision: 22
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
ms.openlocfilehash: ed531c83dba02b38576bf8354b1ff92f075048bc
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="while-c-reference"></a><span data-ttu-id="726c5-102">while (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="726c5-102">while (C# Reference)</span></span>
<span data-ttu-id="726c5-103">`while` ステートメントでは、指定された式が `false` と評価されるまで、ステートメントまたはステートメント ブロックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="726c5-103">The `while` statement executes a statement or a block of statements until a specified expression evaluates to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="726c5-104">例</span><span class="sxs-lookup"><span data-stu-id="726c5-104">Example</span></span>  
 <span data-ttu-id="726c5-105">[!code-cs[csrefKeywordsIteration#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="726c5-105">[!code-cs[csrefKeywordsIteration#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="726c5-106">例</span><span class="sxs-lookup"><span data-stu-id="726c5-106">Example</span></span>  
 <span data-ttu-id="726c5-107">[!code-cs[csrefKeywordsIteration#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="726c5-107">[!code-cs[csrefKeywordsIteration#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="726c5-108">例</span><span class="sxs-lookup"><span data-stu-id="726c5-108">Example</span></span>  
 <span data-ttu-id="726c5-109">`while` 式が評価されてからループが実行されるため、`while` ループは 0 回以上実行されます。</span><span class="sxs-lookup"><span data-stu-id="726c5-109">Because the test of the `while` expression takes place before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="726c5-110">[do](../../../csharp/language-reference/keywords/do.md) ループは、これとは異なり、1 回以上実行されます。</span><span class="sxs-lookup"><span data-stu-id="726c5-110">This differs from the [do](../../../csharp/language-reference/keywords/do.md) loop, which executes one or more times.</span></span>  
  
 <span data-ttu-id="726c5-111">`while` ループは、[break](../../../csharp/language-reference/keywords/break.md)、[goto](../../../csharp/language-reference/keywords/goto.md)、[return](../../../csharp/language-reference/keywords/return.md)、または [throw](../../../csharp/language-reference/keywords/throw.md) ステートメントがループの外部に制御を移動すると終了できます。</span><span class="sxs-lookup"><span data-stu-id="726c5-111">A `while` loop can be terminated when a [break](../../../csharp/language-reference/keywords/break.md), [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), or [throw](../../../csharp/language-reference/keywords/throw.md) statement transfers control outside the loop.</span></span> <span data-ttu-id="726c5-112">ループを終了せずに制御を次の繰り返しに渡すには、[continue](../../../csharp/language-reference/keywords/continue.md) ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="726c5-112">To pass control to the next iteration without exiting the loop, use the [continue](../../../csharp/language-reference/keywords/continue.md) statement.</span></span> <span data-ttu-id="726c5-113">上記の 3 つの例での出力は、`int n` がインクリメントされる位置によって異なる点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="726c5-113">Notice the difference in output in the three previous examples, depending on where `int n` is incremented.</span></span> <span data-ttu-id="726c5-114">次の例では出力は生成されません。</span><span class="sxs-lookup"><span data-stu-id="726c5-114">In the example below no output is generated.</span></span>  
  
 <span data-ttu-id="726c5-115">[!code-cs[csrefKeywordsIteration#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="726c5-115">[!code-cs[csrefKeywordsIteration#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_3.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="726c5-116">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="726c5-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="726c5-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="726c5-117">See Also</span></span>  
 <span data-ttu-id="726c5-118">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="726c5-118">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="726c5-119">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="726c5-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="726c5-120">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="726c5-120">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="726c5-121">[while ステートメント (C++)](/cpp/cpp/while-statement-cpp) </span><span class="sxs-lookup"><span data-stu-id="726c5-121">[while Statement (C++)](/cpp/cpp/while-statement-cpp) </span></span>  
 [<span data-ttu-id="726c5-122">繰り返しステートメント</span><span class="sxs-lookup"><span data-stu-id="726c5-122">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)

