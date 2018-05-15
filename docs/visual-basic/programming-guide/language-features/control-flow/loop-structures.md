---
title: ループ構造 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- control flow [Visual Basic], loops
- For keyword [Visual Basic], loop structures
- loops
- loop structures [Visual Basic]
- statements [Visual Basic], loop
- Do statement [Visual Basic], Do loops
- conditional statements [Visual Basic], loop structures
ms.assetid: ecacb09b-a4c9-42be-98b2-a15d368b5db8
ms.openlocfilehash: 8138609f06d82b53ef5b5afb480e8609461ffc33
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="loop-structures-visual-basic"></a><span data-ttu-id="0fb57-102">ループ構造 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0fb57-102">Loop Structures (Visual Basic)</span></span>
<span data-ttu-id="0fb57-103">Visual Basic のループ構造を使用すると、コードの 1 つまたは複数の行を繰り返し実行できます。</span><span class="sxs-lookup"><span data-stu-id="0fb57-103">Visual Basic loop structures allow you to run one or more lines of code repetitively.</span></span> <span data-ttu-id="0fb57-104">条件になるまで、ループ構造内のステートメントを繰り返すことができます`True`条件になるまで、`False`コレクションの回数、または各要素に対して 1 回の数を指定します。</span><span class="sxs-lookup"><span data-stu-id="0fb57-104">You can repeat the statements in a loop structure until a condition is `True`, until a condition is `False`, a specified number of times, or once for each element in a collection.</span></span>  
  
 <span data-ttu-id="0fb57-105">次の図は、条件が true になるまでの一連のステートメントを実行しているループ構造を示しています。</span><span class="sxs-lookup"><span data-stu-id="0fb57-105">The following illustration shows a loop structure that runs a set of statements until a condition becomes true.</span></span>  
  
 <span data-ttu-id="0fb57-106">![フロー チャートしています.ループまで](../../../../visual-basic/programming-guide/language-features/control-flow/media/dountilloop.gif "DoUntilLoop")</span><span class="sxs-lookup"><span data-stu-id="0fb57-106">![Flow chart of a Do...Until loop](../../../../visual-basic/programming-guide/language-features/control-flow/media/dountilloop.gif "DoUntilLoop")</span></span>  
<span data-ttu-id="0fb57-107">条件が true になるまで、一連のステートメントを実行しています。</span><span class="sxs-lookup"><span data-stu-id="0fb57-107">Running a set of statements until a condition becomes true</span></span>  
  
## <a name="while-loops"></a><span data-ttu-id="0fb57-108">While ループ</span><span class="sxs-lookup"><span data-stu-id="0fb57-108">While Loops</span></span>  
 <span data-ttu-id="0fb57-109">`While`しています.`End While`で条件が指定されていれば、構築が一連のステートメントを実行、`While`ステートメントが`True`です。</span><span class="sxs-lookup"><span data-stu-id="0fb57-109">The `While`...`End While` construction runs a set of statements as long as the condition specified in the `While` statement is `True`.</span></span> <span data-ttu-id="0fb57-110">詳細については、次を参照してください[中...While ステートメント終了](../../../../visual-basic/language-reference/statements/while-end-while-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="0fb57-110">For more information, see [While...End While Statement](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span></span>  
  
## <a name="do-loops"></a><span data-ttu-id="0fb57-111">Do ループ</span><span class="sxs-lookup"><span data-stu-id="0fb57-111">Do Loops</span></span>  
 <span data-ttu-id="0fb57-112">`Do`しています.`Loop`構築では、ループ構造の末尾または先頭のいずれかに条件をテストすることができます。</span><span class="sxs-lookup"><span data-stu-id="0fb57-112">The `Do`...`Loop` construction allows you to test a condition at either the beginning or the end of a loop structure.</span></span> <span data-ttu-id="0fb57-113">条件がある限り、ループ処理を実行するかどうかを指定することも`True`になるまで`True`です。</span><span class="sxs-lookup"><span data-stu-id="0fb57-113">You can also specify whether to repeat the loop while the condition remains `True` or until it becomes `True`.</span></span> <span data-ttu-id="0fb57-114">詳細については、次を参照してください[操作を行います...ステートメントをループ](../../../../visual-basic/language-reference/statements/do-loop-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="0fb57-114">For more information, see [Do...Loop Statement](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span>  
  
## <a name="for-loops"></a><span data-ttu-id="0fb57-115">For ループ</span><span class="sxs-lookup"><span data-stu-id="0fb57-115">For Loops</span></span>  
 <span data-ttu-id="0fb57-116">`For`しています.`Next`構築は、指定された回数だけループを実行します。</span><span class="sxs-lookup"><span data-stu-id="0fb57-116">The `For`...`Next` construction performs the loop a set number of times.</span></span> <span data-ttu-id="0fb57-117">呼ばれる、ループ コントロール変数を使用して、*カウンター*繰り返しを追跡します。</span><span class="sxs-lookup"><span data-stu-id="0fb57-117">It uses a loop control variable, also called a *counter*, to keep track of the repetitions.</span></span> <span data-ttu-id="0fb57-118">開始日と終了このカウンターの値を指定して、必要に応じて量で増加している 1 つの繰り返しから、次を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="0fb57-118">You specify the starting and ending values for this counter, and you can optionally specify the amount by which it increases from one repetition to the next.</span></span> <span data-ttu-id="0fb57-119">詳細については、次を参照してください[をしています...次のステートメントの](../../../../visual-basic/language-reference/statements/for-next-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="0fb57-119">For more information, see [For...Next Statement](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
## <a name="for-each-loops"></a><span data-ttu-id="0fb57-120">For Each ループ</span><span class="sxs-lookup"><span data-stu-id="0fb57-120">For Each Loops</span></span>  
 <span data-ttu-id="0fb57-121">`For Each`しています.`Next`構築は、コレクション内の各要素に対して 1 回のステートメントのセットを実行します。</span><span class="sxs-lookup"><span data-stu-id="0fb57-121">The `For Each`...`Next` construction runs a set of statements once for each element in a collection.</span></span> <span data-ttu-id="0fb57-122">ループ コントロール変数を指定するが、開始または終了値を決定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="0fb57-122">You specify the loop control variable, but you do not have to determine starting or ending values for it.</span></span> <span data-ttu-id="0fb57-123">詳細については、次を参照してください[ごとにしています...次のステートメントの](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="0fb57-123">For more information, see [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fb57-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="0fb57-124">See Also</span></span>  
 [<span data-ttu-id="0fb57-125">制御フロー</span><span class="sxs-lookup"><span data-stu-id="0fb57-125">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="0fb57-126">条件判断構造</span><span class="sxs-lookup"><span data-stu-id="0fb57-126">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="0fb57-127">その他の制御構造</span><span class="sxs-lookup"><span data-stu-id="0fb57-127">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)  
 [<span data-ttu-id="0fb57-128">入れ子になった制御構造</span><span class="sxs-lookup"><span data-stu-id="0fb57-128">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
