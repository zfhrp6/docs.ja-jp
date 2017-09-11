---
title: "方法: プロシージャ (Visual Basic の場合) から値を返す |Microsoft ドキュメント"
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
- procedures, returning from
- procedures, returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
caps.latest.revision: 12
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
ms.openlocfilehash: 601cd3adca0105eb829bb6156f94289b5c9f5f72
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a><span data-ttu-id="89092-102">方法: プロシージャから値を返す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89092-102">How to: Return a Value from a Procedure (Visual Basic)</span></span>
<span data-ttu-id="89092-103">A`Function`プロシージャに値を返す、呼び出し元コードを実行していずれか、`Return`ステートメントまたはを戻したり、`Exit Function`または`End Function`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="89092-103">A `Function` procedure returns a value to the calling code either by executing a `Return` statement or by encountering an `Exit Function` or `End Function` statement.</span></span>  
  
### <a name="to-return-a-value-using-the-return-statement"></a><span data-ttu-id="89092-104">Return ステートメントを使用して値を返す</span><span class="sxs-lookup"><span data-stu-id="89092-104">To return a value using the Return statement</span></span>  
  
1.  <span data-ttu-id="89092-105">Put、`Return`ステートメント、プロシージャのタスクが完了した時点です。</span><span class="sxs-lookup"><span data-stu-id="89092-105">Put a `Return` statement at the point where the procedure's task is completed.</span></span>  
  
2.  <span data-ttu-id="89092-106">次の`Return`呼び出し元のコードに戻したいキーワードの値を生成する式を使用します。</span><span class="sxs-lookup"><span data-stu-id="89092-106">Follow the `Return` keyword with an expression that yields the value you want to return to the calling code.</span></span>  
  
3.  <span data-ttu-id="89092-107">1 つ以上が持てる`Return`同じプロシージャ内のステートメントです。</span><span class="sxs-lookup"><span data-stu-id="89092-107">You can have more than one `Return` statement in the same procedure.</span></span>  
  
     <span data-ttu-id="89092-108">次`Function`プロシージャと最も長い辺または直角三角形の斜辺を計算し、呼び出し元のコードを返します。</span><span class="sxs-lookup"><span data-stu-id="89092-108">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, and returns it to the calling code.</span></span>  
  
     <span data-ttu-id="89092-109">[!code-vb[VbVbcnProcedures&#1;](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="89092-109">[!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_1.vb)]</span></span>  
  
     <span data-ttu-id="89092-110">次の例では、一般的な呼び出しを`hypotenuse`、返される値を格納します。</span><span class="sxs-lookup"><span data-stu-id="89092-110">The following example shows a typical call to `hypotenuse`, which stores the returned value.</span></span>  
  
     <span data-ttu-id="89092-111">[!code-vb[VbVbcnProcedures&6;](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="89092-111">[!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_2.vb)]</span></span>  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a><span data-ttu-id="89092-112">Exit 関数または終了関数を使用して値を返す</span><span class="sxs-lookup"><span data-stu-id="89092-112">To return a value using Exit Function or End Function</span></span>  
  
1.  <span data-ttu-id="89092-113">内の少なくとも&1; つの場所で、`Function`プロシージャ、プロシージャの名前に値を代入します。</span><span class="sxs-lookup"><span data-stu-id="89092-113">In at least one place in the `Function` procedure, assign a value to the procedure's name.</span></span>  
  
2.  <span data-ttu-id="89092-114">実行すると、`Exit Function`または`End Function`ステートメント、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プロシージャの名前に最も最近割り当てられた値を返します。</span><span class="sxs-lookup"><span data-stu-id="89092-114">When you execute an `Exit Function` or `End Function` statement, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] returns the value most recently assigned to the procedure's name.</span></span>  
  
3.  <span data-ttu-id="89092-115">1 つ以上を持つことができます`Exit Function`して、同じプロシージャ内のステートメントを混在させること`Return`と`Exit Function`同じプロシージャ内のステートメントです。</span><span class="sxs-lookup"><span data-stu-id="89092-115">You can have more than one `Exit Function` statement in the same procedure, and you can mix `Return` and `Exit Function` statements in the same procedure.</span></span>  
  
4.  <span data-ttu-id="89092-116">1 つだけ持つことができます`End Function`内のステートメントで、`Function`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="89092-116">You can have only one `End Function` statement in a `Function` procedure.</span></span>  
  
     <span data-ttu-id="89092-117">詳細と例を参照してください「戻り値」 [Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="89092-117">For more information and an example, see "Return Value" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89092-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="89092-118">See Also</span></span>  
 <span data-ttu-id="89092-119">[手順](./index.md) </span><span class="sxs-lookup"><span data-stu-id="89092-119">[Procedures](./index.md) </span></span>  
<span data-ttu-id="89092-120"> [Sub プロシージャ](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="89092-120"> [Sub Procedures](./sub-procedures.md) </span></span>  
<span data-ttu-id="89092-121"> [プロパティ プロシージャ](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="89092-121"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="89092-122"> [演算子プロシージャ](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="89092-122"> [Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="89092-123"> [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="89092-123"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="89092-124"> [Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="89092-124"> [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="89092-125"> [Return ステートメント](../../../../visual-basic/language-reference/statements/return-statement.md) </span><span class="sxs-lookup"><span data-stu-id="89092-125"> [Return Statement](../../../../visual-basic/language-reference/statements/return-statement.md) </span></span>  
<span data-ttu-id="89092-126"> [方法: 値を返すプロシージャを作成します。](./how-to-create-a-procedure-that-returns-a-value.md) </span><span class="sxs-lookup"><span data-stu-id="89092-126"> [How to: Create a Procedure that Returns a Value](./how-to-create-a-procedure-that-returns-a-value.md) </span></span>  
<span data-ttu-id="89092-127"> [方法: 値を返すプロシージャを呼び出す](./how-to-call-a-procedure-that-returns-a-value.md)</span><span class="sxs-lookup"><span data-stu-id="89092-127"> [How to: Call a Procedure That Returns a Value](./how-to-call-a-procedure-that-returns-a-value.md)</span></span>
