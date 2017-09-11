---
title: "再帰プロシージャ (Visual Basic) |Microsoft ドキュメント"
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
- Visual Basic code, procedures
- procedures, that call themselves
- procedures, recursive
- procedures, calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
caps.latest.revision: 13
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
ms.openlocfilehash: 5e4838bb14125dcfd27798acf0c196f351ba5b90
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="recursive-procedures-visual-basic"></a><span data-ttu-id="f9167-102">再帰プロシージャ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9167-102">Recursive Procedures (Visual Basic)</span></span>
<span data-ttu-id="f9167-103">A*再帰*手順は、自分自身を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f9167-103">A *recursive* procedure is one that calls itself.</span></span> <span data-ttu-id="f9167-104">一般に、これは最も効果的な方法を記述する[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コードです。</span><span class="sxs-lookup"><span data-stu-id="f9167-104">In general, this is not the most effective way to write [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] code.</span></span>  
  
 <span data-ttu-id="f9167-105">次の手順では、再帰を使用して、元の引数の階乗を計算します。</span><span class="sxs-lookup"><span data-stu-id="f9167-105">The following procedure uses recursion to calculate the factorial of its original argument.</span></span>  
  
 <span data-ttu-id="f9167-106">[!code-vb[VbVbcnProcedures&51;](./codesnippet/VisualBasic/recursive-procedures_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f9167-106">[!code-vb[VbVbcnProcedures#51](./codesnippet/VisualBasic/recursive-procedures_1.vb)]</span></span>  
  
## <a name="considerations-with-recursive-procedures"></a><span data-ttu-id="f9167-107">再帰プロシージャに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="f9167-107">Considerations with Recursive Procedures</span></span>  
 <span data-ttu-id="f9167-108">**制限条件**します。</span><span class="sxs-lookup"><span data-stu-id="f9167-108">**Limiting Conditions**.</span></span> <span data-ttu-id="f9167-109">再帰を終了するには、少なくとも&1; つの条件をテストする再帰的な手順を設計する必要があり、再帰呼び出しの適切な数値の中でこのような条件が満たされるないケースを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="f9167-109">You must design a recursive procedure to test for at least one condition that can terminate the recursion, and you must also handle the case where no such condition is satisfied within a reasonable number of recursive calls.</span></span> <span data-ttu-id="f9167-110">失敗せずに満たすことのできる、少なくとも&1; つの条件がない、プロシージャは、無限ループで実行するリスクが高くを実行します。</span><span class="sxs-lookup"><span data-stu-id="f9167-110">Without at least one condition that can be met without fail, your procedure runs a high risk of executing in an infinite loop.</span></span>  
  
 <span data-ttu-id="f9167-111">**メモリ使用量**します。</span><span class="sxs-lookup"><span data-stu-id="f9167-111">**Memory Usage**.</span></span> <span data-ttu-id="f9167-112">アプリケーションでは、ローカル変数の領域量が制限を持ちます。</span><span class="sxs-lookup"><span data-stu-id="f9167-112">Your application has a limited amount of space for local variables.</span></span> <span data-ttu-id="f9167-113">プロシージャが自分自身を呼び出すたびに、ローカル変数の追加のコピーの領域を使用します。</span><span class="sxs-lookup"><span data-stu-id="f9167-113">Each time a procedure calls itself, it uses more of that space for additional copies of its local variables.</span></span> <span data-ttu-id="f9167-114">最終的と、この処理がいつまでも続く場合、<xref:System.StackOverflowException>エラー</xref:System.StackOverflowException> 。</span><span class="sxs-lookup"><span data-stu-id="f9167-114">If this process continues indefinitely, it eventually causes a <xref:System.StackOverflowException> error.</span></span>  
  
 <span data-ttu-id="f9167-115">**効率性**します。</span><span class="sxs-lookup"><span data-stu-id="f9167-115">**Efficiency**.</span></span> <span data-ttu-id="f9167-116">ほとんどの場合、再帰はループを置換できます。</span><span class="sxs-lookup"><span data-stu-id="f9167-116">You can almost always substitute a loop for recursion.</span></span> <span data-ttu-id="f9167-117">ループには、引数の受け渡し、追加のストレージを初期化し、値を返すのオーバーヘッドはありません。</span><span class="sxs-lookup"><span data-stu-id="f9167-117">A loop does not have the overhead of passing arguments, initializing additional storage, and returning values.</span></span> <span data-ttu-id="f9167-118">パフォーマンスは、再帰呼び出しなしの方があります。</span><span class="sxs-lookup"><span data-stu-id="f9167-118">Your performance can be much better without recursive calls.</span></span>  
  
 <span data-ttu-id="f9167-119">**相互再帰**します。</span><span class="sxs-lookup"><span data-stu-id="f9167-119">**Mutual Recursion**.</span></span> <span data-ttu-id="f9167-120">2 つの手順では、互いを呼び出す場合は、パフォーマンスが大きく低下または無限ループではあってを監視することがあります。</span><span class="sxs-lookup"><span data-stu-id="f9167-120">You might observe very poor performance, or even an infinite loop, if two procedures call each other.</span></span> <span data-ttu-id="f9167-121">このような設計は、1 つの再帰プロシージャと同じ問題を提示しますが、検出およびデバッグが困難になることができます。</span><span class="sxs-lookup"><span data-stu-id="f9167-121">Such a design presents the same problems as a single recursive procedure, but can be harder to detect and debug.</span></span>  
  
 <span data-ttu-id="f9167-122">**かっこを使った呼び出し**します。</span><span class="sxs-lookup"><span data-stu-id="f9167-122">**Calling with Parentheses**.</span></span> <span data-ttu-id="f9167-123">ときに、`Function`プロシージャを呼び出す再帰的に、引数リストがない場合でも、かっこを付けて、プロシージャ名を従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="f9167-123">When a `Function` procedure calls itself recursively, you must follow the procedure name with parentheses, even if there is no argument list.</span></span> <span data-ttu-id="f9167-124">関数名を取得する場合は、関数の戻り値を表しているとします。</span><span class="sxs-lookup"><span data-stu-id="f9167-124">Otherwise, the function name is taken as representing the return value of the function.</span></span>  
  
 <span data-ttu-id="f9167-125">**テスト**します。</span><span class="sxs-lookup"><span data-stu-id="f9167-125">**Testing**.</span></span> <span data-ttu-id="f9167-126">再帰プロシージャを記述する場合に、非常に慎重に常にいくつかの制限の条件を満たしているかどうかを確認するテスト必要があります。</span><span class="sxs-lookup"><span data-stu-id="f9167-126">If you write a recursive procedure, you should test it very carefully to make sure it always meets some limiting condition.</span></span> <span data-ttu-id="f9167-127">多すぎるの再帰呼び出しのためのメモリ不足が実行できないということを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f9167-127">You should also ensure that you cannot run out of memory due to having too many recursive calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9167-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9167-128">See Also</span></span>  
 <span data-ttu-id="f9167-129"><xref:System.StackOverflowException></xref:System.StackOverflowException></span><span class="sxs-lookup"><span data-stu-id="f9167-129"><xref:System.StackOverflowException></span></span>   
<span data-ttu-id="f9167-130"> [手順](./index.md) </span><span class="sxs-lookup"><span data-stu-id="f9167-130"> [Procedures](./index.md) </span></span>  
<span data-ttu-id="f9167-131"> [Sub プロシージャ](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="f9167-131"> [Sub Procedures](./sub-procedures.md) </span></span>  
<span data-ttu-id="f9167-132"> [Function プロシージャ](./function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="f9167-132"> [Function Procedures](./function-procedures.md) </span></span>  
<span data-ttu-id="f9167-133"> [プロパティ プロシージャ](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="f9167-133"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="f9167-134"> [演算子プロシージャ](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="f9167-134"> [Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="f9167-135"> [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="f9167-135"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="f9167-136"> [プロシージャのオーバー ロード](./procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="f9167-136"> [Procedure Overloading](./procedure-overloading.md) </span></span>  
<span data-ttu-id="f9167-137"> [トラブルシューティングの手順](./troubleshooting-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="f9167-137"> [Troubleshooting Procedures](./troubleshooting-procedures.md) </span></span>  
<span data-ttu-id="f9167-138"> [ループ構造](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md) </span><span class="sxs-lookup"><span data-stu-id="f9167-138"> [Loop Structures](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md) </span></span>  
<span data-ttu-id="f9167-139"> [例外のトラブルシューティング : System.StackOverflowException](http://msdn.microsoft.com/library/51b71217-c507-4f5b-bc35-0236180d7968)</span><span class="sxs-lookup"><span data-stu-id="f9167-139"> [Troubleshooting Exceptions: System.StackOverflowException](http://msdn.microsoft.com/library/51b71217-c507-4f5b-bc35-0236180d7968)</span></span>
