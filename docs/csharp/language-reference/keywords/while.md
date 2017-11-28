---
title: "while (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords: while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 420b409689d877c3e1ac744e8d7a65500cf8f964
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="while-c-reference"></a><span data-ttu-id="8b8a9-102">while (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="8b8a9-102">while (C# Reference)</span></span>
<span data-ttu-id="8b8a9-103">`while` ステートメントでは、指定された式が `false` と評価されるまで、ステートメントまたはステートメント ブロックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="8b8a9-103">The `while` statement executes a statement or a block of statements until a specified expression evaluates to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b8a9-104">例</span><span class="sxs-lookup"><span data-stu-id="8b8a9-104">Example</span></span>  
 [!code-csharp[csrefKeywordsIteration#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="8b8a9-105">例</span><span class="sxs-lookup"><span data-stu-id="8b8a9-105">Example</span></span>  
 [!code-csharp[csrefKeywordsIteration#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="8b8a9-106">例</span><span class="sxs-lookup"><span data-stu-id="8b8a9-106">Example</span></span>  
 <span data-ttu-id="8b8a9-107">`while` 式が評価されてからループが実行されるため、`while` ループは 0 回以上実行されます。</span><span class="sxs-lookup"><span data-stu-id="8b8a9-107">Because the test of the `while` expression takes place before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="8b8a9-108">[do](../../../csharp/language-reference/keywords/do.md) ループは、これとは異なり、1 回以上実行されます。</span><span class="sxs-lookup"><span data-stu-id="8b8a9-108">This differs from the [do](../../../csharp/language-reference/keywords/do.md) loop, which executes one or more times.</span></span>  
  
 <span data-ttu-id="8b8a9-109">`while` ループは、[break](../../../csharp/language-reference/keywords/break.md)、[goto](../../../csharp/language-reference/keywords/goto.md)、[return](../../../csharp/language-reference/keywords/return.md)、または [throw](../../../csharp/language-reference/keywords/throw.md) ステートメントがループの外部に制御を移動すると終了できます。</span><span class="sxs-lookup"><span data-stu-id="8b8a9-109">A `while` loop can be terminated when a [break](../../../csharp/language-reference/keywords/break.md), [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), or [throw](../../../csharp/language-reference/keywords/throw.md) statement transfers control outside the loop.</span></span> <span data-ttu-id="8b8a9-110">ループを終了せずに制御を次の繰り返しに渡すには、[continue](../../../csharp/language-reference/keywords/continue.md) ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="8b8a9-110">To pass control to the next iteration without exiting the loop, use the [continue](../../../csharp/language-reference/keywords/continue.md) statement.</span></span> <span data-ttu-id="8b8a9-111">上記の 3 つの例での出力は、`int n` がインクリメントされる位置によって異なる点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="8b8a9-111">Notice the difference in output in the three previous examples, depending on where `int n` is incremented.</span></span> <span data-ttu-id="8b8a9-112">次の例では出力は生成されません。</span><span class="sxs-lookup"><span data-stu-id="8b8a9-112">In the example below no output is generated.</span></span>  
  
 [!code-csharp[csrefKeywordsIteration#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="8b8a9-113">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="8b8a9-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8b8a9-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="8b8a9-114">See Also</span></span>  
 [<span data-ttu-id="8b8a9-115">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="8b8a9-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8b8a9-116">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="8b8a9-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8b8a9-117">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="8b8a9-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="8b8a9-118">while ステートメント (C++)</span><span class="sxs-lookup"><span data-stu-id="8b8a9-118">while Statement (C++)</span></span>](/cpp/cpp/while-statement-cpp)  
 [<span data-ttu-id="8b8a9-119">繰り返しステートメント</span><span class="sxs-lookup"><span data-stu-id="8b8a9-119">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
