---
title: do (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 5599f079e29fd094c4d6a6a75afba89fb562a166
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="do-c-reference"></a><span data-ttu-id="ca725-102">do (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="ca725-102">do (C# Reference)</span></span>
<span data-ttu-id="ca725-103">`do` ステートメントでは、指定された式が `false` になるまで、ステートメントまたはステートメント ブロックが繰り返し実行されます。</span><span class="sxs-lookup"><span data-stu-id="ca725-103">The `do` statement executes a statement or a block of statements repeatedly until a specified expression evaluates to `false`.</span></span> <span data-ttu-id="ca725-104">ループの本体は、単一のステートメントで構成されている場合を除いて、中かっこ (`{}`) で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="ca725-104">The body of the loop must be enclosed in braces, `{}`, unless it consists of a single statement.</span></span> <span data-ttu-id="ca725-105">単一ステートメントで構成されている場合、中かっこはオプションです。</span><span class="sxs-lookup"><span data-stu-id="ca725-105">In that case, the braces are optional.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca725-106">例</span><span class="sxs-lookup"><span data-stu-id="ca725-106">Example</span></span>  
 <span data-ttu-id="ca725-107">次の例では、変数 `x` が 5 未満である限り、`do-while` ループ ステートメントが実行されます。</span><span class="sxs-lookup"><span data-stu-id="ca725-107">In the following example, the `do-while` loop statements execute as long as the variable `x` is less than 5.</span></span>  
  
 [!code-csharp[csrefKeywordsIteration#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/do_1.cs)]  
  
 <span data-ttu-id="ca725-108">[while](../../../csharp/language-reference/keywords/while.md) ステートメントとは異なり、`do-while` ループは条件式が評価される前に 1 回実行されます。</span><span class="sxs-lookup"><span data-stu-id="ca725-108">Unlike the [while](../../../csharp/language-reference/keywords/while.md) statement, a `do-while` loop is executed one time before the conditional expression is evaluated.</span></span>  
  
 <span data-ttu-id="ca725-109">`do-while` ブロック内の任意の位置で、[break](../../../csharp/language-reference/keywords/break.md) ステートメントを使用してループを抜けることができます。</span><span class="sxs-lookup"><span data-stu-id="ca725-109">At any point in the `do-while` block, you can break out of the loop using the [break](../../../csharp/language-reference/keywords/break.md) statement.</span></span> <span data-ttu-id="ca725-110">[continue](../../../csharp/language-reference/keywords/continue.md) ステートメントを使用すると、`while` 式の評価ステートメントを直接ステップ実行できます。</span><span class="sxs-lookup"><span data-stu-id="ca725-110">You can step directly to the `while` expression evaluation statement by using the [continue](../../../csharp/language-reference/keywords/continue.md) statement.</span></span> <span data-ttu-id="ca725-111">`while` 式の評価が true の場合、ループの最初のステートメントから実行が続行されます。</span><span class="sxs-lookup"><span data-stu-id="ca725-111">If the `while` expression evaluates to true, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="ca725-112">式の評価が false の場合、`do-while` ループの後の最初のステートメントから実行が続行されます。</span><span class="sxs-lookup"><span data-stu-id="ca725-112">If the expression evaluates to false, execution continues at the first statement after the `do-while` loop.</span></span>  
  
 <span data-ttu-id="ca725-113">[goto](../../../csharp/language-reference/keywords/goto.md) ステートメント、[return](../../../csharp/language-reference/keywords/return.md) ステートメント、または [throw](../../../csharp/language-reference/keywords/throw.md) ステートメントを使用して `do-while` ループを抜けることもできます。</span><span class="sxs-lookup"><span data-stu-id="ca725-113">A `do-while` loop can also be exited by the [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), or [throw](../../../csharp/language-reference/keywords/throw.md) statements.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="ca725-114">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="ca725-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ca725-115">参照</span><span class="sxs-lookup"><span data-stu-id="ca725-115">See Also</span></span>  
 [<span data-ttu-id="ca725-116">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="ca725-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ca725-117">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="ca725-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ca725-118">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="ca725-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="ca725-119">do-while ステートメント (C++)</span><span class="sxs-lookup"><span data-stu-id="ca725-119">do-while Statement (C++)</span></span>](/cpp/cpp/do-while-statement-cpp)  
 [<span data-ttu-id="ca725-120">繰り返しステートメント</span><span class="sxs-lookup"><span data-stu-id="ca725-120">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
