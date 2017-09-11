---
title: "構造体 (Visual Basic) の意思決定 |Microsoft ドキュメント"
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
- statements [Visual Basic], control flow
- If statement, decision structures
- If statement, If...Then...Else
- control flow, decision structures
- decision structures
- conditional statements, decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
caps.latest.revision: 29
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
ms.openlocfilehash: dcbfb4bc3318d5f79870d04e606fab8bfa2dafb9
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="decision-structures-visual-basic"></a><span data-ttu-id="fc37e-102">条件判断構造 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc37e-102">Decision Structures (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="fc37e-103">条件をテストし、そのテストの結果に応じて別の操作を実行することができます。</span><span class="sxs-lookup"><span data-stu-id="fc37e-103"> lets you test conditions and perform different operations depending on the results of that test.</span></span> <span data-ttu-id="fc37e-104">True または false の場合、さまざまな値の式、または一連のステートメントを実行するときに生成された例外のさまざまな条件をテストできます。</span><span class="sxs-lookup"><span data-stu-id="fc37e-104">You can test for a condition being true or false, for various values of an expression, or for various exceptions generated when you execute a series of statements.</span></span>  
  
 <span data-ttu-id="fc37e-105">次の図は、条件が真かをテストし、true または false であるかに基づいて異なる処理を実行する条件判断構造を示しています。</span><span class="sxs-lookup"><span data-stu-id="fc37e-105">The following illustration shows a decision structure that tests for a condition being true and takes different actions depending on whether it is true or false.</span></span>  
  
 <span data-ttu-id="fc37e-106">![If のフロー チャート.そうしたら。。。Else 構文](../../../../visual-basic/programming-guide/language-features/control-flow/media/ifthenelse.gif "IfThenElse")</span><span class="sxs-lookup"><span data-stu-id="fc37e-106">![Flow chart of an If...Then...Else construction](../../../../visual-basic/programming-guide/language-features/control-flow/media/ifthenelse.gif "IfThenElse")</span></span>  
<span data-ttu-id="fc37e-107">条件が true と false の場合は、異なる処理を実行</span><span class="sxs-lookup"><span data-stu-id="fc37e-107">Taking different actions when a condition is true and when it is false</span></span>  
  
## <a name="ifthenelse-construction"></a><span data-ttu-id="fc37e-108">もし。。。そうしたら。。。Else 構文</span><span class="sxs-lookup"><span data-stu-id="fc37e-108">If...Then...Else Construction</span></span>  
 <span data-ttu-id="fc37e-109">`If...Then...Else`構造では、1 つまたは複数の条件をテストして、各条件に応じて&1; つまたは複数のステートメントを実行できます。</span><span class="sxs-lookup"><span data-stu-id="fc37e-109">`If...Then...Else` constructions let you test for one or more conditions and run one or more statements depending on each condition.</span></span> <span data-ttu-id="fc37e-110">条件をテストし、次の方法で行うことができます。</span><span class="sxs-lookup"><span data-stu-id="fc37e-110">You can test conditions and take actions in the following ways:</span></span>  
  
-   <span data-ttu-id="fc37e-111">条件の場合は、1 つまたは複数のステートメントを実行します。`True`</span><span class="sxs-lookup"><span data-stu-id="fc37e-111">Run one or more statements if a condition is `True`</span></span>  
  
-   <span data-ttu-id="fc37e-112">条件の場合は、1 つまたは複数のステートメントを実行します。`False`</span><span class="sxs-lookup"><span data-stu-id="fc37e-112">Run one or more statements if a condition is `False`</span></span>  
  
-   <span data-ttu-id="fc37e-113">条件の場合は、いくつかのステートメントを実行`True`およびその他のユーザーである場合`False`</span><span class="sxs-lookup"><span data-stu-id="fc37e-113">Run some statements if a condition is `True` and others if it is `False`</span></span>  
  
-   <span data-ttu-id="fc37e-114">前の条件の場合、追加的な条件をテストします。`False`</span><span class="sxs-lookup"><span data-stu-id="fc37e-114">Test an additional condition if a prior condition is `False`</span></span>  
  
 <span data-ttu-id="fc37e-115">これらすべての可能性を提供する制御構造体は、[場合.そうしたら。。。Else ステートメント](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="fc37e-115">The control structure that offers all these possibilities is the [If...Then...Else Statement](../../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span></span> <span data-ttu-id="fc37e-116">1 つのテストと&1; つのステートメントを実行する必要がある場合は、単一行のバージョンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="fc37e-116">You can use a single-line version if you have just one test and one statement to run.</span></span> <span data-ttu-id="fc37e-117">条件とアクションのより複雑なセットがある場合は、複数行のバージョンを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="fc37e-117">If you have a more complex set of conditions and actions, you can use the multiple-line version.</span></span>  
  
## <a name="selectcase-construction"></a><span data-ttu-id="fc37e-118">選択してください。Case 構造</span><span class="sxs-lookup"><span data-stu-id="fc37e-118">Select...Case Construction</span></span>  
 <span data-ttu-id="fc37e-119">`Select...Case`構築では、1 回式を評価し、異なる一連の別の使用可能な値に基づくステートメントを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="fc37e-119">The `Select...Case` construction lets you evaluate an expression one time and run different sets of statements based on different possible values.</span></span> <span data-ttu-id="fc37e-120">詳細については、次を参照してください[を選択しています.。Case ステートメント](../../../../visual-basic/language-reference/statements/select-case-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="fc37e-120">For more information, see [Select...Case Statement](../../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="trycatchfinally-construction"></a><span data-ttu-id="fc37e-121">しようとしてください.キャッチしてください.最後に構築</span><span class="sxs-lookup"><span data-stu-id="fc37e-121">Try...Catch...Finally Construction</span></span>  
 <span data-ttu-id="fc37e-122">`Try...Catch...Finally`構造では、一連のステートメントのいずれかの例外が発生した場合は、コントロールを保持する環境の下のステートメントを実行できます。</span><span class="sxs-lookup"><span data-stu-id="fc37e-122">`Try...Catch...Finally` constructions let you run a set of statements under an environment that retains control if any one of your statements causes an exception.</span></span> <span data-ttu-id="fc37e-123">さまざまな例外のさまざまなアクションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="fc37e-123">You can take different actions for different exceptions.</span></span> <span data-ttu-id="fc37e-124">全体を終了する前に実行されるコードのブロックを指定することもできます。`Try...Catch...Finally`どうなるかに関係なく、構築します。</span><span class="sxs-lookup"><span data-stu-id="fc37e-124">You can optionally specify a block of code that runs before you exit the whole `Try...Catch...Finally` construction, regardless of what occurs.</span></span> <span data-ttu-id="fc37e-125">詳細については、次を参照してください[しようとしています.。キャッチしてください.Finally ステートメント](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="fc37e-125">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fc37e-126">多くの制御構造のキーワードをクリックすると、すべての構造のキーワードが強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="fc37e-126">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="fc37e-127">クリックすると、`If`で、`If...Then...Else`構築のすべてのインスタンス`If`、 `Then`、 `ElseIf`、 `Else`、および`End If`構造で強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="fc37e-127">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="fc37e-128">前または次の強調表示されているキーワードに移動するには、ctrl キーと shift キーを押しながら下方向キーまたは ctrl キーと shift キーを押しながら上方向をキーを押します。</span><span class="sxs-lookup"><span data-stu-id="fc37e-128">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc37e-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="fc37e-129">See Also</span></span>  
 <span data-ttu-id="fc37e-130">[制御フロー](../../../../visual-basic/programming-guide/language-features/control-flow/index.md) </span><span class="sxs-lookup"><span data-stu-id="fc37e-130">[Control Flow](../../../../visual-basic/programming-guide/language-features/control-flow/index.md) </span></span>  
<span data-ttu-id="fc37e-131"> [ループ構造](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md) </span><span class="sxs-lookup"><span data-stu-id="fc37e-131"> [Loop Structures](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md) </span></span>  
<span data-ttu-id="fc37e-132"> [他の制御構造](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md) </span><span class="sxs-lookup"><span data-stu-id="fc37e-132"> [Other Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md) </span></span>  
<span data-ttu-id="fc37e-133"> [入れ子になった制御構造](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md) </span><span class="sxs-lookup"><span data-stu-id="fc37e-133"> [Nested Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md) </span></span>  
<span data-ttu-id="fc37e-134"> [If 演算子](../../../../visual-basic/language-reference/operators/if-operator.md)</span><span class="sxs-lookup"><span data-stu-id="fc37e-134"> [If Operator](../../../../visual-basic/language-reference/operators/if-operator.md)</span></span>
