---
title: "その他の制御構造 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 09e59d25b3b2fc89026295e8500c30dad7b75086
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="3b482-102">その他の制御構造 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b482-102">Other Control Structures (Visual Basic)</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="3b482-103">リソースを破棄または繰り返しオブジェクト参照に必要な回数の数を削減するのに役立つ制御構造を提供します。</span><span class="sxs-lookup"><span data-stu-id="3b482-103"> provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="3b482-104">使用しています.構築を使用して終了</span><span class="sxs-lookup"><span data-stu-id="3b482-104">Using...End Using Construction</span></span>  
 <span data-ttu-id="3b482-105">`Using...End Using`構築を行うステートメント ブロックを確立する、SQL 接続などのリソースを使用します。</span><span class="sxs-lookup"><span data-stu-id="3b482-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="3b482-106">リソースを取得することができます必要に応じて、`Using`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="3b482-106">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="3b482-107">終了すると、`Using`ブロック、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]を自動的に破棄されたリソースを使用するには、他のコードで使用可能になるようにします。</span><span class="sxs-lookup"><span data-stu-id="3b482-107">When you exit the `Using` block, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="3b482-108">ローカルで破棄可能なリソースを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3b482-108">The resource must be local and disposable.</span></span> <span data-ttu-id="3b482-109">詳細については、「[Using ステートメント](../../../../visual-basic/language-reference/statements/using-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b482-109">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="3b482-110">しています.末尾の構築に使用</span><span class="sxs-lookup"><span data-stu-id="3b482-110">With...End With Construction</span></span>  
 <span data-ttu-id="3b482-111">`With...End With`構築では、オブジェクト参照を 1 回指定することができますし、一連のメンバーにアクセスするステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="3b482-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="3b482-112">これは、コードを簡略化でき、パフォーマンスを向上させるため[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]にアクセスしたステートメントごとに参照を再確立する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="3b482-112">This can simplify your code and improve performance because [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="3b482-113">詳細については、次を参照してください[としています.。ステートメントで終了して](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="3b482-113">For more information, see [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b482-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="3b482-114">See Also</span></span>  
 [<span data-ttu-id="3b482-115">制御フロー</span><span class="sxs-lookup"><span data-stu-id="3b482-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="3b482-116">条件判断構造</span><span class="sxs-lookup"><span data-stu-id="3b482-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="3b482-117">ループ構造</span><span class="sxs-lookup"><span data-stu-id="3b482-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="3b482-118">入れ子になった制御構造</span><span class="sxs-lookup"><span data-stu-id="3b482-118">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="3b482-119">Using ステートメント</span><span class="sxs-lookup"><span data-stu-id="3b482-119">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)  
 [<span data-ttu-id="3b482-120">With...End With ステートメント</span><span class="sxs-lookup"><span data-stu-id="3b482-120">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
