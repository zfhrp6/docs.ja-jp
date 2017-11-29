---
title: "再帰プロシージャ (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], that call themselves
- procedures [Visual Basic], recursive
- procedures [Visual Basic], calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 444eeaf043cf3710c5154fd7e8577590e3ce7d1e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="recursive-procedures-visual-basic"></a><span data-ttu-id="789c4-102">再帰プロシージャ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="789c4-102">Recursive Procedures (Visual Basic)</span></span>
<span data-ttu-id="789c4-103">A*再帰*手順は、自分自身を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="789c4-103">A *recursive* procedure is one that calls itself.</span></span> <span data-ttu-id="789c4-104">一般に、これが最も効果的な方法を記述する[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]コード。</span><span class="sxs-lookup"><span data-stu-id="789c4-104">In general, this is not the most effective way to write [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code.</span></span>  
  
 <span data-ttu-id="789c4-105">次の手順では、元の引数の階乗を計算するのに再帰を使用します。</span><span class="sxs-lookup"><span data-stu-id="789c4-105">The following procedure uses recursion to calculate the factorial of its original argument.</span></span>  
  
 [!code-vb[VbVbcnProcedures#51](./codesnippet/VisualBasic/recursive-procedures_1.vb)]  
  
## <a name="considerations-with-recursive-procedures"></a><span data-ttu-id="789c4-106">再帰プロシージャに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="789c4-106">Considerations with Recursive Procedures</span></span>  
 <span data-ttu-id="789c4-107">**制限条件**です。</span><span class="sxs-lookup"><span data-stu-id="789c4-107">**Limiting Conditions**.</span></span> <span data-ttu-id="789c4-108">再帰を終了するには、少なくとも 1 つの条件をテストする再帰的な手順を設計する必要がありも、再帰呼び出しの適切な数値の中でこのような条件が満たされるないケースを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="789c4-108">You must design a recursive procedure to test for at least one condition that can terminate the recursion, and you must also handle the case where no such condition is satisfied within a reasonable number of recursive calls.</span></span> <span data-ttu-id="789c4-109">失敗することがなく満たすことのできるに少なくとも 1 つの条件が、存在しない、プロシージャには、無限ループを実行する危険度の高いが実行されます。</span><span class="sxs-lookup"><span data-stu-id="789c4-109">Without at least one condition that can be met without fail, your procedure runs a high risk of executing in an infinite loop.</span></span>  
  
 <span data-ttu-id="789c4-110">**メモリ使用状況**。</span><span class="sxs-lookup"><span data-stu-id="789c4-110">**Memory Usage**.</span></span> <span data-ttu-id="789c4-111">アプリケーションは、限られた量のローカル変数の領域を持ちます。</span><span class="sxs-lookup"><span data-stu-id="789c4-111">Your application has a limited amount of space for local variables.</span></span> <span data-ttu-id="789c4-112">プロシージャが、それ自体を呼び出すたびに、ローカル変数の追加のコピーの領域を使用します。</span><span class="sxs-lookup"><span data-stu-id="789c4-112">Each time a procedure calls itself, it uses more of that space for additional copies of its local variables.</span></span> <span data-ttu-id="789c4-113">最終的と、このプロセスが無期限に解決しない場合は、<xref:System.StackOverflowException>エラーです。</span><span class="sxs-lookup"><span data-stu-id="789c4-113">If this process continues indefinitely, it eventually causes a <xref:System.StackOverflowException> error.</span></span>  
  
 <span data-ttu-id="789c4-114">**効率**です。</span><span class="sxs-lookup"><span data-stu-id="789c4-114">**Efficiency**.</span></span> <span data-ttu-id="789c4-115">ほとんどの場合、再帰はループを置換できます。</span><span class="sxs-lookup"><span data-stu-id="789c4-115">You can almost always substitute a loop for recursion.</span></span> <span data-ttu-id="789c4-116">ループには、引数の渡し、追加のストレージを初期化し、値を返すことのオーバーヘッドはありません。</span><span class="sxs-lookup"><span data-stu-id="789c4-116">A loop does not have the overhead of passing arguments, initializing additional storage, and returning values.</span></span> <span data-ttu-id="789c4-117">パフォーマンスは、再帰呼び出しなしの方があります。</span><span class="sxs-lookup"><span data-stu-id="789c4-117">Your performance can be much better without recursive calls.</span></span>  
  
 <span data-ttu-id="789c4-118">**相互再帰**です。</span><span class="sxs-lookup"><span data-stu-id="789c4-118">**Mutual Recursion**.</span></span> <span data-ttu-id="789c4-119">2 つの手順では、互いを呼び出す場合、パフォーマンスが大きく低下または無限ループを確認する場合があります。</span><span class="sxs-lookup"><span data-stu-id="789c4-119">You might observe very poor performance, or even an infinite loop, if two procedures call each other.</span></span> <span data-ttu-id="789c4-120">この設計では、1 つの再帰プロシージャと同じ問題を表示しますが検出およびデバッグが困難になることができます。</span><span class="sxs-lookup"><span data-stu-id="789c4-120">Such a design presents the same problems as a single recursive procedure, but can be harder to detect and debug.</span></span>  
  
 <span data-ttu-id="789c4-121">**かっこで呼び出して**です。</span><span class="sxs-lookup"><span data-stu-id="789c4-121">**Calling with Parentheses**.</span></span> <span data-ttu-id="789c4-122">ときに、`Function`プロシージャを呼び出す自体を再帰的に、引数リストがない場合でも、プロシージャ名をかっこを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="789c4-122">When a `Function` procedure calls itself recursively, you must follow the procedure name with parentheses, even if there is no argument list.</span></span> <span data-ttu-id="789c4-123">それ以外の場合、関数名が取得された関数の戻り値を表しているとします。</span><span class="sxs-lookup"><span data-stu-id="789c4-123">Otherwise, the function name is taken as representing the return value of the function.</span></span>  
  
 <span data-ttu-id="789c4-124">**テスト**です。</span><span class="sxs-lookup"><span data-stu-id="789c4-124">**Testing**.</span></span> <span data-ttu-id="789c4-125">再帰的なプロシージャを記述する場合はテストする非常に慎重に常にいくつかの制限の条件を満たしているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="789c4-125">If you write a recursive procedure, you should test it very carefully to make sure it always meets some limiting condition.</span></span> <span data-ttu-id="789c4-126">再帰呼び出しが多すぎるためのメモリが不足して実行できないことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="789c4-126">You should also ensure that you cannot run out of memory due to having too many recursive calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="789c4-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="789c4-127">See Also</span></span>  
 <xref:System.StackOverflowException>  
 [<span data-ttu-id="789c4-128">手順</span><span class="sxs-lookup"><span data-stu-id="789c4-128">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="789c4-129">Sub プロシージャ</span><span class="sxs-lookup"><span data-stu-id="789c4-129">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="789c4-130">Function プロシージャ</span><span class="sxs-lookup"><span data-stu-id="789c4-130">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="789c4-131">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="789c4-131">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="789c4-132">演算子プロシージャ</span><span class="sxs-lookup"><span data-stu-id="789c4-132">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="789c4-133">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="789c4-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="789c4-134">プロシージャのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="789c4-134">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="789c4-135">プロシージャのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="789c4-135">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="789c4-136">ループ構造</span><span class="sxs-lookup"><span data-stu-id="789c4-136">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="789c4-137">例外のトラブルシューティング : System.StackOverflowException</span><span class="sxs-lookup"><span data-stu-id="789c4-137">Troubleshooting Exceptions: System.StackOverflowException</span></span>](http://msdn.microsoft.com/library/51b71217-c507-4f5b-bc35-0236180d7968)
