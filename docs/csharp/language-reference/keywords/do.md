---
title: do (C# リファレンス)
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: b918b378623a239803fb4e0a65fcf82fd677b21f
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34566086"
---
# <a name="do-c-reference"></a><span data-ttu-id="3fcc6-102">do (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="3fcc6-102">do (C# Reference)</span></span>

<span data-ttu-id="3fcc6-103">`do` ステートメントでは、指定されたブール式が `true` と評価される間に、ステートメントまたはステートメント ブロックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="3fcc6-103">The `do` statement executes a statement or a block of statements while a specified boolean expression evaluates to `true`.</span></span> <span data-ttu-id="3fcc6-104">ループの各実行の後に式が評価されるため、`do-while` ループは 1 回以上実行されます。</span><span class="sxs-lookup"><span data-stu-id="3fcc6-104">Because that expression is evaluated after each execution of the loop, a `do-while` loop executes one or more times.</span></span> <span data-ttu-id="3fcc6-105">[while](while.md) ループは、これとは異なり、0 回以上実行されます。</span><span class="sxs-lookup"><span data-stu-id="3fcc6-105">This differs from the [while](while.md) loop, which executes zero or more times.</span></span>

<span data-ttu-id="3fcc6-106">`do` ステートメント ブロック内の任意の位置で、[break](break.md) ステートメントを使用してループを抜けることができます。</span><span class="sxs-lookup"><span data-stu-id="3fcc6-106">At any point within the `do` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="3fcc6-107">[continue](continue.md) ステートメントを使用すると、`while` 式の評価に直接ステップ実行できます。</span><span class="sxs-lookup"><span data-stu-id="3fcc6-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="3fcc6-108">式の評価が `true` の場合、ループの最初のステートメントから実行が続行されます。</span><span class="sxs-lookup"><span data-stu-id="3fcc6-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="3fcc6-109">それ以外の場合、実行は、ループの後の最初のステートメントから続行されます。</span><span class="sxs-lookup"><span data-stu-id="3fcc6-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="3fcc6-110">また、[goto](goto.md)、[return](return.md)、[throw](throw.md) ステートメントのいずれかを使って `do-while` ループを終了することもできます。</span><span class="sxs-lookup"><span data-stu-id="3fcc6-110">You also can exit a `do-while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="3fcc6-111">例</span><span class="sxs-lookup"><span data-stu-id="3fcc6-111">Example</span></span>

<span data-ttu-id="3fcc6-112">`do` ステートメントの使用方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="3fcc6-112">The following example shows the usage of the `do` statement.</span></span> <span data-ttu-id="3fcc6-113">**[実行]** を選択して、コード例を実行します。</span><span class="sxs-lookup"><span data-stu-id="3fcc6-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="3fcc6-114">その後に、コードを変更し、もう一度実行することができます。</span><span class="sxs-lookup"><span data-stu-id="3fcc6-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="3fcc6-115">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="3fcc6-115">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="3fcc6-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="3fcc6-116">See also</span></span>

 [<span data-ttu-id="3fcc6-117">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="3fcc6-117">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="3fcc6-118">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="3fcc6-118">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="3fcc6-119">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="3fcc6-119">C# Keywords</span></span>](index.md)  
 [<span data-ttu-id="3fcc6-120">do-while ステートメント (C++)</span><span class="sxs-lookup"><span data-stu-id="3fcc6-120">do-while Statement (C++)</span></span>](/cpp/cpp/do-while-statement-cpp)  
 [<span data-ttu-id="3fcc6-121">繰り返しステートメント</span><span class="sxs-lookup"><span data-stu-id="3fcc6-121">Iteration Statements</span></span>](iteration-statements.md)  
 [<span data-ttu-id="3fcc6-122">while ステートメント</span><span class="sxs-lookup"><span data-stu-id="3fcc6-122">while statement</span></span>](while.md)  
