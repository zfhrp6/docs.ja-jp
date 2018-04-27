---
title: '方法: プロシージャから値を返す (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: affcb25951a6647604286bc91dcaec8898fe2e30
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a><span data-ttu-id="41312-102">方法: プロシージャから値を返す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41312-102">How to: Return a Value from a Procedure (Visual Basic)</span></span>
<span data-ttu-id="41312-103">A`Function`プロシージャに値を返す呼び出し元のコードを実行するか、`Return`ステートメントまたはを戻したり、`Exit Function`または`End Function`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="41312-103">A `Function` procedure returns a value to the calling code either by executing a `Return` statement or by encountering an `Exit Function` or `End Function` statement.</span></span>  
  
### <a name="to-return-a-value-using-the-return-statement"></a><span data-ttu-id="41312-104">Return ステートメントを使用して値を返す</span><span class="sxs-lookup"><span data-stu-id="41312-104">To return a value using the Return statement</span></span>  
  
1.  <span data-ttu-id="41312-105">Put、`Return`プロシージャのタスクが完了した時点でのステートメント。</span><span class="sxs-lookup"><span data-stu-id="41312-105">Put a `Return` statement at the point where the procedure's task is completed.</span></span>  
  
2.  <span data-ttu-id="41312-106">以下の`Return`呼び出し元のコードを取得するキーワード、値を生成する式でします。</span><span class="sxs-lookup"><span data-stu-id="41312-106">Follow the `Return` keyword with an expression that yields the value you want to return to the calling code.</span></span>  
  
3.  <span data-ttu-id="41312-107">同じプロシージャ内に複数の `Return` ステートメントを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="41312-107">You can have more than one `Return` statement in the same procedure.</span></span>  
  
     <span data-ttu-id="41312-108">次`Function`プロシージャが長い側またはの三角形の斜辺を計算し、呼び出し元のコードを返します。</span><span class="sxs-lookup"><span data-stu-id="41312-108">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, and returns it to the calling code.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_1.vb)]  
  
     <span data-ttu-id="41312-109">次の例では、一般的な呼び出しを`hypotenuse`、返された値を格納します。</span><span class="sxs-lookup"><span data-stu-id="41312-109">The following example shows a typical call to `hypotenuse`, which stores the returned value.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_2.vb)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a><span data-ttu-id="41312-110">Exit 関数または終了関数を使用して値を返す</span><span class="sxs-lookup"><span data-stu-id="41312-110">To return a value using Exit Function or End Function</span></span>  
  
1.  <span data-ttu-id="41312-111">内の少なくとも 1 つの場所で、`Function`プロシージャ、値、プロシージャの名前を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="41312-111">In at least one place in the `Function` procedure, assign a value to the procedure's name.</span></span>  
  
2.  <span data-ttu-id="41312-112">実行すると、`Exit Function`または`End Function`ステートメントでは、Visual Basic は、プロシージャの名前を最も最近割り当てられた値を返します。</span><span class="sxs-lookup"><span data-stu-id="41312-112">When you execute an `Exit Function` or `End Function` statement, Visual Basic returns the value most recently assigned to the procedure's name.</span></span>  
  
3.  <span data-ttu-id="41312-113">同じプロシージャ内に複数の `Exit Function` ステートメントを含めることができ、さらに同じプロシージャ内に `Return` ステートメントと `Exit Function` ステートメントを混在させることができます。</span><span class="sxs-lookup"><span data-stu-id="41312-113">You can have more than one `Exit Function` statement in the same procedure, and you can mix `Return` and `Exit Function` statements in the same procedure.</span></span>  
  
4.  <span data-ttu-id="41312-114">1 つだけ持つことができます`End Function`内のステートメント、`Function`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="41312-114">You can have only one `End Function` statement in a `Function` procedure.</span></span>  
  
     <span data-ttu-id="41312-115">詳細と例を参照してください「戻り値」[関数ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="41312-115">For more information and an example, see "Return Value" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41312-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="41312-116">See Also</span></span>  
 [<span data-ttu-id="41312-117">手順</span><span class="sxs-lookup"><span data-stu-id="41312-117">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="41312-118">Sub プロシージャ</span><span class="sxs-lookup"><span data-stu-id="41312-118">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="41312-119">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="41312-119">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="41312-120">演算子プロシージャ</span><span class="sxs-lookup"><span data-stu-id="41312-120">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="41312-121">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="41312-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="41312-122">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="41312-122">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="41312-123">Return ステートメント</span><span class="sxs-lookup"><span data-stu-id="41312-123">Return Statement</span></span>](../../../../visual-basic/language-reference/statements/return-statement.md)  
 [<span data-ttu-id="41312-124">方法 : 値を返すプロシージャを作成する</span><span class="sxs-lookup"><span data-stu-id="41312-124">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)  
 [<span data-ttu-id="41312-125">方法: 値を返すプロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="41312-125">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
