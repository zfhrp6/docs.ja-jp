---
title: その他の制御構造 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e1ea44cf2f0405dc55f8df60fb842691e50a9a0
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="20024-102">その他の制御構造 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20024-102">Other Control Structures (Visual Basic)</span></span>
<span data-ttu-id="20024-103">Visual Basic では、リソースを破棄または繰り返しオブジェクト参照に必要な回数の数を削減するのに役立つ制御構造を提供します。</span><span class="sxs-lookup"><span data-stu-id="20024-103">Visual Basic provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="20024-104">使用しています.構築を使用して終了</span><span class="sxs-lookup"><span data-stu-id="20024-104">Using...End Using Construction</span></span>  
 <span data-ttu-id="20024-105">`Using...End Using`構築を行うステートメント ブロックを確立する、SQL 接続などのリソースを使用します。</span><span class="sxs-lookup"><span data-stu-id="20024-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="20024-106">リソースを取得することができます必要に応じて、`Using`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="20024-106">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="20024-107">終了すると、`Using`ブロック、Visual Basic を自動的に破棄されたリソースを使用するには、他のコードで使用可能になるようにします。</span><span class="sxs-lookup"><span data-stu-id="20024-107">When you exit the `Using` block, Visual Basic automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="20024-108">ローカルで破棄可能なリソースを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="20024-108">The resource must be local and disposable.</span></span> <span data-ttu-id="20024-109">詳細については、「[Using ステートメント](../../../../visual-basic/language-reference/statements/using-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20024-109">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="20024-110">しています.末尾の構築に使用</span><span class="sxs-lookup"><span data-stu-id="20024-110">With...End With Construction</span></span>  
 <span data-ttu-id="20024-111">`With...End With`構築では、オブジェクト参照を 1 回指定することができますし、一連のメンバーにアクセスするステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="20024-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="20024-112">コードを簡略化でき、Visual Basic がそれにアクセスする各ステートメントの参照を再確立があるないために、パフォーマンスを向上させるこのことができます。</span><span class="sxs-lookup"><span data-stu-id="20024-112">This can simplify your code and improve performance because Visual Basic does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="20024-113">詳細については、次を参照してください[としています.。ステートメントで終了して](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="20024-113">For more information, see [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20024-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="20024-114">See Also</span></span>  
 [<span data-ttu-id="20024-115">制御フロー</span><span class="sxs-lookup"><span data-stu-id="20024-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="20024-116">条件判断構造</span><span class="sxs-lookup"><span data-stu-id="20024-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="20024-117">ループ構造</span><span class="sxs-lookup"><span data-stu-id="20024-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="20024-118">入れ子になった制御構造</span><span class="sxs-lookup"><span data-stu-id="20024-118">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="20024-119">Using ステートメント</span><span class="sxs-lookup"><span data-stu-id="20024-119">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)  
 [<span data-ttu-id="20024-120">With...End With ステートメント</span><span class="sxs-lookup"><span data-stu-id="20024-120">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
