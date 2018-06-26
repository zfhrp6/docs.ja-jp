---
title: while (C# リファレンス)
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: c082107472ac53d05b3b43dd4d9d8afc508a16cb
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34565866"
---
# <a name="while-c-reference"></a><span data-ttu-id="112d8-102">while (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="112d8-102">while (C# Reference)</span></span>

<span data-ttu-id="112d8-103">`while` ステートメントでは、指定されたブール式が `true` と評価される間に、ステートメントまたはステートメント ブロックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="112d8-103">The `while` statement executes a statement or a block of statements while a specified boolean expression evaluates to `true`.</span></span> <span data-ttu-id="112d8-104">ループの各実行の前に式が評価されるため、`while` ループは 0 回以上実行されます。</span><span class="sxs-lookup"><span data-stu-id="112d8-104">Because that expression is evaluated before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="112d8-105">[do](do.md) ループは、これとは異なり、1 回以上実行されます。</span><span class="sxs-lookup"><span data-stu-id="112d8-105">This differs from the [do](do.md) loop, which executes one or more times.</span></span>

<span data-ttu-id="112d8-106">`while` ステートメント ブロック内の任意の位置で、[break](break.md) ステートメントを使用してループを抜けることができます。</span><span class="sxs-lookup"><span data-stu-id="112d8-106">At any point within the `while` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="112d8-107">[continue](continue.md) ステートメントを使用すると、`while` 式の評価に直接ステップ実行できます。</span><span class="sxs-lookup"><span data-stu-id="112d8-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="112d8-108">式の評価が `true` の場合、ループの最初のステートメントから実行が続行されます。</span><span class="sxs-lookup"><span data-stu-id="112d8-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="112d8-109">それ以外の場合、実行は、ループの後の最初のステートメントから続行されます。</span><span class="sxs-lookup"><span data-stu-id="112d8-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="112d8-110">また、[goto](goto.md)、[return](return.md)、[throw](throw.md) ステートメントのいずれかを使って `while` ループを終了することもできます。</span><span class="sxs-lookup"><span data-stu-id="112d8-110">You also can exit a `while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="112d8-111">例</span><span class="sxs-lookup"><span data-stu-id="112d8-111">Example</span></span>

<span data-ttu-id="112d8-112">`while` ステートメントの使用方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="112d8-112">The following example shows the usage of the `while` statement.</span></span> <span data-ttu-id="112d8-113">**[実行]** を選択して、コード例を実行します。</span><span class="sxs-lookup"><span data-stu-id="112d8-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="112d8-114">その後に、コードを変更し、もう一度実行することができます。</span><span class="sxs-lookup"><span data-stu-id="112d8-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[while loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="112d8-115">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="112d8-115">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="112d8-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="112d8-116">See also</span></span>

 [<span data-ttu-id="112d8-117">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="112d8-117">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="112d8-118">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="112d8-118">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="112d8-119">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="112d8-119">C# Keywords</span></span>](index.md)  
 [<span data-ttu-id="112d8-120">while ステートメント (C++)</span><span class="sxs-lookup"><span data-stu-id="112d8-120">while Statement (C++)</span></span>](/cpp/cpp/while-statement-cpp)  
 [<span data-ttu-id="112d8-121">繰り返しステートメント</span><span class="sxs-lookup"><span data-stu-id="112d8-121">Iteration Statements</span></span>](iteration-statements.md)  
 [<span data-ttu-id="112d8-122">do ステートメント</span><span class="sxs-lookup"><span data-stu-id="112d8-122">do statement</span></span>](do.md)  
