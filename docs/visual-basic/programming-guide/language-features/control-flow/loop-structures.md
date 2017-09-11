---
title: "ループ構造 (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- control flow, loops
- For keyword [Visual Basic], loop structures
- loops
- loop structures
- statements [Visual Basic], loop
- Do statement, Do loops
- conditional statements, loop structures
ms.assetid: ecacb09b-a4c9-42be-98b2-a15d368b5db8
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: eba728d782bb5a6259467fb48f738f35580049c0
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="loop-structures-visual-basic"></a><span data-ttu-id="83ecd-102">ループ構造 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83ecd-102">Loop Structures (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="83ecd-103">ループ構造を使用すると、1 つまたは複数の行のコードを繰り返し実行できます。</span><span class="sxs-lookup"><span data-stu-id="83ecd-103"> loop structures allow you to run one or more lines of code repetitively.</span></span> <span data-ttu-id="83ecd-104">条件になるまで、ループ構造内のステートメントを繰り返すことができます`True`条件になるまで、`False`コレクションの回数、または各要素に対して&1; 回の番号を指定します。</span><span class="sxs-lookup"><span data-stu-id="83ecd-104">You can repeat the statements in a loop structure until a condition is `True`, until a condition is `False`, a specified number of times, or once for each element in a collection.</span></span>  
  
 <span data-ttu-id="83ecd-105">次の図は、条件が true になるまでは、一連のステートメントを実行するループ構造を示しています。</span><span class="sxs-lookup"><span data-stu-id="83ecd-105">The following illustration shows a loop structure that runs a set of statements until a condition becomes true.</span></span>  
  
 <span data-ttu-id="83ecd-106">![フロー チャート.ループ](../../../../visual-basic/programming-guide/language-features/control-flow/media/dountilloop.gif "DoUntilLoop")</span><span class="sxs-lookup"><span data-stu-id="83ecd-106">![Flow chart of a Do...Until loop](../../../../visual-basic/programming-guide/language-features/control-flow/media/dountilloop.gif "DoUntilLoop")</span></span>  
<span data-ttu-id="83ecd-107">条件が true になるまで、一連のステートメントを実行しています。</span><span class="sxs-lookup"><span data-stu-id="83ecd-107">Running a set of statements until a condition becomes true</span></span>  
  
## <a name="while-loops"></a><span data-ttu-id="83ecd-108">While ループ</span><span class="sxs-lookup"><span data-stu-id="83ecd-108">While Loops</span></span>  
 <span data-ttu-id="83ecd-109">The `While`...`End While`構築には一連のステートメントが実行される、条件で指定されている限り、`While`ステートメントは`True`です。</span><span class="sxs-lookup"><span data-stu-id="83ecd-109">The `While`...`End While` construction runs a set of statements as long as the condition specified in the `While` statement is `True`.</span></span> <span data-ttu-id="83ecd-110">詳細については、次を参照してください[中.。While ステートメント終了](../../../../visual-basic/language-reference/statements/while-end-while-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="83ecd-110">For more information, see [While...End While Statement](../../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span></span>  
  
## <a name="do-loops"></a><span data-ttu-id="83ecd-111">Do ループ</span><span class="sxs-lookup"><span data-stu-id="83ecd-111">Do Loops</span></span>  
 <span data-ttu-id="83ecd-112">The `Do`...`Loop`構築では、先頭またはループ構造の末尾のいずれかの条件をテストすることができます。</span><span class="sxs-lookup"><span data-stu-id="83ecd-112">The `Do`...`Loop` construction allows you to test a condition at either the beginning or the end of a loop structure.</span></span> <span data-ttu-id="83ecd-113">条件がある限り、ループ処理を実行するかどうかを指定することも`True`になるまで`True`します。</span><span class="sxs-lookup"><span data-stu-id="83ecd-113">You can also specify whether to repeat the loop while the condition remains `True` or until it becomes `True`.</span></span> <span data-ttu-id="83ecd-114">詳細については、次を参照してください[操作を行います.。ステートメントのループ](../../../../visual-basic/language-reference/statements/do-loop-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="83ecd-114">For more information, see [Do...Loop Statement](../../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span>  
  
## <a name="for-loops"></a><span data-ttu-id="83ecd-115">For ループ</span><span class="sxs-lookup"><span data-stu-id="83ecd-115">For Loops</span></span>  
 <span data-ttu-id="83ecd-116">The `For`...`Next`構築は、指定された回数だけループを実行します。</span><span class="sxs-lookup"><span data-stu-id="83ecd-116">The `For`...`Next` construction performs the loop a set number of times.</span></span> <span data-ttu-id="83ecd-117">呼ばれますループ制御変数を使用して、*カウンター*繰り返しを追跡するためです。</span><span class="sxs-lookup"><span data-stu-id="83ecd-117">It uses a loop control variable, also called a *counter*, to keep track of the repetitions.</span></span> <span data-ttu-id="83ecd-118">開始と終了日、このカウンターの値を指定して、必要に応じて、量が増加している&1; 回の繰り返しから次の手順を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="83ecd-118">You specify the starting and ending values for this counter, and you can optionally specify the amount by which it increases from one repetition to the next.</span></span> <span data-ttu-id="83ecd-119">詳細については、次を参照してください[にしています.。次のステートメントの](../../../../visual-basic/language-reference/statements/for-next-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="83ecd-119">For more information, see [For...Next Statement](../../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
## <a name="for-each-loops"></a><span data-ttu-id="83ecd-120">For Each ループ</span><span class="sxs-lookup"><span data-stu-id="83ecd-120">For Each Loops</span></span>  
 <span data-ttu-id="83ecd-121">The `For Each`...`Next`構築は、コレクション内の各要素に対して&1; 回のステートメントのセットを実行します。</span><span class="sxs-lookup"><span data-stu-id="83ecd-121">The `For Each`...`Next` construction runs a set of statements once for each element in a collection.</span></span> <span data-ttu-id="83ecd-122">ループ制御変数を指定するが、開始または終了値を確認する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="83ecd-122">You specify the loop control variable, but you do not have to determine starting or ending values for it.</span></span> <span data-ttu-id="83ecd-123">詳細については、次を参照してください[ごとにしています.。次のステートメントの](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="83ecd-123">For more information, see [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83ecd-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="83ecd-124">See Also</span></span>  
 <span data-ttu-id="83ecd-125">[制御フロー](../../../../visual-basic/programming-guide/language-features/control-flow/index.md) </span><span class="sxs-lookup"><span data-stu-id="83ecd-125">[Control Flow](../../../../visual-basic/programming-guide/language-features/control-flow/index.md) </span></span>  
<span data-ttu-id="83ecd-126"> [条件判断構造](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md) </span><span class="sxs-lookup"><span data-stu-id="83ecd-126"> [Decision Structures](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md) </span></span>  
<span data-ttu-id="83ecd-127"> [他の制御構造](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md) </span><span class="sxs-lookup"><span data-stu-id="83ecd-127"> [Other Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md) </span></span>  
<span data-ttu-id="83ecd-128"> [入れ子になった制御構造](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)</span><span class="sxs-lookup"><span data-stu-id="83ecd-128"> [Nested Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)</span></span>
