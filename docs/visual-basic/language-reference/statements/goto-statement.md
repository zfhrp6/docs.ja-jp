---
title: GoTo ステートメント
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.GoTo
helpviewer_keywords:
- GoTo statement [Visual Basic]
- control flow [Visual Basic], branching
- unconditional branching [Visual Basic]
- branching [Visual Basic]
- branching [Visual Basic], unconditional
- branching [Visual Basic], conditional
- conditional statements [Visual Basic], GoTo statement
- GoTo statement [Visual Basic], syntax
ms.assetid: 313274c2-8ab3-4b9c-9ba3-0fd6798e4f6d
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 22a6315e69cd6c797d462d0835e85bb1dde67dcc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="goto-statement"></a><span data-ttu-id="0c7e9-102">GoTo ステートメント</span><span class="sxs-lookup"><span data-stu-id="0c7e9-102">GoTo Statement</span></span>
<span data-ttu-id="0c7e9-103">プロシージャ内の指定した行に無条件に分岐します。</span><span class="sxs-lookup"><span data-stu-id="0c7e9-103">Branches unconditionally to a specified line in a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c7e9-104">構文</span><span class="sxs-lookup"><span data-stu-id="0c7e9-104">Syntax</span></span>  
  
```  
GoTo line  
```  
  
## <a name="part"></a><span data-ttu-id="0c7e9-105">パーツ</span><span class="sxs-lookup"><span data-stu-id="0c7e9-105">Part</span></span>  
 `line`  
 <span data-ttu-id="0c7e9-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="0c7e9-106">Required.</span></span> <span data-ttu-id="0c7e9-107">任意の行ラベル。</span><span class="sxs-lookup"><span data-stu-id="0c7e9-107">Any line label.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c7e9-108">コメント</span><span class="sxs-lookup"><span data-stu-id="0c7e9-108">Remarks</span></span>  
 <span data-ttu-id="0c7e9-109">`GoTo`ステートメントの分岐が表示されるプロシージャ内の行にのみです。</span><span class="sxs-lookup"><span data-stu-id="0c7e9-109">The `GoTo` statement can branch only to lines in the procedure in which it appears.</span></span> <span data-ttu-id="0c7e9-110">行がある行をいる必要があります`GoTo`を参照できます。</span><span class="sxs-lookup"><span data-stu-id="0c7e9-110">The line must have a line label that `GoTo` can refer to.</span></span> <span data-ttu-id="0c7e9-111">詳細については、次を参照してください。[する方法: ラベル ステートメント](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0c7e9-111">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c7e9-112">`GoTo`ステートメントを使用するコードの管理を読み取ったりするが困難です。</span><span class="sxs-lookup"><span data-stu-id="0c7e9-112">`GoTo` statements can make code difficult to read and maintain.</span></span> <span data-ttu-id="0c7e9-113">可能な限り、制御構造を使用します。</span><span class="sxs-lookup"><span data-stu-id="0c7e9-113">Whenever possible, use a control structure instead.</span></span> <span data-ttu-id="0c7e9-114">詳細については、次を参照してください。[制御フロー](../../../visual-basic/programming-guide/language-features/control-flow/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="0c7e9-114">For more information, see [Control Flow](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span></span>  
  
 <span data-ttu-id="0c7e9-115">使用することはできません、`GoTo`ステートメントの外部からの分岐を`For`しています.`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`、または`Using`しています.`End Using`内のラベルに構築します。</span><span class="sxs-lookup"><span data-stu-id="0c7e9-115">You cannot use a `GoTo` statement to branch from outside a `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`, or `Using`...`End Using` construction to a label inside.</span></span>  
  
## <a name="branching-and-try-constructions"></a><span data-ttu-id="0c7e9-116">分岐と構造を再試行してください</span><span class="sxs-lookup"><span data-stu-id="0c7e9-116">Branching and Try Constructions</span></span>  
 <span data-ttu-id="0c7e9-117">内で、`Try`しています.`Catch`...`Finally`を使用して分岐をコンストラクションは、次の規則の適用、`GoTo`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="0c7e9-117">Within a `Try`...`Catch`...`Finally` construction, the following rules apply to branching with the `GoTo` statement.</span></span>  
  
|<span data-ttu-id="0c7e9-118">ブロックまたは地域</span><span class="sxs-lookup"><span data-stu-id="0c7e9-118">Block or region</span></span>|<span data-ttu-id="0c7e9-119">外部からへの分岐</span><span class="sxs-lookup"><span data-stu-id="0c7e9-119">Branching in from outside</span></span>|<span data-ttu-id="0c7e9-120">外部への分岐からの内部</span><span class="sxs-lookup"><span data-stu-id="0c7e9-120">Branching out from inside</span></span>|  
|---------------------|-------------------------------|-------------------------------|  
|<span data-ttu-id="0c7e9-121">`Try`ブロック</span><span class="sxs-lookup"><span data-stu-id="0c7e9-121">`Try` block</span></span>|<span data-ttu-id="0c7e9-122">のみ、`Catch`同じ構築ブロック<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="0c7e9-122">Only from a `Catch` block of the same construction <sup>1</sup></span></span>|<span data-ttu-id="0c7e9-123">のみ、全体の構造の外部</span><span class="sxs-lookup"><span data-stu-id="0c7e9-123">Only to outside the whole construction</span></span>|  
|<span data-ttu-id="0c7e9-124">`Catch`ブロック</span><span class="sxs-lookup"><span data-stu-id="0c7e9-124">`Catch` block</span></span>|<span data-ttu-id="0c7e9-125">許可されることはありません。</span><span class="sxs-lookup"><span data-stu-id="0c7e9-125">Never allowed</span></span>|<span data-ttu-id="0c7e9-126">のみ、全体の構造の外部にまたは、`Try`同じ構築ブロック<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="0c7e9-126">Only to outside the whole construction, or to the `Try` block of the same construction <sup>1</sup></span></span>|  
|<span data-ttu-id="0c7e9-127">`Finally`ブロック</span><span class="sxs-lookup"><span data-stu-id="0c7e9-127">`Finally` block</span></span>|<span data-ttu-id="0c7e9-128">許可されることはありません。</span><span class="sxs-lookup"><span data-stu-id="0c7e9-128">Never allowed</span></span>|<span data-ttu-id="0c7e9-129">許可されることはありません。</span><span class="sxs-lookup"><span data-stu-id="0c7e9-129">Never allowed</span></span>|  
  
 <span data-ttu-id="0c7e9-130"><sup>1</sup>場合`Try`しています.`Catch`...`Finally`コンストラクションは、別の入れ子になった、`Catch`ブロックに分岐、`Try`独自入れ子のレベルにあるではなく、他のブロック`Try`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="0c7e9-130"><sup>1</sup> If one `Try`...`Catch`...`Finally` construction is nested within another, a `Catch` block can branch into the `Try` block at its own nesting level, but not into any other `Try` block.</span></span> <span data-ttu-id="0c7e9-131">入れ子になった`Try`しています.`Catch`...`Finally`構築は完全に含まれる必要があります、`Try`または`Catch`は構造の内部で入れ子にされているブロックです。</span><span class="sxs-lookup"><span data-stu-id="0c7e9-131">A nested `Try`...`Catch`...`Finally` construction must be contained completely in a `Try` or `Catch` block of the construction within which it is nested.</span></span>  
  
 <span data-ttu-id="0c7e9-132">次の図に 1 つ`Try`別内で入れ子になった構築します。</span><span class="sxs-lookup"><span data-stu-id="0c7e9-132">The following illustration shows one `Try` construction nested within another.</span></span> <span data-ttu-id="0c7e9-133">有効または無効では、2 つの構築のブロック間でさまざまな分岐が示されます。</span><span class="sxs-lookup"><span data-stu-id="0c7e9-133">Various branches among the blocks of the two constructions are indicated as valid or invalid.</span></span>  
  
 <span data-ttu-id="0c7e9-134">![Try 構造内の分岐のグラフィック ダイアグラム](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")</span><span class="sxs-lookup"><span data-stu-id="0c7e9-134">![Graphic diagram of branching in Try constructions](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")</span></span>  
<span data-ttu-id="0c7e9-135">Try 構造内の有効および無効な分岐</span><span class="sxs-lookup"><span data-stu-id="0c7e9-135">Valid and invalid branches in Try constructions</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c7e9-136">例</span><span class="sxs-lookup"><span data-stu-id="0c7e9-136">Example</span></span>  
 <span data-ttu-id="0c7e9-137">次の例では、`GoTo`ステートメントをプロシージャ内の行ラベルに分岐します。</span><span class="sxs-lookup"><span data-stu-id="0c7e9-137">The following example uses the `GoTo` statement to branch to line labels in a procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#31](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/goto-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0c7e9-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="0c7e9-138">See Also</span></span>  
 [<span data-ttu-id="0c7e9-139">Do...Loop ステートメント</span><span class="sxs-lookup"><span data-stu-id="0c7e9-139">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [<span data-ttu-id="0c7e9-140">For...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="0c7e9-140">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="0c7e9-141">For Each...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="0c7e9-141">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="0c7e9-142">If...Then...Else ステートメント</span><span class="sxs-lookup"><span data-stu-id="0c7e9-142">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [<span data-ttu-id="0c7e9-143">Select...Case ステートメント</span><span class="sxs-lookup"><span data-stu-id="0c7e9-143">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)  
 [<span data-ttu-id="0c7e9-144">Try...Catch...Finally ステートメント</span><span class="sxs-lookup"><span data-stu-id="0c7e9-144">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="0c7e9-145">While...End While ステートメント</span><span class="sxs-lookup"><span data-stu-id="0c7e9-145">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [<span data-ttu-id="0c7e9-146">With...End With ステートメント</span><span class="sxs-lookup"><span data-stu-id="0c7e9-146">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
