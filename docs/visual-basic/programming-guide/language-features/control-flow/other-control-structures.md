---
title: "その他の制御構造 (Visual Basic) |Microsoft ドキュメント"
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
- control structures
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
caps.latest.revision: 19
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
ms.openlocfilehash: 8f8bd57f193be0d7f410f7325355ffc47ab10e3f
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="b4b1a-102">その他の制御構造 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4b1a-102">Other Control Structures (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="b4b1a-103">リソースを破棄またはをオブジェクト参照を繰り返す必要が時間の数を削減するのに役立つ制御構造を提供します。</span><span class="sxs-lookup"><span data-stu-id="b4b1a-103"> provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="b4b1a-104">使用しています.最後の構築を使用して</span><span class="sxs-lookup"><span data-stu-id="b4b1a-104">Using...End Using Construction</span></span>  
 <span data-ttu-id="b4b1a-105">`Using...End Using`構築を行うステートメント ブロックを確立する、SQL 接続などのリソースを使用します。</span><span class="sxs-lookup"><span data-stu-id="b4b1a-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="b4b1a-106">使用してリソースを取得することができます必要に応じて、`Using`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="b4b1a-106">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="b4b1a-107">終了すると、`Using`ブロック、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]自動的にリソースの破棄を使用するには、他のコードで使用可能になるようにします。</span><span class="sxs-lookup"><span data-stu-id="b4b1a-107">When you exit the `Using` block, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="b4b1a-108">ローカルで破棄可能なリソースがあります。</span><span class="sxs-lookup"><span data-stu-id="b4b1a-108">The resource must be local and disposable.</span></span> <span data-ttu-id="b4b1a-109">詳細については、次を参照してください。 [Using ステートメント](../../../../visual-basic/language-reference/statements/using-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="b4b1a-109">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="b4b1a-110">しています.構築と終了します。</span><span class="sxs-lookup"><span data-stu-id="b4b1a-110">With...End With Construction</span></span>  
 <span data-ttu-id="b4b1a-111">`With...End With`構築では、オブジェクト参照を&1; 回指定することができ、一連のメンバーにアクセスするステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="b4b1a-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="b4b1a-112">これは、コードを簡略化されためパフォーマンスが向上[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]にアクセスした各ステートメントの参照を再設定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b4b1a-112">This can simplify your code and improve performance because [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="b4b1a-113">詳細については、次を参照してください[としています.。ステートメントで終了して](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="b4b1a-113">For more information, see [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4b1a-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="b4b1a-114">See Also</span></span>  
 <span data-ttu-id="b4b1a-115">[制御フロー](../../../../visual-basic/programming-guide/language-features/control-flow/index.md) </span><span class="sxs-lookup"><span data-stu-id="b4b1a-115">[Control Flow](../../../../visual-basic/programming-guide/language-features/control-flow/index.md) </span></span>  
<span data-ttu-id="b4b1a-116"> [条件判断構造](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md) </span><span class="sxs-lookup"><span data-stu-id="b4b1a-116"> [Decision Structures](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md) </span></span>  
<span data-ttu-id="b4b1a-117"> [ループ構造](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md) </span><span class="sxs-lookup"><span data-stu-id="b4b1a-117"> [Loop Structures](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md) </span></span>  
<span data-ttu-id="b4b1a-118"> [入れ子になった制御構造](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md) </span><span class="sxs-lookup"><span data-stu-id="b4b1a-118"> [Nested Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md) </span></span>  
<span data-ttu-id="b4b1a-119"> [ステートメントを使用します。](../../../../visual-basic/language-reference/statements/using-statement.md) </span><span class="sxs-lookup"><span data-stu-id="b4b1a-119"> [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md) </span></span>  
<span data-ttu-id="b4b1a-120"> [With...End With ステートメント](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)</span><span class="sxs-lookup"><span data-stu-id="b4b1a-120"> [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)</span></span>
